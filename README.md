# Football Match Prediction

**Course:** Data Mining

## Team Members

* **Mobina Khaksar** - 40117713
* **Sara Ghafoury** - 40121233

---

## Project Overview

This project focuses on predicting the outcome of football matches using data mining and machine learning techniques. The objective is to analyze historical football match data, perform data preprocessing and feature engineering, and build classification models capable of predicting the final match result.

The target variable is **`match_result`**, which represents the outcome of a match (Home Win, Draw, or Away Win).

---

## Dataset

The dataset contains historical football match records with current match information and the previous ten matches of both participating clubs.

| Feature              | Description                                         |
| -------------------- | --------------------------------------------------- |
| `match_id`           | Unique match identifier                             |
| `match_result`       | **Target variable**                                 |
| `home_club`          | Home team                                           |
| `away_club`          | Away team                                           |
| `fixture_date`       | Match date                                          |
| `competition`        | Competition name                                    |
| `competition_code`   | Competition identifier                              |
| `cup_game`           | Indicates whether the match is a cup competition    |
| `home_manager_id`    | Home team manager ID                                |
| `away_manager_id`    | Away team manager ID                                |
| `home_club_recent_*` | Statistics from the home club's previous 10 matches |
| `away_club_recent_*` | Statistics from the away club's previous 10 matches |

The historical features include:

* Fixture dates
* Goals scored
* Goals conceded
* Team ratings
* Opponent ratings
* Competition codes
* Manager IDs
* Home/Away indicators
* Cup game indicators

> **Note:** The original dataset is not included in this repository because of its size.

---

## Project Workflow

* Exploratory Data Analysis (EDA)
* Data Cleaning
* Feature Engineering
* Feature Selection
* Model Training
* Model Evaluation
* Hyperparameter Tuning

---

## Data Cleaning

The following preprocessing steps were performed:

* Removing unnecessary columns
* Standardizing categorical values
* Removing duplicate records
* Handling missing values

---

## Feature Engineering

Several new features were created from the previous ten matches of each club, including:

## Feature Engineering Steps

* Converting date columns to datetime format
* Sorting data chronologically to strictly prevent data leakage
* Extracting year, month, day of week, and summer break indicator
* Calculating rest days from previous matches
* Dropping high-cardinality and noisy features (e.g., manager IDs)
* Encoding target variable (home/away/draw) using Label Encoding
* Average goals scored & conceded
* Goal difference (home and away)
* Average team rating & Average opponent rating
* **True Strength Metric** (Team rating / Opponent rating)
* Rating difference & True Strength difference between teams
* Average rest days & rest days difference
* Recent home match ratio & Recent cup match ratio

---

## Data Leakage Prevention Strategy

To ensure the model evaluation is scientifically valid and reflects real-world predictive capabilities, strict data leakage prevention measures were implemented:
* **Chronological Split:** The dataset was split into training (80%) and testing (20%) sets chronologically (`shuffle=False`), preventing the model from learning from future matches.
* **Safe Target Encoding:** Club and competition names were transformed using Target Encoding. The encoder was fitted **only** on the training set.
* **Safe Imputation:** Missing values (NaNs) were imputed using the median, calculated **strictly** from the training set and then applied to the test set.

---

## Machine Learning Models

Several classification algorithms were trained and compared to find the most robust predictive model:

* Logistic Regression
* Decision Tree
* Random Forest
* K-Nearest Neighbors (KNN)
* XGBoost Classifier (Best Performing Model)

All models were trained on the safely preprocessed data to ensure fair comparison and accurate metrics.

---

## Evaluation Metrics

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## Repository Structure

```text
Football-Match-Prediction/
│
├── data/
│   ├── student_version.csv
│   └── ...
│
├── notebooks/
│   ├── Data_Cleaning.ipynb
│   ├── Feature_Engineering.ipynb
│   └── Model_Training_and_Evaluation.ipynb
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/saraghafoury/Football-Match-Prediction.git
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook
