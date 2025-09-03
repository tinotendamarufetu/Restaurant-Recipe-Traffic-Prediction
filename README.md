# 🍲 Recipe Traffic Prediction: Data Cleaning, EDA & Classification Models

## 📌 Project Overview
This project analyzes a dataset of **947 recipes** with nutritional and categorical information to predict whether a recipe will attract **high site traffic**.  
The goal is to combine **data cleaning, feature engineering, exploratory analysis, and supervised learning** to deliver both business insights and predictive power.  

This project was developed and designed with **real-world business focus** in mind — turning raw recipe data into actionable recommendations for a recipe platform.  

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/62515cb5-57df-4bde-8608-39b2e6359b68" />

---

## 📊 Dataset
The dataset contains **13 columns** with nutritional and categorical details:  

- `recipe` → unique recipe ID (not used for modeling)  
- `calories`, `carbohydrate`, `sugar`, `protein` → nutritional values  
- `category` → recipe category (Meat, Vegetable, Dessert, etc.)  
- `servings` → number of servings per recipe  
- `high_traffic` → target variable (High vs Unknown traffic)  
- **Engineered Features**:  
  - `calories_per_serving`  
  - `protein_ratio`, `carb_ratio`, `sugar_ratio`  
  - `high_calorie` (binary indicator)  

---

## 🧹 Data Validation & Cleaning
- Checked for missing values, data types, duplicates.  
- Filled missing nutritional values with **median** instead of dropping rows.  
- Replaced missing `high_traffic` with `"Unknown"`.  
- Cleaned `servings` column (e.g., `"4 as a snack"` → `4`).  
- Standardized categories, merging `"Pork"` and `"Chicken"` into `"Meat"`.  
- Engineered features like **calories per serving** and **macronutrient ratios** for richer analysis.  

---

## 🔎 Exploratory Data Analysis (EDA)
We explored the data visually using **Seaborn** and **Matplotlib**, focusing on both raw and engineered features.  

- **Histogram of Calories** → Most recipes are under 500 calories, with strong right skew.  
- **Category Counts** → Meat and Vegetable recipes dominate the dataset.  
- **Calories vs Protein Scatterplot** → Meat drives protein intake, Beverages & Desserts add calories but little protein.  
- **Calories per Serving (Boxplot)** → Desserts and Meat are calorie-dense; Vegetables and Beverages are lighter.  
- **Macronutrient Ratios (Stacked Bar)** → Meat is protein-heavy, Vegetables are carb-balanced, Desserts are sugar-dominant.  
- **High vs Low Calorie Recipes (Countplot)** → Most recipes are low-calorie, with only a few dense outliers in Meat and Dessert.  

---

## 🤖 Model Development
Problem type: **Classification** (predict `high_traffic`).  

- **Baseline Model**: Logistic Regression (simple, interpretable).  
- **Comparison Model**: Decision Tree (captures non-linear interactions). 

Features used:  
- Nutritional values (`calories`, `carbohydrate`, `sugar`, `protein`)  
- Engineered features (`calories_per_serving`, nutrient ratios)  
- `servings`  
- `category` (one-hot encoded)  

---

## 📈 Model Evaluation
We used multiple metrics to ensure robust evaluation:  

- **Logistic Regression**:  
  - Accuracy: **72%**  
  - AUC: **0.74**  
  - Precision (High Traffic): **0.83**  
  - Recall (High Traffic): **0.39**  

- **Decision Tree**:  
  - Accuracy: **64%**  
  - AUC: **0.62**  
  - Precision (High Traffic): **0.56**  
  - Recall (High Traffic): **0.53**
 
  <img width="1930" height="777" alt="image" src="https://github.com/user-attachments/assets/6dc40421-930b-48d2-8f59-8ebdf004b744" />

**Findings:** Logistic Regression was more stable and interpretable, while the Decision Tree caught more popular recipes but at the cost of overall reliability.  

---

## 📊 Business Metrics
From a business perspective, the key KPI is **recall on high-traffic recipes**:  
- It is better to catch as many popular recipes as possible so they can be promoted.  

- Logistic Regression → Stronger overall model, best balance between accuracy and interpretability.  
- Decision Tree → Highlights opportunities to capture more high-traffic recipes if recall can be improved.  

---

## 📌 Business Recommendations
1. **Deploy Logistic Regression** as the first predictive model.  
2. **Monitor Recall** on high-traffic recipes as the KPI.  
3. **Iteratively improve models** with ensembles (Random Forest, Gradient Boosting).  
4. **Leverage insights from EDA**:  
   - Promote Meat dishes as protein-rich highlights.  
   - Use Vegetable dishes to target health-conscious users.  
   - Manage Desserts and Beverages carefully — calorie-heavy but nutritionally weak.  
5. **Collect more engagement data** (clicks, shares, likes) to strengthen predictions beyond current features.  

---

## 🛠️ Tech Stack
- Python  
- Pandas, NumPy (data wrangling)  
- Seaborn, Matplotlib (visualization)  
- Scikit-learn (modeling, evaluation)  
- Jupyter Notebook  

---

## 🎯 Key Learnings
- How to clean and validate real-world categorical and numeric data.  
- The importance of **feature engineering** for richer insights.  
- Trade-offs between simple interpretable models vs flexible but riskier ones.  
- Translating technical results into **business-relevant recommendations**.  

---
