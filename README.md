# Diabetes Disease Progression Prediction (Health Domain)

Thiranex Task 4: Real-world Data Project.

## Objective
Predict how much a diabetes patient's disease will progress one year after baseline, using clinical measurements.

## Dataset
Scikit-learn Diabetes dataset: 442 patients, 10 features (age, sex, BMI, blood pressure, 6 blood serum measurements: total cholesterol, LDL, HDL, TCH ratio, log triglycerides, glucose). Target: quantitative disease progression score. No missing values.

## Approach
1. Data loading and cleaning
2. EDA: target distribution, feature spread, correlation heatmap
3. 80/20 train-test split (random_state=42) and 5-fold cross validation
4. Four regression models compared: Linear Regression, Ridge, Random Forest, Gradient Boosting
5. Evaluation with R2, RMSE, MAE; feature importance of the best model

## Results
| Model | R2 | RMSE | MAE | CV R2 (mean) |
|---|---|---|---|---|
| Gradient Boosting | 0.482 | 52.38 | 42.51 | 0.449 |
| Random Forest | 0.457 | 53.62 | 43.48 | 0.438 |
| Ridge | 0.454 | 53.78 | 42.81 | 0.482 |
| Linear Regression | 0.453 | 53.85 | 42.79 | 0.482 |

## Key Insights
- Gradient Boosting scored best on the test set (R2 = 0.482). Under cross validation, the linear models were slightly better (0.48), so all four models perform similarly.
- Top predictors: **BMI (41%)**, **serum triglycerides / ltg (31%)**, **blood pressure (10%)**.
- BMI has the strongest correlation with progression (0.59); HDL ("good" cholesterol) is the only feature negatively correlated (-0.40).
- Average prediction error is about 43 points on a score averaging 152.
- Clinical measurements explain under half of the variance, so they should support, not replace, a doctor's judgement.

## Visualizations (`output/`)
- `1_distribution.png`: target distribution and feature spread
- `2_correlation.png`: correlation heatmap
- `3_model_comparison.png`: R2 / RMSE / MAE per model
- `4_best_model.png`: feature importance and actual vs predicted
- `model_comparison.csv`, `feature_importance.csv`: result tables

## Conclusion
Weight (BMI), triglyceride level and blood pressure are the main drivers of diabetes progression in this data. Controlling them is the most useful intervention. Next steps: hyperparameter tuning, more patient data and additional lifestyle features.

## How to run
```
pip install pandas numpy scikit-learn matplotlib seaborn
jupyter notebook health_data_project.ipynb
```
