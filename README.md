# 🩺 Breast Cancer Classification with XGBoost, SHAP & LLM-based Analysis

## 📌 Project Overview
This project focuses on **breast cancer classification** using the **XGBoost (XGBClassifier)** model. It integrates:
- **Data preprocessing** with `StandardScaler` and `train_test_split`.
- **Modeling** with **XGBoost**.
- **Interpretability** using **SHAP**.
- **Post-hoc evaluation & clinical reasoning** using an **LLM (Large Language Model)** to analyze results such as confusion matrices, ROC-AUC, PR curves, and risk stratification.

The ultimate goal is not just to achieve strong predictive performance, but also to provide **clinically meaningful insights**.

---

## ⚙️ Workflow
1. **Data Preprocessing**
   - Standardized features using `StandardScaler`.
   - Splitting dataset into training and testing sets (`train_test_split`).

2. **Model Training**
   - Trained **XGBClassifier** for classification.
   - Trained both **baseline** and **imbalance-handled** models.

3. **Model Evaluation**
   - Confusion Matrices
   - ROC-AUC curves
   - Precision-Recall curves
   - Risk stratification (Low, Medium, High)

4. **Interpretability**
   - SHAP analysis for feature importance.
   - Identification of top biological markers.

5. **LLM-Based Results Interpretation**
   - Used an LLM to explain results in **clinical and analytical terms**.

---

## 📊 Results & Insights

### 🔹 Confusion Matrices
- **Baseline Model**: `[[122, 0], [15, 4]]`
  - Specificity = **1.0**
  - Sensitivity = **0.21**
- **Imbalance-Handled Model**: `[[121, 1], [13, 6]]`
  - Specificity = **0.992**
  - Sensitivity = **0.32**

🔑 **Insight**: The imbalance-handled model improves sensitivity (more true positives detected), making it more clinically useful.

---

### 🔹 ROC-AUC Comparison
- Baseline = **0.609**
- Imbalance-Handled = **0.599**

🔑 **Insight**: Baseline has slightly higher ROC-AUC, but difference is marginal.

---

### 🔹 Precision-Recall (PR) Curves
- Baseline PR-AUC = **0.441**
- Imbalance-Handled PR-AUC = **0.432**

At threshold 0.5:
- **Baseline**: Precision = 1.00, Recall = 0.21
- **Imbalance-handled**: Recall = 0.32

🔑 **Insight**: The imbalance-handled model sacrifices a bit of precision for better recall, which is critical in **detecting more high-risk patients**.

---

### 🔹 SHAP Feature Importance
- **Baseline Model**: CALML5, CYP4F22, MMP12, LGALS12
- **Imbalance-Handled Model**: MUC15, LGALS12, MMP12, CYP4F8

🔑 **Insight**: Both models highlight **MMP12** and **LGALS12** as important, suggesting consistent biological relevance.

---

## 🧠 LLM-Based Risk Stratification Analysis

### 1. **Risk Score Distributions**
- Baseline has more patients in **High risk** group.
- Imbalance-handled model distributes patients more evenly across risk groups.

### 2. **Risk Group Performance**
- Baseline tends to **overestimate risk**, placing more positives in High group.
- Imbalance-handled model achieves **better balance** across Low, Medium, High risk groups.

### 3. **Clinical Usefulness**
- **Imbalance-handled model** is more clinically useful because:
  - Handles class imbalance better.
  - Provides more accurate **risk group assignments**.
  - Reduces unnecessary high-risk classifications.

---

✅ **Final Verdict**:  
For purely statistical performance, the baseline model has a marginal edge in ROC-AUC and precision.  
But for **clinical applications** where recall (catching more true positives) is critical, the **imbalance-handled model is the better choice**.

