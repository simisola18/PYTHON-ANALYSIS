# PYTHON-ANALYSIS
AN ANALYSIS OF ROAD ACCIDENTS AND VEHICLES IN THE UNITED KINGDOM FROM 2018 - 2020
# 1.0	ABSTRACT
The issue of road accidents is a major societal concern in every country. A study of UK road traffic accidents and vehicle data for the period 2018-2020 has been conducted for this report. It explores various variables (weather conditions, light conditions, accident severity, road type, urban or rural area, age band of driver, and sex of driver) and their outcomes concentrating majorly on all regions of the United Kingdom.
Data analysis for this study was carried out using Apache Spark and the SparkSQL Library to analyze the data set. The Department of Transportation Accidents, Casualties, and Vehicles in the United Kingdom provided the data used for this analysis. The results of this analysis show that the combination of different factors influences the number of road accidents.
# 2.0 INTRODUCING THE DATA
2.1 SOURCE
In this report, information and data from ‘data.gov.uk’ were aggregated through the Department of Transportation Accidents, Casualties, and Vehicles, a government website that provides information and data about accidents and vehicles in England, Wales, and Northern Ireland.
The Data used in this report has been preloaded in the Hadoop distributed file system and a reference was made to the path for import. Road safety data on accidents and vehicles for the period of January 2018 to December 2020 are included in the dataset. The dataset evaluated has 19 columns/variables with 610165 records.
The data sets are available freely and the public can access them for free. The data sets are collected independently by each police force to an agreed specification which is reviewed periodically to ensure information collected by the police is relevant to the emerging road safety needs and minimizes the burden on the police.
2.2      DATA FORMAT
The whole data was published as a comma-delimited file uploaded every year for the Road Safety Data – Accidents and Road Safety Data – Vehicle files. The file had most of the variable values represented with numbers which were interpreted using the Road Safety Open Dataset Data Guide.
2.3       SCOPE, RANGE, AND ACCURACY
This data scope was limited to details about the accident and vehicle information and not much focus on the Casualties involved using the Apache Spark SQL written in Python Programming Language. A large part of the data had a lot of unknown values and missing data ranges.

