# Project1-Group3: Less moneyball? The influence of the Competitive Balance Tax on Major League   Baseball from 1985 to 2015

UofM Bootcamp Project 1 by Group 3 (baseball data)

## Contributors
Clayton Knight,
Molly Ingram,
Wanderson Oliveria


## Project Overview

In 1997, Major League Baseball (MLB) introduced the Competitive Balance Tax (CBT) as a measure to deter teams from exploiting a spending advantage without consequences. The goal was to level the playing field and prevent teams from gaining an unfair advantage in acquiring higher-quality players by overspending. This project assess how the CBT may have impacted team behavior and performance.  

We use a baseball dataset compiled by Sean Lahman and shared via kaggle (see link in Credits). We limit our sample to the MLB seasons corresponding to calender years 1985 to 2015. During that time period, new teams (franchises) joined the league so we restrict our sample to the 26 teams present in all years of the study period. The resulting dataset contains 806 observations uniquely identified by year-team pair.  We supplement this data with information on the tax thresholds set by the MLB association.

The MLB implemented the competitive balance tax in 1997 to reduce anti-competitive behavior in the league.The first agreement stated that the top five salary teams in each year would pay a 34% fine on each dollar a team spent beyond halfway between the salaries of the fifth and sixth teams.
For example, if the fifth-highest salary team had a payroll of $100 million and the sixth-highest salary team had a payroll of $98 million, the top five teams would pay 34% on each dollar they spent over $99 million.
The MLB luxury tax was eliminated from 2000 to 2002, and MLB brought it back with a new change to the system.

The system today is based on the 2002 collective bargaining agreement. Instead of putting a level between the 5th and 6th teams, they decided to set a threshold that a team could not pass without a fee. Taxes are factored on each dollar going over the threshold.
2003 - 2011, first-time offenders would pay a fee of 17.5% of excess payrolls (later increased to 22.5%), second-time offenders would pay 30%, and third-time offenders would pay 40%.
2012 - 2015, after seeing teams go over more than three times, the agreement added a 50% taxation level when teams went over the limit four or more times. (These offenses must be in consecutive years for these percentages. If a team falls below the threshold one year the penalty resets the next year to the "first offense")  

### Repository Organization
Baseball Dataset contains the Baseball Databank download from kaggle.  
Output contains all generated .csv files and figures.  
Presentations contains a pdf of our presentation slides.  
Salary Thresholds contains the supplemental data on tax thresholds set for the 2003-2015 season and background information on how the taxes were implemented in each year.  
data_cleaning_and_analysis.ipynb contains all code needed to generate the data and analysis for this project.  
Grading rubrik is the project's requirements for reference.


## Project Analysis
To better understand how the CBT impacted MLB teams, we break the topic into three questions: 1) Did the teams' spending on player salaries change, 2) Did more spent on players salaries led to more wins, and 3) Did was player talent better distributed.  An analysis of each question follows.


### Question 1: Did implementation of penalty system eventually discipline the teams? (Led by Clayton)

Despite occasional fluctuations in the gap between teams with the highest and lowest salaries following the implementation of the CBT, the sustained increase in average salaries suggests that teams have not collectively exhibited greater fiscal discipline to circumvent CBT payments.  
<img src="Output\Disparity Fig.png"
 alt="Disparity"
style="display: inline-block; margin: 0 auto; max-width: 300px">

<img src="Output\Avg Regression Fig.png"
 alt="Avg Regression"
style="display: inline-block; margin: 0 auto; max-width: 300px">

### Question 2: What was the most dominant team during the 30-year period and its correlation to salary? (Led by Wanderson)
After analyzing the data, was showed that the New York Yankees (NYY) won most games during 30 years, hence being the most dominant team for a 30 years period. Potentially due to ownership and good management, by spending money on the team in order to win games.Overall, from 1985 to 2015 Teams have showed an exponential growth in salary, meaning teams are investing more in their players, however, after analyzing the data, concluded that there is no correlation between wins and salary spent per each team. One Example is (ANA), which won the most games in 2014 and had a total team salary spent of approx. $121M, that same year, (SFG) won 88 games and total spent of approx.163M.
(NYY), the most dominant team, had spent the most and won the most games in 2009, however, the following year, 2010, it didn’t win the most games and still was the team that spent the most, approx. $206M. Hence, there is no correlation between wins and salary pear year for the most dominant team.

