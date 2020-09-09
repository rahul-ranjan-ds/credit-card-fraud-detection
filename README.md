# credit-card-fraud-detection
Build a predictive model to recognize fraudulent credit card transactions so that customers are not charged for items that they did not purchase.

# Data Understanding
•	The datasets contains transactions made by credit cards in September 2013 by European cardholders.
•	It has transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.
•	It contains only numerical input variables (V1, V2 … V28) which are the result of a PCA transformation. Features which have not been transformed with PCA are 'Time' and 'Amount'.
•	Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.
# Data Pre-Processing
•	Mostly the PCA transformed variables are Gaussian Normal distribution as per the Central limit theorem for a large number of data points. But histogram and distribution plots of variables show some skewness still left. Thus sklearn PowerTransformer is used to transform the variables into more normal distribution.
•	The scatter plot is then plotted to view the Time and Amount feature distribution for different classes. The plot shows Time feature as evenly distributed and thus of very little or no significance. Thus the Time variable is dropped.
Test- Train Split
•	The data is then split into 70% Training and 30% test set using stratify=True, such that the Imbalance is preserved.
# Model Building 
1.	Imbalanced Training data
•	Build Models (Logistic Regression, KNN, SVM, Decision Trees and Random Forest) on the imbalanced training data.
•	Hyper parameters tuning is done using cross-validation (Stratified Kfold) and GridSearchCV.
•	Models using hyper parameters with best roc-auc score is selected.
2.	Random Oversampling
•	Build Models (Logistic Regression, KNN, SVM, Decision Trees and Random Forest) on the balanced training data using Random Oversampling.
•	Hyper parameters tuning is done using cross-validation (Stratified Kfold) and GridSearchCV.
•	Models using hyper parameters with best roc-auc score is selected.
3.	SMOTE
•	Build Models (Logistic Regression, KNN, SVM, Decision Trees and Random Forest) on the balanced training data using SMOTE.
•	Hyper parameters tuning is done using cross-validation (Stratified Kfold) and GridSearchCV.
•	Models using hyper parameters with best roc-auc score is selected.
4.	ADASYN
•	Build Models (Logistic Regression, KNN, SVM, Decision Trees and Random Forest) on the balanced training data using ADASYN.
•	Hyper parameters tuning is done using cross-validation (Stratified Kfold) and GridSearchCV.
•	Models using hyper parameters with best roc-auc score is selected.
# Model Selection
•	Select the oversampling method which shows the best result on a model.
•	Apply the best hyperparameter on the model.
•	Predict on the test dataset
•	Evaluate on roc-auc score, Precision and Recall. Model with good Recall is selected for the European bank as catching fraud is of paramount importance (which may include a few non-fraudulent cases).
