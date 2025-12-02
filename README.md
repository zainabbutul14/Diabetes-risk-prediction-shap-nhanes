# 🌟 Precision Risk Modeling for Type 2 Diabetes (NHANES Clinical Biomarkers)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![Final ROC-AUC](https://img.shields.io/badge/ROC--AUC-0.9431-brightgreen.svg)]()

This project demonstrates the full Machine Learning lifecycle, from clinical feature engineering and model comparison to advanced interpretability (SHAP), to predict the risk of Type 2 Diabetes using real-world public health data (NHANES 2017-2020).

| Metric | Score | Status |
| :--- | :--- | :--- |
| **Final ROC-AUC** | **0.9431** | **Winner** |
| Baseline (LR) AUC | 0.9285 | Strong Baseline |
| Top Feature | Age | SHAP Confirmed |

---
##  1. The Challenge and Data

**Goal:** Build, compare, and optimize models for diabetes risk prediction, focusing on **explainability** (trust) to derive actionable clinical insights from complex biomarkers.

**Data Source:** The National Health and Nutrition Examination Survey (**NHANES**) 2017-2020. This is a crucial, high-quality, real-world public health dataset provided by the U.S. Centers for Disease Control and Prevention (CDC).

* **URL:** **[NHANES Data Link (CDC)](https://wwwn.cdc.gov/nchs/nhanes/Default.aspx)**

The final dataset contained **14,690** samples, with a class imbalance of **9.86%** diabetic cases.

**Key Features Used:**
* **Age**, **BMI**
* **Glucose**, **Insulin**, **HbA1c** (Long-term blood sugar control).
* **Engineered Feature:** **HOMA-IR** (Insulin Resistance Index) $\approx \frac{\text{Insulin} \times \text{Glucose}}{405}$. This feature translates a core biological concept (insulin resistance) directly into a predictive input.

---

##  2. Exploratory Data Analysis (EDA)

The initial analysis confirmed a strong predictive signal, as the distributions for key chronic markers show a clear separation between healthy and diabetic cohorts.

* **Observation:** The distribution for **HbA1c** was visually the most distinct, hinting at its high predictive power.

<img width="1490" height="390" alt="1" src="https://github.com/user-attachments/assets/feebec1a-f315-4239-98ea-51422663c589" />

---

##  3. Model Training & Optimization

We benchmarked three models (Logistic Regression, Random Forest, XGBoost) using **Stratified K-Fold** cross-validation, prioritizing the **ROC-AUC** score due to the data imbalance.

### Model Comparison Table

| Model | Final ROC-AUC | Sensitivity (Recall) | Specificity | Key Insight |
| :--- | :--- | :--- | :--- | :--- |
| **Logistic Regression (Baseline)** | 0.9285 | **0.8304** | 0.8584 | Strong recall, but overall lower discrimination. |
| **XGBoost (Tuned Winner)** | **0.9431** | 0.5986 | **0.9819** | Highest discrimination (AUC) and lowest false positive rate. |

### Visual Results: ROC Curves

The tuning of the **XGBoost** model yielded the highest overall discriminative performance.

| Logistic Regression (AUC: 0.929) | XGBoost Final (AUC: 0.943) |
| :---: | :---: |
 
<img width="536" height="470" alt="2" src="https://github.com/user-attachments/assets/21281bf0-fee3-474b-96fb-4eaefefdc53c" />

<img width="536" height="470" alt="5" src="https://github.com/user-attachments/assets/e9c3653d-5662-40f2-9d14-76924ae7eb16" />

---

##  4. Model Interpretability (SHAP Analysis)

We utilized **SHAP (SHapley Additive exPlanations)** on the final optimized XGBoost model to move beyond raw accuracy and understand the *why* behind its decisions.

### A. SHAP Summary: Overall Feature Impact

The SHAP summary plot ranks features by overall impact. **High Age** and **High HbA1c** are clearly shown to push the prediction toward diabetes (moving dots to the right).

<img width="759" height="420" alt="6" src="https://github.com/user-attachments/assets/ac2aaf8c-f748-4513-b6a0-43a1883e5450" />

**Top 3 Predictors:** The model confirms that **Age**, **HbA1c**, and **BMI** are the most powerful factors.

### B. Feature Importance Bar Chart

The absolute mean SHAP values quantify the average magnitude of impact for each feature, confirming **Age** and **HbA1c** dominance.

<img width="762" height="547" alt="8" src="https://github.com/user-attachments/assets/d9990e88-585d-4231-ab2d-0c87fd74ee0f" />

### C. Detailed Look at Age

The dependence plot for the top feature, **Age**, confirms a clear monotonic relationship: risk increases consistently with age, which is the model's strongest determinant.

<img width="561" height="453" alt="7" src="https://github.com/user-attachments/assets/38b93c17-82cc-4a04-ae49-50badac9f1b2" />

---

##  5. Key Achievements & Clinical Impact

> **Real-World Impact:** This explainable model serves as an advanced screening tool, prioritizing high-risk patients to optimize resource allocation and enable early intervention in chronic disease management.

* **High-Performance Prediction:** Developed an optimized **XGBoost** model achieving a final ROC-AUC of **0.9431**, a robust score for initial risk screening.
* **Advanced ML Methodology:** Demonstrated proficiency in advanced techniques like **Grid Search** optimization with **Stratified K-Fold** cross-validation.
* **Clinical Validation via SHAP:** The SHAP analysis definitively identified **Age** and **HbA1c** as the dominant risk factors, providing evidence-based guidance for screening and policy that aligns with chronic disease pathology.
* **Deployment Ready:** Saved the final trained model (`.pkl`) and necessary preprocessor (`.pkl`), creating artifacts ready for immediate integration into a production environment.

---

##  6. Repository Structure & Reproduction

### Repository Structure

---

### How to Reproduce



### Licensing

This project is licensed under the **MIT License**.
