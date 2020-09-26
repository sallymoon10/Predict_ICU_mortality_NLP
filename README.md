# Predict_ICU_mortality_NLP


### Highlights:
- Predict ICU mortality based on clinicians notes and tabular data (ie. patient information, vitals, etc) by training a logistic regression model on TFIDF features from notes and tabular data. Evaluate fairness of model (parity gap, recall gap, specificity gap) 
- Obtained 0.87 AUC in in mortality prediction
- Found that the model favored males in predicting mortality rate according to recall gap between male and female
- Tech: Python (NLTK (TFIDF), SkLearn, Scipy, Numpy, Pandas), matplotlib)
- Work completed: Data exploration (plotting distributions of gender, ethnicity, language, etc), data processing (filtering notes by time, tokenizing, transforming to TFIDF features), training logistic regression model, evaluating model (AUC), evaluating fairness metrics (parity gap, recall gap, specificity gap) by gender

![Alt text](/assets/results.png?raw=true=50x50  "Forecasting results on test dataset")

### Dataset:
- MIMIC-III, a freely accessible critical care database. Johnson AEW, Pollard TJ, Shen L, Lehman L, Feng M, Ghassemi M, Moody B, Szolovits P, Celi LA, and Mark RG. Scientific Data (2016). DOI: 10.1038/sdata.2016.35. Available from: http://www.nature.com/articles/sdata201635

### TFIDF features:
- TF-IDF evaluates how relevant a word token is to a document in a set of documents. This is calculated by multiplying how frequently the word appears in a document and the inverse document frequence of the word across a set of documents. 
- This allows us to rank words that appear numerously in all documents (eg. and, or, etc) lower and rank higher the words that are relevant to understanding the context of the document
- Clinician's notes can be transformed to TF-IDF features and be used to train models to predict variables given text data


### Fairness metrics:

Recall gap (equalized odds): (TP / TP + FN) 
- Recall gap calculates the gap between how acculately positive predictions are made out of all positive examples between sesitive populations
- A classifier with low recall gap across sensitive populations is a classifier that predicts labels equally well 

Specificity gap (specificity parity): (TN / TN + FP)
- Specificity gap calculates the gap between how accurately negative predictions are made uot of all negative examples between sensitive populations
- This is considered the inverse of the recall gap

Parity gap (demographic parity): (TP + FP) / N
- Parity gap calculates the gap between absolute sum of predicted positive labels among sensitive populations. 
- It calculates whether sensitive populations have equal chances of being predicted as the positive label. 
- However, this metric is not very useful in healthcare because some positive labels are more prevalent in certain populations by nature. For example, when predicting for breast cancer, the parity gap between females and males will expectedly be very high. The assumption that all sensitive populations should have equal true positive labels by nature should hold true for parity gap to be a useful metric. 

Thoughts on fairness and healthcare:
- Individual fairness in healthcare calculates whether individuals of similar characteristics receive similar treatment or outcomes . However, this is tricky to define because provided healthcare is widely varied based on the healthcare provide, or even geographical location that the patient received care. Furthermore, it is tricky to define which individuals are similar. Many factors beyond medical condition, such as gender, race, socioeconomic background, etc. can describe individuals and all factors may affect their health outcomes. 

### References:
- Course project: CSC2541 (Machine Learning in Healthcare), University of Toronto