# 3.0	THE METHODOLOGY
The raw data used in this analysis is a CSV (Comma-Separated Values) file which was uploaded to the HDFS. The analysis was conducted using Apache spark(pyspark), a consolidated analytics engine that provides high-level SQL tools for large-scale data processing. The library used was Spark SQL. Matplotlib and Pixie dust libraries were used to carry out the visualizations.
The Jupyter notebook was used to upload the three-year files of accident and vehicle data into the local directory, which was then uploaded into the Hadoop Distributed File System (HDFS) using the Web Console. 
The data preparation and cleansing are explained below.
3.1	SETTING THE CONFIGURATION AND DATA FRAME CREATION
Using pyspark in jupyter the configuration was set and two DataFrames “accidents” and “vehicle” were created directly from the dataset stored in the HDFS through the SQL context file. 
![image](https://github.com/user-attachments/assets/ff44a816-db4e-4b66-b0cc-fd1689a987f0)
![image](https://github.com/user-attachments/assets/21662c50-2062-4b56-88cf-414042b24314)
![image](https://github.com/user-attachments/assets/94a3ff7a-28a1-4a30-b351-d5e27e115bf4)
3.1.0 Code 1: Configuration and Data frame creation for accident and vehicle data
An action ‘printSchema’ was also run on the two data frames created to confirm the data structure. The two data frames created had to be joined enabled by the accident index to analyze the dataset correctly. After the dataset had been joined a print schema was run on the new data frame.
 ![image](https://github.com/user-attachments/assets/00143d6a-8969-40f9-9ac3-9acbcd10aed7)
3.1.1 Code 2: New data frame creation by combining the vehicle and accident data frame

3.2	DATA PREPARATION AND CLEANSING
The combined data frame had a lot of variables that would not be concentrated on in this analysis hence the need to drop them out of the analysis. After dropping the variables, A print schema was done to determine the variables left which totalled 19 variables.
 ![image](https://github.com/user-attachments/assets/4ebbbad9-586e-474e-8cf2-7082b8822f2e)
3.2.0 Code 3: Dropping of some variables
A printSchema was done on the new data frame created to see the results of dropping some variables
![image](https://github.com/user-attachments/assets/8fdb35f2-f174-4aa0-8e37-f6be34aecaa0)
3.2.1 Code 4: Running a print schema
The CSV data uploaded had its values for the variables in numbers, this had to be renamed from number to meaningful words to interpret the data accurately.
![image](https://github.com/user-attachments/assets/aacdb150-fe02-42d3-8bda-f43967ca9886)
3.2.2 Code 5: Renaming values to meaningful words
3.3	DATA EXPLORATION
Running through the data with the code below, the total records in Accident, Vehicle file count is 610,165 records in 19 columns of data.
Missing values in the dataset Columns were checked for and it came out with a zero value for each column. 
![image](https://github.com/user-attachments/assets/976cf0e9-c649-42e2-8e88-9eb9f9769be5)
3.3.0 Code 6: Data Exploration to know the count value of the dataset

# 4.0	DATA ANALYSIS
By grouping data based on different variables, we can identify trends and patterns. We will compare the counts by month, and by year, to different variables (sex, age, speed limits, accident severity, etc.) in the last few years of 2018-2020.
4.1 GROUPING BY DAYS OF THE WEEK
As a first step, we ordered by count to see which day of the week had the highest number of casualties whenever an accident took place in the UK region with Sunday turning out to be the highest count of casualties in a week and Saturday following closely with the number 61437 and 59051 respectively for the period of the three years analyzed according to the top 20 data row. 
Weekends are also more likely to result in car accidents. This could be due to lengthier travel times for weekend vacations, intoxicated driving, or simply the bigger number of cars on the road during the weekend. Another analysis below shows that Sunday followed by Saturday were the days that had the highest number of cars on the road.
![image](https://github.com/user-attachments/assets/f6f86154-30e3-42ef-96b7-de76051e7f8f)
4.1.0 Code 7: Casualties per day of week
![image](https://github.com/user-attachments/assets/1afa0519-7759-4a52-a1a0-a6e2bd33a986)
4.1.1 Code 8: Vehicles on the road per day of the week

4.2	Grouping by Speed Limit, Accident Severity, Accident Year, and Accident Per Month
The speed limit range of drivers according to the data given was between 30 – 70. According to a chart that shows the speed limit versus the number of casualties, it showed that the highest number of casualties were from an accident within the speed limit of 30(appendix). This indicates that drivers in towns, cities, and suburbs should also drive as carefully as those on motorways.
![image](https://github.com/user-attachments/assets/e0f88bc1-ad17-4384-8de2-bb92259c50ac)
4.2.0 Code 9: Speed limit list
Accident Severity describes the effects of the accidents on the casualty, whether the accident is Fatal, Serious, or Slight. The code below shows that for the period of 2018-2020, most accident casualties were Slight (includes whiplash, sprains and minor lacerations) with a percentage of 80.3% followed by Serious (detention in hospital, which includes paralysis, fractures and severe lacerations) with a percentage of 18.3%, and Fatal (a collision resulting in a death) with a percentage of 1.4%.
![image](https://github.com/user-attachments/assets/ae56a99b-5470-4ab4-8b30-b92d93f7c079)
4.2.1 Code 10: Accident Severity Vs Count
The most fatal accidents happened at a speed limit of 60 while the speed limit of 30 had the most records for slight accidents.
![image](https://github.com/user-attachments/assets/6535ebc2-f151-4c71-950d-b80316aa389c)
Accident Year shows the total number of accidents count per year with the year 2018 having the highest and decreasing as the years progresses. Accident Per Month shows that the cumulative month of September across the years evaluated has the highest number of accidents followed by July and October with April being the Lowest.
![image](https://github.com/user-attachments/assets/91b7f810-a805-47e7-bf78-f5a93190ed70)
4.2.2 Code 11: Accident year and counts
![image](https://github.com/user-attachments/assets/710638a3-73b9-40eb-9528-77a4f2df2078)
4.2.3 Code 12: Accident Months and counts
4.3	Sex of the driver and Age group of the driver
The sex of the population in the United Kingdom is being led by Females The population of the United Kingdom was 67 million in 2020, with 33.94 million females and 33.15 million males. This is rather amazing because of the significant ratio of male to female drivers involved in the accidents. The counts double for Male as the value for drivers involved in accidents were more than 2x the population of the Females.
![image](https://github.com/user-attachments/assets/c0f09881-90d9-4289-8183-a0bcaed5319d)
4.3.0 Code 13: Sex of driver.
Further Analysis of the Sex of the driver against the Age group of the driver according to the Matplotlib library using Pandas, shows that the age group of 26- 35 for both males and females had the highest number of drivers that were involved in an accident.
![image](https://github.com/user-attachments/assets/fb81ad02-e4f7-4ed0-b64c-aabc595bda56)
4.3.1 Code 14: Sex of driver Vs Age band of driver
4.4	Some Visualizations and their Observations
1. The number of casualties based on the aggregate of the whole data shows Thursday with a percentage of 21% having the highest number of casualties in an accident
![image](https://github.com/user-attachments/assets/3de92903-8c2c-4678-b9b7-1566f2652f4c)
4.4.0 Code Visualization 15: Number of Casualties Vs Day of the week
2. Area is another variable used in the examination of this data where number of casualties is measured against where the accident occurred based on whether the area is a Rural or an Urban Area. Statistics show us that the majority of the accidents with casualties happened in the Urban areas of the country which are the towns and cities.
![image](https://github.com/user-attachments/assets/0daada6f-6cb4-40e5-9c2b-47f2eee2285b)
4.4.1 Code Visualization 16: Number of Casualties Vs Area
Another angle to look at in the analysis of the impact of the area in this data is when the number of casualties is categorized against the area and clustered by the severity of the accident that took place, it was noted that the highest severity of accidents for the two areas was Slight followed by serious and fatal being the least in both cases. It was worthy to note that the Fatal severity of accidents in the rural area was more than that in the urban areas. It could be said that the longer travel distances and travel hours could result in a higher crash risk resulting from increased exposure on the road thereby resulting in high Fatal severity in rural areas.
Also, the conditions of some rural roads such as muddy roads, etc. could prevent some drivers from driving at a fast pace in the rural area to be unable to react in time to hazards or people to prevent a crash. In addition, some drivers when driving in rural areas do not see the need to wear a seat belt which sometimes results in accidents.
![image](https://github.com/user-attachments/assets/57c37772-7461-493f-94f2-e3fdb4a28b4f)
4.4.2 Code Visualization 17: Number of Casualties Vs Area clustered by accident severity
3. The journey purpose of the driver can give more reason or insight as to why the accident happened and what can be done next time to prevent such. According to the data provided on the journey purpose of the drivers a majority percentage which is 60% is Unknown followed by 14% saying they were on their way to work and 10% saying they were commuting to or from work while less than 2% were taking kids to school or picking them up.
One can say 24% of the casualties were on the way to or from work and drivers and victims should endeavour to be extra careful when commuting to work.
![image](https://github.com/user-attachments/assets/795cc85f-2387-42bb-b545-3bb3ded5d763)
4.4.3 Code Visualization 18: Number of Casualties Vs Journey Purpose
4. Weather Conditions also cause some accidents to occur, it was a variable in the dataset analysed. There were so many categories of weather be it raining, snowing, fog or mist, or Fine weather. According to the analyses using Pixie dust for the visualization, the weather condition that produced the most casualty was the Fine with no high winds weather condition followed by raining with no high winds weather. The other weather conditions produced little or no effects on the cause of accidents.
![image](https://github.com/user-attachments/assets/c23f8926-48b1-4889-b1ce-cf70c230d7e6)
4.4.4 Code Visualization 19: Number of Casualties Vs Weather Conditions
5.  Light Conditions are said to be an important factor in a driving scene, If the roads are well lit or not, natural daylight, etc. The analysis doesn’t explain the correlation between light conditions and accidents that happen if it is a causal factor as the majority of the incidences took place in broad Daylight followed by Darkness where lights are lit. A few accidents took place in areas where it was dark with no lighting also.
Another data exploration uses light conditions to determine if light conditions affect the number of accidents/casualties in an area. In the graph below there are a lot of dark areas with no lighting that is present in the rural areas as compared to the urban area which had very few dark areas with no lighting. These dark areas with no lighting also contributed to the high number of accidents and casualties in the rural areas.
![image](https://github.com/user-attachments/assets/ba38fea6-23da-4dbd-ac20-de71e65ad58f)
4.4.5 Code Visualization 20: Days of the week Vs No of vehicles with light conditions as a cluster range
![image](https://github.com/user-attachments/assets/97fea4ae-7670-4745-ba86-908bf82b63ba)
4.4.6 Code Visualization 21: Number of Casualties Vs Area with light conditions as a cluster range

# 4.5     SUMMARY OF THE OBSERVATIONS
Through the use of SparkSql library, Matplotlib and Pixie Dust, a series of queries were run in the data which generated a lot of insightful information.
1.	Majority of the accidents happened in the year 2018 in urban areas on a single carriageway.
2.	The severity of the accidents for the 3 years combined was Slight (includes whiplash, sprains and minor lacerations) with a percentage of 80.3% with Fatal (a collision resulting in death) being the least with a percentage of 1.4%.
3.	Most accidents happened in Fine no high wind conditions during daylight.
4.	Male drivers had the majority population in the age range of 26- 35 involved in the accidents.
5.	The highest number of accidents happened at the end of summer periods September and October.
6.	Most fatal accidents happened at a speed limit of 60 while the speed limit of 30 had the most records for slight accidents which was the majority.
7.	The covid pandemic in the year 2020 could be a reason for the decrease in accidents that occurred as a result of the Lockdown.

# 5.0	CONCLUSIONS, LIMITATIONS AND RECOMMENDATIONS
5.1	CONCLUSIONS
The bulk of road accidents is caused by shortcomings in human behaviour. As a result, it's crucial that it's addressed. In many traffic accidents, personal factors play a crucial influence. The Department of Transportation Accidents, Casualties, and Vehicles must invest in infrastructure and educate drivers about the importance of physical and mental health monitoring to address this situation. The key findings and conclusion from the course of this analysis are;
•	It is assumed that the winter period would be where most accidents happen due to the weather type, but results show that the summer period in fine weather and bright daylight was where most accidents took place.
•	Accidents were majorly domiciled in the Urban towns of the country two times as much as the rural areas.
•	Another finding was that the speed limit at which most accidents happened was 30mph which was shocking as one would expect a speed limit of 80mph and above. One could guess that most users are either distracted, stressed out or probably not using their seatbelts.
5.2	LIMITATIONS
The data available in the data.gov.uk for review was limited as a lot of the data values were either Unknown, had missing values or negative values etc. The variables to be analyzed had lots of missing values and the data was not interpreted adequately, it would save lots of stress having to manually interpret each data value. The covid period covered was only for the year 2020, this may or may not have any impact on the results gotten for the year 2020.

5.3	RECOMMENDATIONS
•	The quality of the roads can always be improved on and the country’s strategy on-road performance and safety can always be improved on also, enforcing speed limits most especially in the rural areas.
•	When it comes to road safety, daylight is crucial and it should be monitored properly using low beam lights during the day helps to limit the number of accidents.
•	Individual risk factors, administered medicines, sleepiness, lack of experience, drunkenness, hearing and visual impairment, usage of mobile phones, distributional attention, health state, and more are all elements that influence a driver's behaviour, this should all be looked out for
•	The environment should be assessed, which includes all environmental factors, road conditions, and other associated elements such as adequate street lighting in all areas both rural and urban.

# 6.0	REFERENCES
Department of Transportation Accidents, Casualties and Vehicles
https://data.gov.uk/dataset/road-accidents-safety-data
https://gov.uk/roads-and-travel/road-safety/crash-and-casualty-data
www.swindon24.co.uk
https://www.statista.com/statistics/281240/population-of-the-united-kingdom-uk-by-gender/
https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data
www.kent.gov.uk

Full Paper write up is in the pdf file attached




