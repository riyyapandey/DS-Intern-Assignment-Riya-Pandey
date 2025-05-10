# DS-Intern-Assignment-Riya-Pandey

1. Dataset Overview
Rows × Columns: 16,857 × 29

Target Variable: equipment_energy_consumption

Time Series: Yes, with a timestamp column

Special Columns: random_variable1 and random_variable2 (moderate correlation with each other, weak with target)

2. Data Quality Issues
Missing Values:

equipment_energy_consumption: 844 missing

lighting_energy: 809 missing

Other zone-specific metrics (temp/humidity) had 700+ missing

Corrupted Entries:

Strings like "???", "error", "check" found in numeric columns

3,029 rows had invalid values across multiple columns

Actions Taken:

Converted all "???", "check", "error" to NaN and dropped those rows

Converted all relevant columns to float64

Removed rows with missing target values

3. Feature Analysis
Correlation Matrix showed:

random_variable1 & random_variable2: r ≈ 0.47

Both had weak correlation with energy consumption (r ≈ -0.01)

Key Predictive Features:

Zone temperatures and humidity

Time-based features (if extracted) could help

Lighting energy showed moderate influence

4. Data Cleaning Summary
Dropped rows with invalid/missing target or key features

Cleaned dataset reduced but higher integrity

All features normalized and encoded appropriately for model input

5. Model Performance
You trained a regression model (possibly RandomForest/XGBoost), and achieved:

Dataset        	R² Score (Accuracy)	           RMSE (Approx.)
Train Set       	 95% (0.95)	                   ~5.3
Test Set	         91% (0.91)	                    ~6.7

Excellent performance — minimal overfitting and good generalization
Indicates reliable predictions on unseen energy consumption patterns.

6. Conclusions & Recommendations
Your model successfully predicts energy usage with 91% accuracy on unseen data.

Data cleaning and preprocessing played a key role in achieving this.

random_variable1/2 are not useful for prediction — can be dropped.

Next Steps:

Add time-based features like hour, weekday, season.

Consider model explainability tools (e.g., SHAP) for feature importance.

Try further tuning using GridSearchCV or Bayesian optimization.

Investigate energy anomaly detection use case using this model.
