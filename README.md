# EECS731_Project3
Major Leagues Prediction

1. Set up a data science project structure in a new git repository in your GitHub account
2. Pick one of the game data sets depending your sports preference
https://github.com/fivethirtyeight/nfl-elo-game
https://github.com/fivethirtyeight/data/tree/master/mlb-elo
https://github.com/fivethirtyeight/data/tree/master/nba-carmelo
https://github.com/fivethirtyeight/data/tree/master/soccer-spi
3. Load the data set into panda data frames
4. Formulate one or two ideas on how feature engineering would help the data set to establish additional value using exploratory data analysis
5. Build one or more regression models to determine the scores for each team using the other columns as features
6. Document your process and results
7. Commit your notebook, source code, visualizations and other supporting files to the git repository in GitHub

# NFL Predictions
I chose to use the NFL data for this project because I know the most about the sport of football, so the data provided was easy to understand. The purpose of this project was to use regression to determine the score of a future NFL game, given past historicle data. This data included the ELO score of each team, the season, date of game, and several other factors about each game.

# Feature Engineering
For feature engineering I first disposed of data that did not provide me with additional information. The two pieces of information that provided me with no further information were: 

1- The date of the game. I plotted the date vs score for a random sample of 1000 games and saw no correlation. This makes sense as the date of a particular game should not affect how a certain team will play. For this reason, I removed dates from my data set.

2- The winner. I chose to remove the outcome for 2 reasons, first is that I already have the final score of each game, meaning I already know who won (telling me the winner creates redundancy in the data set). And secondly I do not care about who won, all I care about is the final score of the game. 

The next piece of feature engineering I performed was to label encode the team names so that they could be fed into my regression model. Because the list of team1 and team2 came from the same overall list of teams, I had to first concatenate them together, then label encode them, then replace the team names in the original data set with their new label encoded value. 

# Regression Model
After cleaning up my data, I passed it into a RandomForestRegressor. This model used season, neutral, playoff, team1, team2, elo1, elo2, and elo_prob1 to predict the score of a future game. I chose to use 200 random estimators to start. This gave me roughly 14% accuracy. I then cut down the number of estimators to 100, and retained roughly the same accuracy. When I attempted to cut the number of estimators in half again to 50, my accuracy began to noticibly decline. For this reason, in the future were I to use this model in industry I would use 100 estimators (for this data set) for the most accuracy and efficiency. 
