# 🩺 Diabetes Health Risk Prediction (BRFSS 2021)

## Project Overview

This project implements an end-to-end Machine Learning pipeline to predict an individual's risk of developing **Diabetes or Pre-diabetes** using health and lifestyle indicators from the **Behavioral Risk Factor Surveillance System (BRFSS) 2021** dataset.

The workflow covers comprehensive **Exploratory Data Analysis (EDA)**, **Data Preprocessing** (including scaling, outlier handling, and feature engineering), and **Feature Selection** based on correlation to prepare a clean dataset for model training. The final deliverable includes a conceptual ML pipeline visualization and a live, interactive Streamlit web application prototype for prediction.

### 🎯 Objective
* Perform deep analysis on the BRFSS 2021 dataset to identify key predictors of diabetes.
* Clean, transform, and prepare the data for classification modeling.
* Select the most relevant features to build an efficient predictive model.
* Develop an interactive web application to demonstrate the prediction capability.

---

## 💻 Technical Stack

* **Language:** Python
* **Data Analysis & Manipulation:** `pandas`, `numpy`
* **Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (for preprocessing and model training)
* **Deployment:** `Streamlit`, `pyngrok`
* **Visualization Utility:** `graphviz` (for pipeline diagram)

---

## 📂 Data & Workflow

### Dataset
The project utilizes the `augmented_diabetes_012_health_indicators_BRFSS2021.csv` dataset, where the target variable is **`Diabetes_012`**:
* **0:** No Diabetes
* **1:** Pre-Diabetes
* **2:** Diabetes

### 📊 Exploratory Data Analysis (EDA) Highlights
EDA revealed crucial relationships between key health indicators and diabetes status:

| Feature | Insight | Visualization |
| :--- | :--- | :--- |
| **BMI** | Higher BMI is strongly associated with increased diabetes risk. |  |
| **Age** | Older age groups show a higher prevalence of diabetes. |  |
| **GenHlth** | Individuals rating their General Health as Fair/Poor are significantly more likely to have diabetes. |  |
| **CholCheck** | The majority of individuals with diabetes have had a cholesterol check. |  |
| **Income** | Lower income levels correlate with a higher incidence of diabetes. |  |

### ✨ Data Preprocessing Pipeline

The project follows a standard ML pipeline, visualized below:

1.  **Load Dataset**
2.  **Handle Duplicates** (Duplicates were checked and removed.)
3.  **Feature Engineering** (`Sex` encoding, `Age_Group` creation.)
4.  **Handle Outliers** (Using IQR method on numeric columns: BMI, Age, MentHlth, PhysHlth.)
5.  **Scale Features** (`StandardScaler` applied to numeric features.)
6.  **Feature Selection** (Selecting features with $\text{Correlation} > 0.1$ with `Diabetes_012`.)
7.  **Save Processed Data** (`processed_features.csv`, `processed_target.csv`)



### 🔑 Selected Features

Based on the correlation analysis, the following features (among others) were selected for modeling: ['GenHlth', 'HighBP', 'HighChol', 'BMI', 'Age', 'DiffWalk', 'PhysHlth', 'Income', 'Stroke', 'HeartDiseaseorAttack', 'MentHlth', 'PhysActivity', 'Smoker']

## 🚀 How to Run the Project

### Prerequisites
1.  **Clone the repository:**
    ```bash
    git clone <repository-link>
    cd <repository-folder>
    ```
2.  **Install dependencies:**
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn streamlit pyngrok
    ```
3.  **Set up ngrok (for deployment):**
    You need an `ngrok` authtoken to deploy the Streamlit app publicly (as shown in the provided script).

### Running the Preprocessing and EDA

The core data processing and visualization steps are executed sequentially in the main Python script or Jupyter Notebook (assuming the provided code block is run).

### Running the Live Prediction App (Streamlit)

The prediction application (`app.py`) is deployed live using Streamlit and `ngrok`. *(Note: The model in `app.py` is trained on the smaller Pima Indians Diabetes Dataset for a quick, stable demo, but the preprocessing steps are applied to the main BRFSS data.)*

1.  **Run the deployment commands:**
    ```bash
    !streamlit run app.py &
    public_url = ngrok.connect(8501)
    print("Open this link to use the app:", public_url)
    ```
2.  **Access the App:** Open the `public_url` printed in the console in your web browser.

---

## 🤝 Contribution
This project is a solid foundation for a comprehensive health risk prediction system. Feel free to fork the repository, enhance the modeling phase (e.g., using Random Forest, XGBoost, or deep learning), and improve the Streamlit application interface!
