# California-Standardized-Testing-Analysis-Project

This project aims to understand the prevalence of standardized test taking to California high school students. Some questions I'd like to consider are 
* Which schools have the highest testing rates?
* Do schools where more students take standardized tests also score better on those tests?
* Do different tests (ACT, SAT, potentially AP) have different patterns?
* How did testing prevalence / scores change in California during COVID?

### Background
The ACT and SAT are two of the most widespread standardized college admission tests used in the United States. 
In 2019 more than 2.2 million students took the SAT ([Source](https://reports.collegeboard.org/pdf/2019-total-group-sat-suite-assessments-annual-report.pdf#page=3&zoom=100,-142,731)).
The ACT is ran by the nonprofit organization [ACT](https://www.act.org/content/act/en/about-act.html) of the same name while the SAT is ran by the [College Board](https://www.collegeboard.org/).

While many colleges and universities have previously required prospective applicants to take either the ACT or SAT this is rapidly changing during the era of COVID-19. 
Nevertheless, several top colleges still require or encourage these exams and they are recommended for many students ([Source 1](https://www.cbsnews.com/news/act-and-sat-no-longer-required-college-admissions/), [Source 2](https://supertutortv.com/college/where-sat-is-required-what-colleges-are-and-arent-test-optional-for-the-class-of-2022/)).
As a result the number of high school students taking the SAT dropped from 2.2 million in the class of 2019 to 1.5 million in the class of 2021 ([2019](https://reports.collegeboard.org/pdf/2019-total-group-sat-suite-assessments-annual-report.pdf#page=3&zoom=100,-142,731), [2021](https://reports.collegeboard.org/pdf/2021-total-group-sat-suite-assessments-annual-report.pdf)).

The SAT has 2 sections: Math, Evidence-Based Reading and Writing (ERW). 
The Math and ERW sections are graded on a scale of 200-800.
The total score is the sum of the scores on the Math and ERW sections ([Source](https://collegereadiness.collegeboard.org/sat/scores/understanding-scores/interpreting)). 
Additionally the college board sets benchmark scores designed to assess college readiness ([Source](https://collegereadiness.collegeboard.org/about/scores/benchmarks)).

The ACT has 4 sections: Math, English, Science, and Reading.
Each section is scored from 1-36 with a national average of about 21.
The composite score is the average of the four subject scores ([Source](https://www.princetonreview.com/college-advice/good-act-scores)).

Additionally both the SAT and ACT have a separate essay or writing test that is optional for a student to take with the rest of the exam.

### Datasets Used

For this project we use data on public California high schools published by the California Department of Education. 
On their [website](https://www.cde.ca.gov/ds/sp/ai/) they provide information on all public highschools in California whose students participated in the ACT, SAT, and AP (Advanced Placement) exams from the 2016-17 school year through the 2019-20 school year.
Private high schools and home schooled students are not included in the data set.

For the SAT, the data includes the number of students at the school, the number of students who took the SAT and the percentage of students meeting college readiness benchmarks.
For the ACT, the data includes similar information about the school, the number of students who took the ACT, the average on each section, and the percentage of students scoring at or above 21. 
Full data dictionaries are available on the CDE website at https://www.cde.ca.gov/ds/sp/ai/.
The data does not include the writing section for either exam.

For both datasets the statistics are also rolled up to the district, county, and state level.

### Data dictionary
All features are based off of the ACT datasets published by the CDE.

|Feature|Type|Description|
|---|---|---|
|**CDS**|*integer*|The code identifying the school, district, or county. Consists of the concatentation of the County, District, and school codes.| 
|**RType**|*string*|The type of entity. 'S' stands for school, 'D' for district, 'C' for county, and 'X' for state|
|**SName**|*string*|The name of the school|
|**DName**|*string*|The name of the district|
|**CName**|*string*|The name of the county|
|**Enroll12**|*int*|The number of enrolled 12th grade students|
|**NumTstTakr**|*int*|The number of 12th graders who have taken the ACT before graduating high school|
|**NumGE21**|*int*|Number of students who scored at least 21 on their ACT composite score|
|**PctGE21**|*int*|Percent of students who scored at least 21 on their ACT composite score|
|**AvgScrComp**|*float*|Approximate average composite score of all students|
|**ACT_taken_pct**|*float*|Percentage of students who took the ACT|
|**SAT_benchmark_pct**|*float*|Percentage of students meeting the Math and ERW benchmarks on the SAT|
|**SAT_taken_pct**|*float*|Percentage of students who took the SAT|

### Conclusions
* SAT and ACT show similar patterns.
* Full school data has a negative association between participation and success.
* Removing schools with very high test rates reverses association
    * Many such schools that have high testing rates but low average scores are charter schools.
* Testing scores and participation is correlated with geography.
* SAT and ACT scores are correlated across schools but participation is not.