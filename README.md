
# Stress Prediction & Period Stress Model

This repository contains two machine learning models used in a **student mental health monitoring system**:

1. **General Stress Predictor**
2. **Menstrual Cycle Stress Predictor (for females)**

Both models are trained using **Random Forest algorithms** and exported using `joblib`.

---

# 📂 Project Structure

```

.
├── period_model.ipynb
├── stress_model.ipynb
├── classifier.joblib
├── periods.xlsx
├── StressLevelDataset.csv
└── README.md

```

---

# 1️⃣ Menstrual Cycle Stress Predictor

## Dataset

File: `periods.xlsx`

- **897 samples**
- **3 columns**

| Feature | Description |
|------|------|
| period_flow | Encoded menstrual flow intensity |
| expected_vs_actual_date_difference | Difference between predicted and actual cycle date |
| period_stress | Continuous stress score |

---

## Model

Random Forest Regressor

```

RandomForestRegressor(
n_estimators = 100,
random_state = 42
)

```

---

## Model Performance

| Metric | Value |
|------|------|
| Mean Squared Error | 0.274 |
| R² Score | 0.832 |
| Accuracy (±0.5 tolerance) | 65.56% |

---

## Example Prediction

Input

```

period_flow = 1
expected_vs_actual_date_difference = 2

```

Output

```

Predicted Period Stress: 1.18

```

---

# 2️⃣ Stress Level Predictor

## Dataset

File: `StressLevelDataset.csv`

- **1100 samples**
- **15 features**

Target variable:

```

stress_level

```

Stress levels:

| Value | Meaning |
|------|------|
| 0 | No Stress |
| 1 | Mild Stress |
| 2 | Moderate Stress |
| 3 | High Stress |

---

## Model

Random Forest Classifier

Best parameters (GridSearchCV):

```

{
'max_depth': None,
'min_samples_leaf': 2,
'min_samples_split': 2,
'n_estimators': 50
}

```

---

## Performance

| Metric | Value |
|------|------|
| Accuracy | 88.18% |
| Cross Validation | ~88% |

---

## Model Export

The trained model is saved using:

```

import joblib
joblib.dump(rf, "classifier.joblib")

```

Load the model:

```

model = joblib.load("classifier.joblib")

```

---

# 🛠 Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib

---

# Application

This models power a **student mental health monitoring system** that:

- predicts stress levels
- analyzes menstrual cycle stress
- provides personalized recommendations
- visualizes stress trends
  
---

