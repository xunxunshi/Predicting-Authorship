# Predicting Authorship From Book Passages
This project aims to select/tune an optimal supervised learning classifier to predict the author of a passage. 
Passages were taken from five Gutenberg digital books written by different authors and in varying era. 
The goal is to determine the optimal algorithm (with the optimal parameters) that would be able to correctly classify the author of a given passage. 

### Data and preprocessing 
To aggregate this dataset, 200 passages containing 100 words each were randomly taken from 5 different books in the NLTK Corpus library (a total of 1000 instances). 
All punctuations were taken out of each passage, and words were lemmatized into their roots. 

The five different books include:
1.	The Man Who Was Thursday - G. K. Chesterton  (1908)/ Chesterton-Thursday 
2.	Alice’s Adventures in Wonderland – Lewis Carroll  (1800) /  Carroll Alice 
3.	Stories – E. Bryant (1900-2000) /  Bryant-stories  
4.	Paradise Lost – John Milton (1667) /  Militon-Paradise 
5.	Hamlet – William Shakespeare (1609) /Shakespeare-Hamlet

### Feature Engineering 
- TF-IDF 
- Bag of Words 

### Models Implemented 
- Support Vector Classifier 
- Random Forest 
- Naïve Bayes

### Model Building Process 
- Train/Test/Validation split: 
- Train/Test (70% of total data) : used to perform ten fold cross validation with grid search during hyper parameter selection 
- Validation (30% of data): used for testing by the tuned algorithm to ensure low variance ( prevent overfitting) 
- GridsearchCV was used to perform the grid search for each parameter

### Grid Search Results  
#### Ten fold cross validation results for algorithms implemented with TF-IDF
The following table shows the 10 fold cross validation results for varying hyper parameters in the different algorithms (Random Forest, SVC, and Naïve Bayes) implemented with TF-IDF. This process was repeated for BOW as well. 

![image](https://user-images.githubusercontent.com/29676594/115343841-7bcc4a00-a17a-11eb-9962-de2b22be39a8.png)

#### Optimal parameters for each feature engineering and algorithm combination 
![image](https://user-images.githubusercontent.com/29676594/115340646-16298f00-a175-11eb-8e29-f6c14084b3d3.png)

###  Testset Results 
Aggregated accuray score of the testset results. Bag of word/SVC generated very similar prediction results as Tf-idf/SVC! SVC seems to perform the best, with Naïve Bayes right behind, followed by Random Forest. 

Note: This does not mean Random Forest can not be implemented for this dataset, it's possible that insufficient amount of hyper parameters were investigated for RF (number of trees/ whether to use bootstrap). Other parameters such as number of splits or depth of trees could be invesigated to improve this model. Different strategies such as boosting could also be implemented.

![image](https://user-images.githubusercontent.com/29676594/115340712-35c0b780-a175-11eb-80a5-39812a607dc5.png)

###  Final Tuned Predictor Results 
* The optimal algorithm is SVC with TF-IDF(C=10,loss='hinge). 
* Confusion matrix and ROC of the predictor's performance on the test set is impressive: majority of the values of the confusion matrix is in the diagonal, and AUC is mostly 1. 
* The final predictor achieves an accuacy of 99% on the test set data! 

![image](https://user-images.githubusercontent.com/29676594/115344869-fc3f7a80-a17b-11eb-8a99-8afbf642d8be.png)
![image](https://user-images.githubusercontent.com/29676594/115344878-ff3a6b00-a17b-11eb-9061-688cfce3e515.png)
 
