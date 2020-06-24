# Predicting the Length of MLB Careers from Minor League Stats

## Overview
In Major League Baseball, data science has become an incredibly popular tool for player evaluation. However, General Managers (GMs) for teams have always needed to have a way to evaluate players in order to understand whether to draft them or acquire them through other means. For this project, I will pretend like I’m a data scientist for a professional baseball team and see if I can predict the length of a professional baseball player’s career by looking at their stats in the minor leagues. For some context, professional baseball teams all have “farm systems” with several levels of minor league teams that newly drafted players play in before reaching the Major Leagues. This is useful because the teams draft 18-20 year olds who need to spend years in the minor leagues before they have the skills necessary to be effective players at the top level. So while GMs are of course very focused on the current professional team, they need to always be developing talent that will be ready to contribute to the major league team years down the line. In fact, they need to know exactly how good each player in their “farm system” is expected to be in the majors in order to make decisions about trades and future draft picks. 


## Objective

My goal is to create a linear regression model that will predict how good a major league player someone will be based on their minor league statistics. In order to make this a problem that a linear regression model can solve I will measure “good” players by how long their careers were (specifically in how many at-bats they had at the major league level). Since teams are continually trying to field the best team as possible, the best players should get the most at-bats.


## Features

The features used to try and predict MLB at-bats were:
1. Minor League Runs per AB
1. Minor League Strikeouts per AB
1. Minor League On base plus slugging percentage (OPS)
1. Age player made it to the MLB
1. If the player went to college or not
1. What draft round was the player drafted in?
1. Player BMI
1. Player Position
1. Right or left handedness

## Findings:

The final R^2 score was 0.408 and was given by a Ridge Linear Regression model. Ultimately, all three regression models I used (OLS, Ridge, and Lasso) were very similar. 

Given that the R^2 is low, it does not make sense to use this model for prediction. However, what is useful is the relative weight of the coefficients. This gives us an idea of which stats we should pay attention to more when looking at minor league player stats. 

According to the model, the features with the highest impact on at-bats were:
1. Debut Age
1. Strikeouts per at-bat
1. On base plus slugging percentage 
1. Runs per AB

Debut age makes sense since the early you enter the MLB the more likely you are to have more at-bats. However, the other three give us useful statistics to focus on when looking for players that might have a long MLB career. We should look for players who don't strike out very much, have a high OPS and account for a large amount of runs. 

It's also interesting to note that the position, handedness, and round drafted do not make much of an impact. 

## Navigating the Project Files:
You should follow the following workflow when going through my work to repeat the results: 
1. Start at 01_data_collection.ipynb to see my first round of web scraping
1. Next go to 03_EDA.ipynb to see my MVP model. 
1. Before finishing the EDA notebook, go to 02_data_collection.ipynb to see my second round of web scraping and feature engineering
1. Head back to 02_EDA.ipynb to see the next iteration of my OLS models
1. Finally, go to 04_model_selection.ipynb to see the regularization and validation steps I took to arrive at my final Ridge model

Also, some of the data collection functions take a while to load so I've included a pkl file to the dataset I used in the model selection notebook so you don't need to generate it from scratch.

