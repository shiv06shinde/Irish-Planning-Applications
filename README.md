# What Gets Built, What Gets Refused, and Why?
Data Mining & Machine Learning study of Irish planning applications
NCI · H9DMML · Prathmesh Arya, Sahil Manjrekar, Shivam Shinde

## Data source
National Planning Applications, Department of Housing, Local Government and Heritage
https://data.gov.ie/dataset/national-planning-applications (CC BY 4.0)
Scope: applications received from 1 July 2021 onwards.

## Folder structure
```
data/
  raw/          Downloaded CSV goes here. NOT in Git (too large, may contain personal data)
  processed/    Output of notebook 01. Everyone loads planning_clean.csv.gz from here
notebooks/
  data_preparation.ipynb   Shared cleaning (Shivam)
  eda.ipynb                Shared exploratory analysis (group)
  x25248677.ipynb          Topic modelling, association rules, Lasso, Logistic Regression
  x26125935.ipynb              Anomaly detection, temporal analysis, XGBoost, Random Forest
  x25223151.ipynb             PCA, clustering, Polynomial Regression, SVM
src/            Shared Python code (e.g. evaluation.py with baselines and metrics)
figures/        Saved plots for the report (name them e.g. shivam_pca_scree.png)
models/         Saved trained models (.joblib)
outputs/        Metric tables as CSV, for the final comparison
report/         IEEE report files
```

## How to reproduce
1. Download the CSV from the link above into `data/raw/`
2. Create the environment: `python -m venv .venv`, activate it, then `pip install -r requirements.txt`
3. Run `notebooks/01_data_preparation.ipynb` top to bottom. It creates `data/processed/planning_clean.csv.gz`
4. Run notebooks in order of folder structure in readme

## Rules for the team
- Never edit files in `data/raw/`
- Always load data from `data/processed/planning_clean.csv.gz` and use the `split` column for train/test
- Check `data/processed/data_dictionary.csv` before choosing features. Columns marked
  "AFTER application" must never be used as features (leakage)
- Use `random_state=23` everywhere
- Save figures to `figures/` and metric tables to `outputs/` with your name in the file name
