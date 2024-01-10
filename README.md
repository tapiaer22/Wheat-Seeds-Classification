# Wheat Seeds Classification
An Analysis was performed on a group of seed kernels (<a href="https://archive.ics.uci.edu/dataset/236/seeds">source here</a>) that were part of 3 classes of wheat: Kama (Type 1), Rosa (Type 2), and Canadian (Type 3). The Analysis has the purpose to identify how these classes differ within multiple variables, find a predictive model to accurately classify samples, and infer conclusions in the process.

Hypothesis Testing is a powerful tool to analyze and demonstrate evidence of significant differences between variables, distributions, and groups. The K-means clustering method is useful in identifying patterns and classifies them into partitions and clusters. Using both tools in analysis provide evidence for stronger conclusions and insights on what variables are good at classifying, why they are good, and how they contribute to a prediction.

In this project, the following were done:
- Analyze variables
- Find evidence in differences of groups
- Implement a classification model
- Predict the class of a sample
- Infer powerful and detailed conclusions

If you would like to see the code and detailed explanations in the process, check out the file <a href="https://github.com/tapiaer22/Wheat-Seeds-Classification/blob/main/Wheat_Seeds_Classification_DataAnalysis.ipynb">Wheat_Seeds_Classification_DataAnalysis.ipynb</a>

## Key Conclusions
### Assumption of Normality in Distributions
After testing each distribution and deciding that the  D’Agostino and Pearson’s (dap) test was appropriate for this task, I classified the distributions as either "normal" or "not normal". Consequently, for the sake of this project, I only included "normal" distributions in the analysis:

(Image for normality table here)

### The Groups with the Most Differences
The groups that had generally the major statistically significant differences were `area`, `perimeter`, `length`, and `width`. This is clearly evident in the hypothesized distributions. A statistically significant difference implies that it would be easier to distinguish the class of a sample (and this is proved with the results from the K-means method later on). 

(Hypothesized distributions of variables with differences)

With `compactness` and `groove`, on the other hand, it is very hard to generally identify differences. The tests resulted in the failure to reject the null hypothesis, implying that there is no difference between the 2 tested groups. If you were to randomly measure the `compactness` of a sample, you won't be able to tell if the sample is from type 1 or type 2. The same happens on `groove` with type 1 and type 3.

(Hypothesized distributions of variables with no significant differences)

### The Best Variable Predictors and Synergy of Variables
To support the claims of the hypotheses and find the best classification model with the K-means method, I used all combinations of variables to test and verify which combinations had the best accuracy. The `area` and `perimeter` happened to be in the accurate models, while `groove` and `compactness` were the worse in prediction. 

(Table with Top 5 and Worse 5)

The synergy of variables towards the model can be explained with the results obtained in hypothesis testing. But what is synergy of variables? The synergy of variables is how well the variables perform as a group. A good synergy is able to classify properly even in complex scenarios of data.

Bad synergy in classification:
(Example of Bad Synergy)

Good synergy in classification:
(Example of Good Synergy)

The accuracy of the model can be explained with how much synergy exists in the combination of variables for the model. The following synergy cases were identified in the project: 

- Some combinations of variables were great because they complemented each other with their strengths and weaknesses.

  Assume there are two different variables: x1 and x2. Even though variable x1 has no significant difference between class 1 and  class 2, there is another variable x2 with significant difference between those classes, which may help determine the difference that x1 was not able to discern. Take `groove` as an example: it fails to tell a difference between class 1 and class 3, but `width` is fairly good at classifying class 1 and class 3. Putting both together result in better chances of classifying classes correctly, and they turn each of their weaknesses into a strength. This is evident in the table of accuracy.

(Rank and pvalues of groove, rank and pvalues of width, rank of combined)

- A good predictor variable in a combination 'carries the group', meaning the accuracy score is only good because of one variable while there is no synergy at all.

  Take `area` and `groove` as an example: area is highly efficient in determining the difference with an accuracy score of (0.84) while groove is weak with a score of (0.65). Now, if you combine both of them, you will get a score of (0.84), which does not improve with respect to the score of the `area`. Even though the score of groove was low, since area was good at determining a difference it will help groove appear in the top of the list even though it did not improve accuracy at all; it was the area the variable responsible for such a high score.

(Rank and pvalues of area, rank and pvalues of groove, rank of combined)
