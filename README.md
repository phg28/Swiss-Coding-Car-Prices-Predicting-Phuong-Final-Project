![image](https://github.com/user-attachments/assets/11b34f59-aa44-4656-9b76-88d4984ba485)# [Final Project] - Uyen Phuong
## Car Prices Predicting

## About this project
This project seeks to analyze car price datasets to identify the features that influence car prices. Using these insights, we will develop a model to predict car prices based on the selected features.

## Data description
The datasets provide the information about different types of cars across the American market, data on vehicle features and prices of different car models.

## Data Source: Where Our Data Comes from 
Source: Public dataset from Kaggle (Car Price Prediction Multiple LinearRegression: https://www.kaggle.com/datasets/hellbuoy/car-price-prediction/data)

Structures: This datasets includes 26 columns and 205 rows.

**Car ID:** Unique identifier for each car model

**Symboling:** Insurance risk rating for the car

**Car name:** Name or model of the car

**Prices:** Price of the car

**Fuel type:** The type of fuel the car uses

**Aspiration:** Method of air intake for the engine (std or turbo)

**Door number:** Number of doors on the car 

**Car body:** Design or type of car body (sedan, hatchback, etc.)

**Drive wheel:** Type of drivetrain or wheels (FWD, RWD, 4WD)

**Engine location:** Engine location (front or rear)

**Wheel base:** Distance between front and rear axles

**Car length:** Length of the car

**Car width:** Width of the car

**Car height:** Height of the car

**Curb weight:** Weight of the car without passengers or cargo

**Engine type:** Type of engine (ohc, ohcv, etc.)

**Cylinder number:** Number of cylinders in the engine

**Engine size:** Size of the engine (in cc or ci)

**Fuel system:** Type of fuel injection system (mpfi, etc.)

**Bore ratio:** Ratio of cylinder bore diameter to stroke length

**Stroke:** Length of the engine stroke

**Compression ratio:** Engine compression ratio

**Horsepower:** Engine power output (in hp)

**Peak rpm:** Engine's peak RPM for generating power

**City mpg:** Fuel efficiency in city driving (mpg) 

**Highway mpg:** Fuel efficiency on the highway (mpg)

## Tools and Technologies:
Python, Pandas, Matplotlib, Seaborn, etc.

## Purpose and Outcome:
Purpose: To determine the features of a car that affect its price and to create predictive models with high accuracy.
Outcome: A precise model for predicting car prices, along with features that affect those prices.



## EDA: 

### AVG price by Car brand
![image](https://github.com/user-attachments/assets/19ce93f2-fb6c-47f4-8735-650969fbb161)

It can be seen that there is a difference in average price between car brands:
+ Top-notch car group: Jaguar, Buick, Porsche and BMW.
+ High-average car group: Volvo, Audi, Mercury, Alfa-Romero, Peugeot, Saab.
+ Affordable car group: Mazda, Nissan, Volkswagen,...

### Avg price by fuealtype used:
![image](https://github.com/user-attachments/assets/92c5a096-fa59-4dd1-9f72-9158ffbd5736)

On average, diesel-powered cars' price (~16000$) are slightly more expensive than petrol-powered cars (~13000$).

### Avg price by aspiration: 
![image](https://github.com/user-attachments/assets/701d31e3-ce2d-41e3-8ba2-4b6aa9c98b72)

On average, turbo cars' price (~17000$) are slightly more expensive than std cars (~13000$).

### Avg price by doornumber:
![image](https://github.com/user-attachments/assets/32b5a204-a7af-4c42-8d3e-eb509c479156)

There appears to be no significant price difference based on the number of doors in cars, as the average cost of 2-door and 4-door models does not vary by more than $1,000.

### Avg price by carbody:
![image](https://github.com/user-attachments/assets/1eb32a76-f17c-4eee-ba19-9af0d5c254d5)

Convertibles and hardtops have the highest average price, both around $23,000, with no distinction between the two. The other models are priced lower, averaging approximately $14,000 for sedans, $12,500 for wagons, and $10,000 for hatchbacks.

### Avg price by drivewheel: 
![image](https://github.com/user-attachments/assets/702c5a22-c327-46b2-8232-d399ae8c9697)

RWD cars, averaging around $20,000, have a significantly higher price than FWD cars (approximately $9,000) and 4WD cars (around $11,000).

### Avg price by Cylindernumber: 
![image](https://github.com/user-attachments/assets/acc7684f-956d-46a5-a400-d21cdb710208)

Cars with eight and twelve cylinders have the highest average prices, ranging from $31,000 to $32,000. Five and six-cylinder cars average between $21,000 and $23,000. In contrast, four-cylinder cars average $13,000, while two-cylinder and three-cylinder cars average $10,000 and $5,000, respectively.

### Avg price by Engine type: 
![image](https://github.com/user-attachments/assets/27b11bc1-bb47-4250-a67b-cc42bda7a5ce)

Cars with DOHC and OHCV engines have the highest average prices, at $31,000 and $25,000, respectively. 
DOHC vehicles average around $18,000. 
Meanwhile, cars with the other engine types range from $13,000 to $15,000.

### Avg price by Fuelsystem: 
![image](https://github.com/user-attachments/assets/857958d6-e579-433c-b5ba-0518ed382d6c)

Cars with MPFI fuel systems have the highest average price, around $18,000, followed by IDI cars at approximately $16,000. Both 4BBL and MFI cars are priced around $12,500, while SPDI and SPFI cars have an average price of about $11,000.

**Based on a visual analysis of the charts, it appears that the "doornumber" feature does not show any price differences among the types. This feature will be removed when integrating into the models.**

## Correlation: 
![image](https://github.com/user-attachments/assets/1328e306-903d-422a-90d3-d13faa35e48c)

This project primarily analyzes the features that affect car prices, so in this correlation, I will mainly focus on the relationship between price and each individual feature.
From the matrix, it is evident that, except for car height, stroke, compression ratio, and peak RPM, the remaining features all have a correlation with price. Specifically:
+ Negative correlation: city MPG, highway MPG.
+ Positive correlation: wheelbase, car length, car width, curb weight, engine size, bore ratio, horsepower.

**Features that do not show any correlation with price will also be removed when incorporating them into the regression model.**

## Key insights:
### General conclusion:
Here are the results of the features that influence car prices, selected using three different methods: 

1. Features filtered by EDA: wheelbase, carlength, carwidth, curbweight, enginesize, boreratio, horsepower, citympg, highwaympg, fueltype, aspiration, carbody, drivewheel, enginelocation, enginetype, cylindernumber, fuelsystem
   
2. Features filtered by RFE: symboling, wheelbase, carlength, carwidth, carheight, curbweight, enginesize, boreratio, stroke, compressionratio, horsepower, peakrpm, citympg, highwaympg, enginetype_ohc
  
3. Features filtered by RFE+VIF: enginetype_ohc, compressionratio, enginesize, citympg, carwidth, peakrpm, stroke.

From comparison, it can be noted that the features selected for the regression model through Exploratory Data Analysis (EDA) differ from those obtained using the Recursive Feature Elimination (RFE) and Variance Inflation Factor (VIF) methods. Even features that show no correlation in the correlation matrix can still be significant when using RFE and VIF, such as "stroke." 

Next, let's examine the results of the regression models with features selected through various methods.

## Regression Models:
**R2 score and Adjusted R2 score of regression models_result 1:**
![image](https://github.com/user-attachments/assets/222f251b-af13-4600-a38a-07f1043eded2)

The adjusted R² score for the training set is quite good, while the adjusted R² for the testing set is very poor. This discrepancy is due to the number of independent variables being too large compared to the number of samples tested, which results in a negative outcome. The negative result indicates that the model is over-parameterized. Overparameterization is a concept in machine learning (ML) that refers to a model having more parameters than the available training data.

**R2 score and Adjusted R2 score of regression models_result 2:**
![image](https://github.com/user-attachments/assets/7b0c7793-36fd-469c-9e7a-b746faabf97f)

After applying Recursive Feature Elimination (RFE), the number of independent variables was reduced to 15. This adjustment also improved the adjusted R² score for both the training and testing sets.

**R2 score and Adjusted R2 score of regression models_result 3:**
![image](https://github.com/user-attachments/assets/e843a893-c29e-47e7-a209-9cc586ec9af4)

There was a slight change in the adjusted R² score for the training data, and the adjusted R² score for the testing data improved significantly.

**Overall Conclusion**
Linear Regression: Has relatively low Training R2_Score and Testing R2_Score, especially the Testing adjusted_R2_Score, which only reaches 74.90. This indicates that the linear regression model does not fit the data well and struggles to compete with more complex models.

Decision Tree and XGBoost: Show good performance with both Training R2_Score and Testing R2_Score being high and a fairly high Testing adjusted_R2_Score. This demonstrates good generalization capability, meaning they can effectively predict on new data.

Random Forest: Achieves the highest Testing R2_Score and Testing adjusted_R2_Score, indicating the best overall performance among all models. It’s the most suitable choice for this dataset as it predicts well on new data.

LGBM: Has slightly lower Testing R2_Score and Testing adjusted_R2_Score compared to other models, possibly because the data structure does not fit as well with this algorithm compared to Random Forest or XGBoost.

### Recommendations:
For analyst:
Random Forest is the model with the best overall performance for this dataset.
Linear Regression has the lowest performance and is less likely to predict accurately on the test set.

If you want to further improve the models, you can try techniques such as hyperparameter tuning, feature engineering, or model ensembling to enhance overall performance.

For company:

