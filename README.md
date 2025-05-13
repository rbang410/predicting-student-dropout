# Predicting Student Dropout in Higher Education

**INST414 Sprint 3 Project**  
Rishabh Banga — University of Maryland, College Park

---

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Repository Structure](#repository-structure)  
3. [Prerequisites & Setup](#prerequisites--setup)  
4. [Data Preparation & Analysis](#data-preparation--analysis)  
5. [Generating Visualizations](#generating-visualizations)  
6. [Results & Presentation](#results--presentation)  
7. [Reproducing on GitHub](#reproducing-on-github)  
8. [License](#license)  

---

## 🚀 Project Overview

Universities lose billions each year to student attrition. This project leverages machine-learning models to predict which students are at risk of dropping out, enabling proactive interventions (tutoring, financial aid, mentorship). We train and compare:

- **Logistic Regression**  
- **Random Forest**  
- **XGBoost (Gradient Boosted Trees)**  

on a Kaggle dataset of 76,518 student records, featuring academic, demographic, behavioral, and financial variables.

---

## 📁 Repository Structure

predicting-student-dropout/
├── environment.yaml # Conda environment specification
├── data/
│ ├── raw/ # (✱) Put student_dropout_data.csv here
│ └── processed/ # Generated processed_data.csv
├── models/ # Saved models (.pkl)
├── reports/
│ └── figures/ # Generated charts/images
├── run_analysis.py # End-to-end data cleaning, feature engineering, training & evaluation
├── run_visualizations.py # Generates all presentation figures
└── README.md # This file

yaml
Copy
Edit

- **(✱) Raw data**: Obtain from Kaggle, rename to `student_dropout_data.csv`, and place in `data/raw/`.

---

## ⚙️ Prerequisites & Setup

1. **Clone the repository**  
   ```bash
   git clone https://github.com/<your-username>/predicting-student-dropout.git
   cd predicting-student-dropout
Create & activate the Conda environment

bash
Copy
Edit
conda env create -f environment.yaml
conda activate dropout-pred
(Optional) Generate requirements.txt for pip users

bash
Copy
Edit
pip freeze > requirements.txt
🏃 Data Preparation & Analysis
run_analysis.py
This single script performs:

Loading & Cleaning

Reads data/raw/student_dropout_data.csv

Removes invalid GPAs (<0) and drops rows missing GPA, attendance_rate, or status

Feature Engineering

GPA Bins: Low (≤10), Med (10–14), High (>14)

Engagement Score: Average of attendance_rate and num_evaluations

Financial Stability: 1 if scholarship_amount>0 and debt_amount<10000, else 0

One-hot encoding of major and gpa_bin

Balancing & Splitting

Uses SMOTE to oversample the minority “Dropout” class

Splits into train/test sets (80/20)

Model Training

Trains Logistic Regression, Random Forest, XGBoost on the training set

Prints Accuracy, Precision, Recall, AUC-ROC for each

Saving Outputs

Processed data → data/processed/processed_data.csv

Models → models/logistic.pkl, models/random_forest.pkl, models/xgboost.pkl

Run it with:

bash
Copy
Edit
python run_analysis.py
📊 Generating Visualizations
run_visualizations.py
Loads your processed data and saved models to produce:

Class Distribution Pie Chart

GPA Distribution by Status (stacked histogram)

Engagement vs. GPA Scatter Plot

Model Performance Metrics (bar chart)

ROC Curve (XGBoost vs. random chance)

Feature Importances (bar chart)

Confusion Matrix Heatmap

Images saved to:

bash
Copy
Edit
reports/figures/
├── class_distribution.png
├── gpa_distribution.png
├── engagement_vs_gpa.png
├── model_metrics.png
├── roc_curve.png
├── feature_importance.png
└── confusion_matrix.png
Run it with:

bash
Copy
Edit
python run_visualizations.py
📈 Results & Presentation
All generated figures are in reports/figures/ for embedding in slides or posters.

The final PowerPoint deck (.pptx) using UMD Fearlessly Forward template is available separately (or can be re-generated with provided visuals).

🔄 Reproducing on GitHub
Initialize & commit

bash
Copy
Edit
git init
git add .
git commit -m "Initial commit: pipeline & documentation"
Add remote & push

bash
Copy
Edit
git remote add origin https://github.com/<your-username>/predicting-student-dropout.git
git branch -M main
git push -u origin main
