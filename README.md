# Predicting Pharmacutical Sales

My objective was to forecast pharmaceutical sales with machine learning models. I utilized this [dataset](https://www.kaggle.com/datasets/milanzdravkovic/pharma-sales-data), comprised of over 600,000 transactional records gathered over a six-year period (2014-2019). I aimed to predict sales quantities after 2019.

## Questions to Consider:

* Given the data available, what ATC category sells the largest quantities over time?
* Are there certain period which more drugs are sold?

## Data Description

Sales data are resampled to the hourly, daily, weekly and monthly periods. 57 drug types were sampled and classified to the following Anatomical Therapeutic Chemical (ATC) Classification System categories:

| Feature Descriptions  |
|---|
| M01AB : Anti-inflammatory and antirheumatic products, non-steroids, Acetic acid derivatives and related substances  |
| M01AE : Anti-inflammatory and antirheumatic products, non-steroids, Propionic acid derivatives  |
| N02BA : Other analgesics and antipyretics, Salicylic acid and derivatives  |
| N02BE/B : Other analgesics and antipyretics, Pyrazolones and Anilides  |
| N05B : Psycholeptics drugs, Anxiolytic drugs  |
| N05C : Psycholeptics drugs, Hypnotics and sedatives drugs  |
| R03 : Antihistamines for systemic use  |

## Data Cleaning and Exploration

**This can be run using the ipynb file "Data Analysis and Visualization".**

I loaded the daily sales data and updated the "datum", "Year", and "Month" columns to datetime.
Using pd.melt I reshaped the data from wide to long where each row represents a individual observations for each drug unit sold. 

After calculating quantity sold per month, I visualized the results with plotly: <br>

![month](Images/month.PNG)

Using the monthly sales data I created a correlation matrix heatmap: <br>

![heatmap](Images/heatmap.PNG)

This is within the ipynb file "Predicting Sales with a Random Forest Model". The correlation coefficient quantifies the strength of a linear relationship between two variables. The correlation coefficient can range from -1 to 1. <br>
Positive correlation: as the value of one variable increases, the value of the other variable also tends to increase.<br>
Negative correlation: as the value of one variable increases, the value of the other variable tends to decrease. <br>
Strong correlations: <br>
M01AE AND N02BE<br>
N02BA AND N02BE<br>
R03 AND N02BE<br>

Quantity sold per year was visualized as well: <br>

![year](Images/year.PNG)

![yearline](Images/yearline.PNG)

M01AE which are anti-inflammatory and antirheumatic products, non-steroids, Acetic acid derivatives and related substances were sold in the highest quntities through both months and years.

### Linear Regression Model

Next, I created a linear regression model using the "Year" variable to reshape the data as a single column array. The dependent variable was "Quantity". Predictions were fit into a linear regression: <br>

![linear](Images/linear.PNG)

The metrics were quite poor which means that a linear regression model does not explain the variance of the dependent variable. The variables may be too complex or non-linear. Next, I will explore more complex models.

### Random Forest Regressior Model

**This can be run using the ipynb file "Predicting Sales with a Random Forest Model".**

