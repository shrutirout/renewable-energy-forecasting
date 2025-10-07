# 🌍 Renewable Energy Forecasting using Machine Learning (Gujarat, India)

## 📖 Overview

This project focuses on forecasting **renewable energy generation** — specifically **wind** and **solar power** — for the state of **Gujarat, India**, using advanced machine learning techniques.
The goal is to analyze how seasonal variations and **government policy interventions** influence renewable energy output and to predict future trends that can aid in energy planning and sustainability strategies.

The project leverages **ensemble regression modeling** to combine the strengths of multiple algorithms and improve prediction accuracy. It’s designed to serve as a practical analytical tool for **policy evaluation, capacity planning, and forecasting future renewable generation**.

---

## 🧩 Dataset Description

* **Source:** Monthly renewable energy generation data from Gujarat, India.
* **Time Period:** 2015 – 2024
* **Structure:** 139 rows × 9 columns (monthly time series)
* **Energy Types:** Wind, Solar, Biomass, Bagasse, Small Hydro, Large Hydro, Waste-to-Energy, and Total Generation.
* **Focus:** Separate datasets were created for **Wind Power** and **Solar Power** forecasting.

---

## ⚙️ Data Preprocessing & Feature Engineering

To make the data suitable for time-series forecasting using machine learning, several transformation steps were applied:

1. **Cleaning & Filtering:**

   * Removed rows with zero or missing values in energy columns.
   * Split combined “Month, Year” column into two numeric columns for better temporal control.

2. **Cyclical Encoding for Month:**

   * To capture seasonal trends, months were encoded as:

     * `month_sin = sin(2π × Month / 12)`
     * `month_cos = cos(2π × Month / 12)`
   * This preserves the cyclical nature of months (e.g., December and January being close in pattern).

3. **Year Scaling:**

   * Normalized using:
     `Year_scaled = Year - min(Year)`
   * This allows the model to learn long-term yearly trends without large numeric bias.

4. **Policy Feature Integration:**

   * Binary indicators were created for years where **renewable energy policies** were introduced or revised (e.g., Solar Policy 2015, Wind Policy 2016).
   * This helps the model account for sudden policy-driven changes in generation output.

---

## 💨 Wind Energy Forecasting

### Objective

Predict monthly **wind energy generation** for Gujarat, factoring in both temporal and policy influences.

### Features Used

* `Year_scaled`, `month_sin`, `month_cos`
* Policy indicators:

  * Wind Power Policy (2002, 2007, 2009, 2013, 2016)
  * GERC Regulations (2006, 2020)

### Modeling Approach

* Models used:

  * **Random Forest Regressor**
  * **Gradient Boosting Regressor**
  * **XGBoost Regressor**
* Combined using a **Voting Regressor** (ensemble averaging) to reduce variance and improve generalization.

### Evaluation Metrics

* **Training Set:**

  * R² Score: **0.94**
  * Mean Squared Error (MSE): **33,582.15**
* **Testing Set:**

  * R² Score: **0.79**
  * Mean Squared Error (MSE): **97,402.89**

### Key Insights

* Seasonal peaks align with the **monsoon months**, when wind intensity is highest.
* The ensemble model effectively captures both **cyclical seasonality** and **yearly growth trends**.
* Predictions from 2025–2030 show a gradual increase in wind generation, consistent with infrastructure expansion and favorable policy support.

---

## ☀️ Solar Energy Forecasting

### Objective

Forecast monthly **solar energy generation** using a similar ensemble approach while accounting for Gujarat’s solar policies.

### Features Used

* `Year_scaled`, `month_sin`, `month_cos`
* Policy indicators:

  * Solar Power Policy (2015, 2021)
  * Wind-Solar Hybrid Policy (2018)
  * Rooftop Solar Scheme (2019)

### Modeling Approach

* Same ensemble strategy as wind forecasting:

  * **Random Forest**, **Gradient Boosting**, and **XGBoost** combined through **Voting Regressor**.
* Trained on 80% of data; tested on 20% to ensure model generalization.

### Evaluation Metrics

* **Training Set:**

  * R² Score: **0.99**
  * Mean Squared Error (MSE): **2,179.23**
* **Testing Set:**

  * R² Score: **0.96**
  * Mean Squared Error (MSE): **8,298.85**

### Key Insights

* Model captures strong **seasonal variation** — higher outputs in summer months and lower during monsoon periods.
* The inclusion of **policy-based features** improved predictive stability around years with new incentives.
* Solar generation forecast till 2030 shows a consistent upward trajectory due to policy-driven adoption and declining installation costs.

---

## 📊 Model Evaluation & Results

| Source | Model Type        | Train R² | Test R² | Train MSE | Test MSE  |
| ------ | ----------------- | -------- | ------- | --------- | --------- |
| Wind   | Ensemble (Voting) | 0.94     | 0.79    | 33,582.15 | 97,402.89 |
| Solar  | Ensemble (Voting) | 0.99     | 0.96    | 2,179.23  | 8,298.85  |

The **ensemble model** provided the best balance between accuracy and generalization, outperforming individual regressors.
Both models successfully captured **temporal cycles, policy effects, and long-term growth trends**.

---

## 🧠 Insights & Discussion

* Ensemble learning proved more robust than any single model (Random Forest, Gradient Boosting, or XGBoost alone).
* Policy indicators significantly improved model interpretability, showing clear jumps in output following major renewable initiatives.
* Wind predictions are more variable due to natural fluctuations, while solar generation exhibits steadier growth.
* Such models can aid **policy planning**, **capacity forecasting**, and **renewable integration** into Gujarat’s energy grid.

---

## 🛠️ Tools & Libraries Used

* **Languages:** Python
* **Libraries:**

  * `pandas`, `numpy`, `matplotlib`
  * `scikit-learn` (RandomForest, GradientBoost, Voting Regressor)
  * `xgboost`
* **Platform:** Google Colab

---

## 🚀 How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/renewable-energy-forecasting.git
   cd renewable-energy-forecasting
   ```
2. Open the notebooks in **Google Colab**:

   * `Wind_energy_prediction.ipynb`
   * `Solar_energy_prediction.ipynb`
3. Run all cells sequentially to reproduce data preprocessing, training, and forecasting steps.

---

## 👥 Contributors

* **Shruti Soumya Rout** – 2022AAPS1144G
* **Shreyas Ashok Meher** – 2023AAPS0646G
* **Harsh Kumar Dixit** – 2021AAPS2935G
* **Institution:** BITS Pilani, K. K. Birla Goa Campus
* **Prepared Under:** Prof Mukund Keshavrao Deshmukh

---

