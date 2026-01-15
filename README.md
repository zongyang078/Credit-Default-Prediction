# Credit-Default-Prediction

## Overview
This project develops and compares credit default prediction models to support credit card approval decisions for a hypothetical regional bank in the Bay Area.

Using historical credit card account data, I build an interpretable baseline model (Logistic Regression) and a nonlinear machine learning model (Random Forest) to estimate default risk. The models are evaluated on an imbalanced dataset using appropriate risk-focused metrics, and the final model is translated into actionable credit approval rules.

This project was completed as part of **DS 5110: Data Science Foundations**.


## Business Problem
Financial institutions rely on risk models to decide which credit applications to approve while minimizing default losses.

Key challenges include:
- Strong class imbalance between default and non-default customers
- Trade-offs between model interpretability and predictive performance
- The high cost of failing to identify high-risk applicants

The goal of this project is to:
- Predict the probability of default for credit card applicants
- Compare classical statistical models with machine learning approaches
- Select a model suitable for real-world credit approval decisions


## Dataset
- **Source**: Simulated credit card account data for a hypothetical bank (XYZ)
- **Training set**: 20,000 accounts  
- **Validation set**: 3,000 accounts  
- **Hidden test set**: 5,000 accounts  
- **Features**: 20 predictors covering:
  - Credit utilization
  - Delinquency history
  - Credit age and account tenure
  - Income and account indicators
- **Target variable**: Binary default indicator

Data preprocessing includes handling class imbalance and preparing features for both linear and tree-based models.


## Methodology

### Logistic Regression (Baseline Model)
- Applied logistic regression with class balancing
- Provides interpretable coefficients for understanding key risk drivers
- Used as a transparent benchmark for credit risk modeling

Key insights:
- Higher default risk is associated with high credit utilization, recent delinquencies, and frequent credit inquiries
- Longer credit history, higher income, and existing customer status are associated with lower default risk

### Random Forest (Machine Learning Model)
- Selected due to its ability to capture nonlinear relationships and feature interactions
- Trained with class weighting to address imbalance
- Performed lightweight hyperparameter tuning over:
  - Number of trees
  - Maximum tree depth
  - Minimum samples per leaf

The tuned Random Forest achieved stronger discrimination between default and non-default customers and improved recall for high-risk cases.


## Model Evaluation
Given the imbalanced nature of the dataset, model performance was evaluated using:
- **ROC-AUC** (primary metric) — measures ranking and discrimination ability
- **Recall (default class)** — critical for identifying high-risk applicants
- **Accuracy** — reported but not emphasized due to imbalance

### Validation Performance (Summary)
- Logistic Regression: AUC ≈ 0.82  
- Random Forest (tuned): AUC ≈ 0.86  

The Random Forest model consistently outperformed Logistic Regression in identifying defaulting customers.


## Model Selection & Decision Strategy
Although Logistic Regression offers interpretability, the tuned Random Forest was selected for credit approval due to:
- Higher AUC
- Better recall for default cases
- Improved modeling of nonlinear credit risk patterns

### Credit Decision Framework
The selected model outputs a predicted probability of default, which can be used to define decision thresholds:
- **Low risk** (e.g., < 0.10): Automatic approval
- **Medium risk** (e.g., 0.10–0.25): Manual review
- **High risk** (e.g., > 0.25): Decline

These thresholds can be adjusted based on the institution’s risk tolerance and loss objectives.


## Fairness & Existing Customer Analysis
Analysis shows that applicants who already hold accounts with the bank tend to have lower predicted default risk.  
Both Logistic Regression coefficients and Random Forest feature importance indicate that existing customers receive slightly more favorable treatment, reflecting historically lower default rates rather than explicit preferential bias.


## Project Structure
├── data/        # Training and validation datasets
├── notebooks/   # Data preprocessing, modeling, and evaluation
├── report/      # Final project report (PDF)
├── figures/     # Key evaluation plots
└── README.md


## Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib / Seaborn
- Jupyter Notebook


## Key Takeaways
- Logistic Regression provides transparency and insight into credit risk drivers
- Random Forest delivers superior predictive performance for default detection
- Proper metric selection is critical for imbalanced credit-risk problems
- Probability-based decision rules bridge modeling results with real-world credit approval


## License
This project is for academic and demonstration purposes.