<img src="Output\team_avg_wins.png"
style="display: inline-block; margin: 0 auto; max-width: 300px">

<img src="Output\wins vs salary.png"
style="display: inline-block; margin: 0 auto; max-width: 300px">



### Question 3: Did the CBT generate a more equitable distribution of talent? (Led by Molly)
To evaluate this question, we first needed to define a measure to use for team performance (or talent). The team performance statistics available for all year in our dataset are runs, at bats, hits, doubles, triples, homeruns, walks, strikeouts, stolen bases, caught stealing, runs averaged, earned runs, earned runs average, complete games, shutouts, saves, hits allowed, homeruns allowed, walks allowed, strikeouts allowed, errors, double plays, and fielding percentage.  We did not use batting or fielding performance factors because we wanted to capture overall team performance, not home versus away performance differences.  The following figure displays the correlations between the performance statistic, wins, and team salaries.  
<img src="Output\performance correlations.png"
style="display: inline-block; margin: 0 auto; max-width: 300px">

The above figure shows there is no dominate relationship between any of the performance statistics and wins, so we needed a way to combine the information captured in the performance statistics into one outcome variable. There are many methods used for dimension reductioned but we use a random forest regressor approach because it's nonparametric and easy to implement. The random forest model uses the team performance statistics to predict a teams number of wins per season. The model was trained on half of the data and tested on the other half and achieved an accuracy of around 95%. The performance indicator we use is the model's predicted wins (based off of performance statistics) for each year-team observation. The figure below is the relationship between the predicated and actual wins.  
<img src="Output\perdicted vs actual.png"
style="display: inline-block; margin: 0 auto; max-width: 300px">  

With the performance indicator, predicted wins, we compare the performance distributions before and after the introduction of the CBT. The distributions are shown in the figure below. Visually the post-CBT distribution appear tighter and shifted to the right. F-test and T-tests confirm that both of these differences are statistically signifant.  

<img src="Output\perf distributions.png"
style="display: inline-block; margin: 0 auto; max-width: 300px">  


### Conclusion
Our analysis suggests that the CBT did not change team spending behavior. The gaps in salaries between the highest and lowest spending teams grows dramaticly post-CBT. We find than player salaries do not predict how a team will fair over a season in terms of wins and losses.  But despite lack of relationship between salaries and wins, some teams continue spending a lot to bring in players. This may be better explained by a profit objective, as opposed to a performance objective. Big name players may generate greater benefits the team more through TV contracts, game attendence, and merchandise sales. Despite not changing salary spending, variation in team performance is not as large in the years after the CBT, which suggests that talent may be better distributed among teams.
Team performance is (at least a little bit) more balanced post CBT  

Our focus was on team data, thus we did not account for player level characteristics. Considering player charateristics may better illuminate the link between salaries and performance as well as talent distribution among the league but it was beyond the scope of our current analysis. It is also important to note that we have not controlled for any other league changes during this time period (expansions, union negotiations/strikes, draft changes, revenue sharing, etc.). We were also not able to controll for characteristics of teams, managers, owners, and other features that may impact hiring, salary, and performance outcomes.  


## Thanks/Credits
Thanks to Vishal Bhatnagar, our original fourth group member, for his input. Thanks to Sam Espe, Hunter Hollis, and Randy Sendek for their troubleshooting support.  All errors are our own.

Data was retrieved from <https://www.kaggle.com/datasets/open-source-sports/baseball-databank>

Random Forest code was adapted from <https://towardsdatascience.com/random-forest-in-python-24d0893d51c0>