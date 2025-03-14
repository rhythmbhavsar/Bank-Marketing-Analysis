# Bank Marketing Analysis

This repository contains a comprehensive analysis and modeling of a bank marketing dataset aimed at predicting client subscription to term deposits. The project includes data preprocessing, exploratory data analysis (EDA), feature engineering, and predictive modeling using machine learning techniques.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset Information](#dataset-information)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Feature Engineering](#feature-engineering)
- [Modeling and Evaluation](#predictive-modeling)
- [Results and Insights](#key-insights)
- [Usage Instructions](#usage-instructions)

## Project Overview
The goal of this project is to analyze bank marketing data to predict whether a client will subscribe to a term deposit. The analysis provides insights into customer behaviors and identifies key factors that influence subscription decisions.

## Dataset Information
The dataset contains 45,211 records with 17 features, including demographic information, financial status, campaign details, and the target variable indicating subscription status (`y`):

| Column Name | Description |
|-------------|-------------|
| age | Age of the client (numeric) |
| job | Job type |
| marital | Marital status |
| education | Education level |
| default | Credit default status |
| balance | Bank balance (euros) |
| housing | Housing loan (yes/no) |
| loan | Personal loan (yes/no) |
| contact | Contact method (cellular/telephone/unknown) |
| day | Day of contact (month) |
| month | Month of contact |
| duration | Call duration (seconds) |
| campaign | Number of contacts during this campaign |
| pdays | Days since last contact (-1 if not previously contacted) |
| previous | Number of previous contacts before this campaign |
| poutcome | Outcome of previous campaign (success/failure/other/unknown) |
| y | Subscription outcome (yes/no) |

The dataset is complete with no missing or duplicate values.

## Data Preprocessing
Key preprocessing steps applied:

- **Outlier Handling**:
  - *Age*: Outliers capped at 70 years.
  - *Balance*: Outliers capped using the IQR method.
  - *Duration*: Outliers capped at upper bound determined by IQR.
  - *Campaign*: Outliers capped at 6 contacts.
  - *Previous Contacts*: Capped at the 99th percentile.

- **Feature Encoding**:
  - Categorical features encoded using label encoding for modeling purposes.

## Exploratory Data Analysis
Key insights from EDA:

- **Job Type**: Students and retired individuals have the highest subscription rates; blue-collar workers have the lowest.
- **Education**: Higher education correlates with higher subscription rates.
- **Marital Status**: Single individuals subscribe more frequently than married or divorced individuals.
- **Loans and Defaults**: Clients without personal or housing loans and without credit defaults are more likely to subscribe.
- **Contact Method**: Cellular contacts yield higher success rates than telephone or unknown methods.
- **Campaign Timing**: March and December campaigns have the highest success rates; May has the lowest.
- **Previous Campaign Outcome**: Previous successful outcomes strongly predict future subscriptions.

## Feature Engineering
New features created include:
- `contact_frequency`: Combines current and previous campaign contacts.
- `contact_density`: Captures relationship between contact frequency and duration.
- `previous_outcome_impact`: Encodes previous campaign outcomes numerically.

## Predictive Modeling
Models evaluated include Random Forest, XGBoost, LightGBM, and SGDClassifier. Hyperparameter tuning was performed to optimize model performance. Evaluation metrics include accuracy, precision, recall, F1-score, ROC-AUC, and confusion matrices.

Best-performing model results:
| Model         | Accuracy | Precision (Class 1) | Recall (Class 1) | F1 Score (Class 1) |
|---------------|----------|--------------------|------------------|---------------------|
| Random Forest | 0.88     | 0.51               | 0.70             | 0.59                |

## Visualizations
Visualizations included:
- Boxplots for outlier detection
- Histograms for feature distributions
- Bar charts for categorical feature analysis
- ROC curves for model evaluation

## How to Use This Repository

### Installation
Clone the repository and install dependencies:
```bash
git clone 
cd Bank-Marketing-Analysis
pip install -r requirements.txt
```

## Usage
Run the provided Jupyter notebooks sequentially to replicate the analysis:

1. `01_data_preprocessing.ipynb` – Data cleaning and preprocessing steps.
2. `02_exploratory_data_analysis.ipynb` – Exploratory data analysis visualizations.
3. `03_feature_engineering.ipynb` – Feature creation and selection strategies.
4. `03_model_training_and_evaluation.ipynb` – Machine learning model training, evaluation, and tuning.

## Contributions
Contributions are welcome! Please open an issue or submit a pull request if you wish to contribute improvements or new analyses.

## License
This project is licensed under the MIT License—see the LICENSE file for details.
