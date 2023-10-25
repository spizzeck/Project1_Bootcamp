# Project1_Bootcamp
In our project, we are analyzing Medicare Fee For Service Data to see where/who Fee for Service Healthcare providers target, and how they operate.

Background:
"Fee-for-service is a system of health insurance payment in which a doctor or other health care provider is paid a fee for each particular service rendered, essentially rewarding medical providers for volume and quantity of services provided, regardless of the outcome."
-healthinsurance.org
This gives Fee For Service health care providers a bad reputation of cutting corners and not providing adequate care.

Often, it is disproportionately the only option for low income households... or so they say.

We wanted to see how this problem in healthcare is affecting our home state of Virginia. We also wanted to find out if this type of service really targets poorer populations.

In our code, we combined data from FRED and CMS.gov to analyze the relationships between income, population, total FFS payments, and total FFS providers per county over time.
We also want to explore what types of services FFS providers offer to see if we can find any trends.

Data Sources:
Market Saturation & Utilization State-County - Centers for Medicare & Medicaid Services Data (cms.gov)
VA, County - Economic Data Series | FRED | St. Louis Fed (stlouisfed.org)

Question 1: Which Types of FFS Health Services are most used year by year?
For this analysis we retrieved the types of services used for all counties and created a bar charts for the types of services used in 2015, 2016, and 2017-2018 (this is because our dataset stopped at 10/01/2017-9-30-2018, and we wanted to include the last time range).

We found some interesting results, Prevention Health, Independent Diagnostic Testing, and Clinical Health take the top 3 spots for each year.
The top categories are consistent and rarely changes year to year
In 2018 we see a small addition to our data, which is a column for Telemedicine. As we know that.

Independent Diagnostic Testing facilities are consistently the 3rd most popular service with around 90,000-100,000 users per year. According to the Office of the US Inspector General, they are also known for cutting corners and not meeting regulatory standard, since they operate outside the mainstream medical system. This could be indicative of FFS providing inadequate services to these areas


Question 2: Can we find differences in FFS payments across years and counties?

To explore this question, we first created a pie chart showing the total payments for each year. This showed that FFS payments were fairly consistent in 2015-2017, and then they drop significantly in 2018. This could be a sign that FFS services are declining in Virginia. However, since our data abruptly stops in September, more research needs to be done to see why that is.

But for us, this begs the follow-up question:
Which counties had the highest amount of payments? What about when we compare them to income and population? What trends can we see?

To answer these questions, we first created a pie chart breaking down the total payments by county. Immediately we see that Virginia Beach has the largest amount of total payments by far with 28.5% of the total. Next is Henrico with 21.2%, and Loudoun with 13.2%. We can also tell that the data is very spread out, with Bath county taking only 0.5% and Richmond County taking 0.8%.

Next, we created a Bar Chart of the total payments by county in 2017, so we can better see the total differences. Here we can see that Virginia Beach has by far the most payments at $350 million. Interestingly, we can now see how much less total FFS payments Loudoun County has compared to Virginia Beach with about $175 million. This graph also shows vast differences between our counties, with the lowest (Bath county) having less than $100k of FFS payments. What is interesting about Bath county is that it has a low population and a high income per capita. Since both those factors are not appealing for FFS providers, it has below average FFS usage.

To dig deeper, we used bar charts again to visualize the differences in population and income per capita across counties. With the population bar chart, we can see that Virginia Beach and Loudoun Counties have similar populations of around 400,000 and 420,000 respectively. However, the income per capita bar chart shows that Loudoun County has a far higher income per capita than Virginia Beach of $75,000 and $55,000 respectively. This leads of to believe that we are on the right track and income does have a significant difference on FFS healthcare service usage.

The income and population charts also shows that many low income counties are also low population counties. This may skew our data more towards large population centers. At first glance, low population centers also seem to have lower FFS payments.

Question 3: Null hypothesis, T-test, and Linear Regression.

Our hypothesis:
If/Then = IF Income per capita (GDP) of a county is related to the amount of medicare FFS Payments in a given county, THEN as Income per Capita decreases, the number of FFS payments should increase since medicare FFS services target lower income populations.

Null = The Income per capita and the FFS payments will have no correlation between them. 

Alternative = The lower the Income per capita the higher the FFS usage, and the higher the income per capita the lower the FFS usage will be.

To test our hypothesis, we used an independent t-test between income per capita and total payments. We got a p-value of about .007. Thus, we reject the null hypothesis and accept that there is some type of relationship between these factors.

Next, we did linear regression analysis on income per capita and total payments to see if our hypothesis is correct, and the results surprised us. It showed the opposite of what we expected, with a fairly strong positive correlation of 0.40 and a line of 
Y = 3372.22x - 60597753. Meaning for every $1 increase in income per capita, total FFS payments go up by about $3372. 

Income per capita vs Total FFS providers per county y = 0.02x + -534.37
For every $1 increase in GDP per capita, there is a 0.02 increase in the number of FFS healthcare providers. 
For every $1 increase in GDP per capita, there is a whopping $3372 increase in the amount of FFS payments received. This means that FFS providers may have an incentive to choose areas with higher GDP per capita


At first, this did not make sense to us since we saw that between Virginia Beach and Loudoun, income seemed to have a large effect. What we weren’t considering was that even though Loudoun had a very high income, it also had a fairly high amount of FFS payments when compared to poorer counties with less population. 

This means that population also has a large impact on the amount of FFS services and payments in an area which our regression and t-test were not considering. The population difference is such an overpowering factor that it was having a positive correlation effect on the counties regardless of income.

Knowing this, we went back and divided total payments by population, to negate the impacts of population on our analysis. Keeping both variables in terms of per capita, means we are really analyzing the affect of income on ffs payments per person, regardless of whether they live in a large population center or not.  

When we retry our regression analysis for income/capita vs. payments/capita, we get a result much more in line with our hypothesis! It even has a stronger negative correlation of -0.51. It has a regression line of y = -0.01x + 1670.17 meaning that for every $1 increase in income there is a .01 decrease in FFS spending. This is still a significant effect on FFS spending. But again, comparing this with total FFS payments shows just how much of an effect population has in regard to total FFS spending, just not on a per-person basis.

When we retry the independent t-test for income/capita vs. payments/capita we get an even lower p-value of 1.688190672219773e-07. Showing an even more significant result than before.


Conclusion/Further Research Needed

The analysis of total payments showed us that there was a drop in FFS service use in 2018. Analyzing the types of services showed us that independent diagnostic testing is a top service used. The income, population, and FFS payment differences between Loudoun and Virginia Beach led us to believe that income does play a large difference in FFS service use. Our initial Regression Analysis showed us that there is a positive relationship between income per capita and total FFS payments. Which went against our hypothesis. 
However, FFS providers and their payments received may be inherently drawn to larger population centers, as our data shows. When population is considered FFS payments, it gives us a negative correlation, which supports our hypothesis, and we learned how much of an effect population and income have on FFS health service use. We also can say that our data backs up what is talked about by healthcare institutions online, which is that FFS services are disproportionately used by lower income households and may be receiving poor-quality care because of it.
Limitations: 
Since we are working with medicare data, FFS services may also be biased towards older population.
Including more counties would give is more information and more accurate regression analysis.
Also, having access to a demographic breakdown of county populations would give us greater insight into how FFS service disproportionately affects lower income communities
