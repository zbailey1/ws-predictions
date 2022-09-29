# Notebooks

**Baseball Predictions** notebook contains a few databases unrelated to the world series predictions. I am using it to teach myself how to make nicer looking plots and can be ignored.

**WS Predictions** notebook is where we attempt to predict, given a playoff teams regular season stats, if it will win the WS that year. This is a Work-in-progress. 

## Some background on World Series Predictions:
1. **Data**: All MLB teams end-of-season general stats e.g. Year (e.g. the NYY in 2010 is distinct from NYY in 2011) Batting Average, Runs Scored, Wins, ballpark attendance, and, of course, Booleans detailing whether they made the Wild Card, Won their Division (either of these two indicate they made the playoffs that year), and whether they won the World series. We filter out teams before 1970 since not all stats were recorded in 1969, and 1969 is the first year in which there was a playoff round before the WS.
2. **Goal**: Given the features listed above, and all the teams who missed the playoffs removed, try to predict who won the world series **W** and who lost, **L**.
  - A random guess "Yes" in 1970 would give you a 25% chance of being correct, since the playoffs back then consisted of only 4 teams. 
  - After the playoff reformation in 1994, there were 8 teams who made the playoffs, and after 2012 two more teams were added. (This year, the MLB is starting a 12-team playoff, so who knows maybe all 30 teams will be in it by 2030). 
  - Combining all playoff teams starting in 1970 thru 2021, about 15% of them have won the world series, so that is the current benchmark. 
  - We want to have better precision (The probability that a "W" prediction belongs to a winning team) than guessing all "W" (15%) while having reasonable recall (probability that a winning team is correctly precited as "W").
3. **Some Considerations**
  - There have only been 52 WS since 1970, 7 won by NYY (Yankees) and a few other teams with 3 or 4. If one carefully guessed NYY or one of these other teams if NYY is not in it that year, one may have a higher precision or recall than random guess.
  - Other heuristic guessing schemes that I have not thought of yet *to-do*
4. **Partial Results**
  - Split the data into train (67%) and test (33%) sets, stratified so that each set has the same distribution of winners and losers (~15% W).
  - Linear methods and tree methods (logistic regression, SVM, Random Forest) perform poorly, classifying every test team as a loser. 
  - KNN (n=1) produced the best results, classified 4 of the 17 (23.5%) winning teams in the test set correctly, after reducing the number of feature vectors. KNN (n=5) produced similar results including all feature vectors. The precision was 4/18 or 22%, that is 18 were labeled "W" but only 4 of them were actually winners. THis is slightly better than a random guess.

## To-do
Get more data
  
