# Credit Card Transaction Fraud Anomaly Detection

## Overview
This project focuses on detecting potentially fraudulent credit card transactions using an **unsupervised anomaly detection approach**. Due to the highly imbalanced nature of fraud data, traditional supervised classification methods are often ineffective without extensive labeled data. To address this challenge, an **Isolation Forest** model is used to identify anomalous transaction patterns that may indicate fraud.

The project demonstrates a realistic, industry-relevant fraud detection pipeline suitable for early-stage screening systems.

---

## Problem Statement
Credit card fraud is a critical problem in financial systems, characterized by:
- Extremely **imbalanced datasets**
- Limited availability of labeled fraud samples
- High cost associated with false negatives and false positives

The objective of this project is to:
- Detect anomalous transactions without relying on labeled training data
- Identify potentially fraudulent transactions
- Evaluate model performance using an appropriate metric for fraud detection

---

## Dataset
- **Source:** Publicly available anonymized credit card transaction dataset  
- **Features:**  
  - Time  
  - Amount  
  - PCA-transformed numerical features (V1–V28)  
- **Target variable:**  
  - `Class` (0 = Normal, 1 = Fraud)

To enable faster experimentation and reproducibility, a **subset of 7,973 transactions** was used while preserving the original data distribution.

---

## Approach

### 1. Data Preprocessing
- Loaded the transaction dataset from CSV format
- Performed data validation and structure checks
- Handled missing values in the target column
- Standardized numerical features using `StandardScaler` to ensure consistent scaling

### 2. Anomaly Detection Model
An **Isolation Forest** model was selected due to its suitability for:
- Unsupervised learning
- High-dimensional data
- Rare anomaly detection

**Key model parameters:**
- `n_estimators = 100`
- `contamination = 0.01` (assumes approximately 1% anomalies)
- `random_state = 42` for reproducibility

Transactions identified as anomalies by the model were flagged as potential fraud cases.

---

## Evaluation Metric
The model was evaluated using **Precision**, defined as:

> Precision = (True Positives) / (Predicted Positives)

Precision was chosen because:
- Fraud detection systems must minimize false positives
- Flagged transactions often require manual review or additional checks

---

## Results
- **Total transactions analyzed:** 7,973  
- **Transactions flagged as anomalous:** 80  
- **Precision score:** 0.2857  

This indicates that approximately **28% of the transactions flagged as fraud were actual fraudulent cases**. Given the unsupervised nature of the approach and extreme class imbalance, this result is considered realistic and acceptable for early-stage fraud screening.

---

## Output
The project generates a CSV file containing detected fraud cases with the following columns:
- `Time`
- `Amount`
- `Class`
- `predicted_fraud`

This output can be used for further investigation, auditing, or downstream processing.

---

## Files in This Repository
- `Credit_Card_Transaction_Fraud_Anomaly_Detection.ipynb`  
  → Complete file containing data processing, modeling, evaluation, and results  
- `detected_fraud_cases.csv`  
  → List of transactions flagged as potential fraud  

---

## Conclusion
This project demonstrates the practical application of unsupervised anomaly detection for fraud identification in highly imbalanced datasets. While false positives are present, such behavior is expected and acceptable in anomaly detection systems designed for early-stage screening. The approach can be extended by integrating supervised models or rule-based systems for multi-layer fraud detection pipelines.

---

## Future Improvements
- Apply the pipeline to the full dataset or streaming data
- Tune contamination thresholds based on business requirements
- Combine with supervised classifiers for second-stage validation
- Incorporate cost-sensitive evaluation metrics

---

## Technologies Used
- Python
- Pandas
- NumPy
- Scikit-learn

---

## Author
Ashith Shetty
