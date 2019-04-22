# team1
Measuring eICU data quality: an open and standardized approach
Data Quality. Tarragona Datathon, November 11 &amp; 12, 2018,

#Objective:
Our challenge was to create an open, standard and general way to examine the quality of data from all variables used in the eICU database (2).

#Introduction:
The eICU database contains data on more than 200,000 ICU patients from multiple hospitals across the USA. Due to its size, geographical distribution, and diversity, these data are widely heterogeneous. As with any large dataset, it is important to understand the structure, content, and quality of the data. Descriptions within the eICU-Collaborative Research Database provided a high-level overview of each data table but these details lacked information that could inform study design and feasibility. There are 31 tables with a combined 397 variables.
Some tables have more than 7 GB of data. Many variables were assigned data types that were not congruent with the description and name of the variable. For example, the variable predictedHospitalMortality was listed as data type “varchar” in the documentation but it was really an integer (int). More importantly we were not able to determine what hypotheses would be appropriate for these data. For example, it would be important to know how many patients had entries into the carePlanEOL table to determine feasibility of conducting a study related to end-of-life discussions.
Although there are many approaches that try to measure the same issue, most of them are really specific for one kind of variables, for unique tables, or are commercial products. We took the Data Quality Dimensions (2) as our base model. Here we have documented all R code used to face our challenge.

#Methods:
We have tested several R packages and have choosen the Data Quality diagnosis (3) to test each variable inside a table. Based on the content in each table we applied different code to adjust for numeric versus categorical variables. Then we have devolped a function to assess missing and outliers for each variable on each eICU table. We made a loop in R for &quot;data hygiene&quot;: cleaning the data in relation to the lost values after visual analysis of the data (many registers with blank values). In this sense we substitute the blank records with &quot;NA&quot; values. We used the R package &quot;dlookr&quot; (2) as our base line to write a new R code to assess Data Quality on eICU database.

#Results:
The total number of patients in eICU database was 200,859. Our R function showed these outputs for each table:
 Number of cases: Total number of records in each table.
 Missing Values (%): Percentage of values that have missing values.
 Irregular Values (%): Percentage of global outliers for the whole table .
 Data Case ratio: Relationship between the total numbers of records stored for each case.
 Overall Cases (%): The number of cases on each table related to total number of cases in the whole database.
 Outliers mean : Arithmetic Average of outliers.
There is an additional table showing an outlier ratio, that is the percentage of outliers for each variable contained in each table in the eICU database.

#Conclusions:
The Descriptive Data Quality Assessment (ddQA) proved to be a feasible approach to analyze eICU Data Quality. We believe it can be extended to other databases. One of the limitations of this approach was the lack of a well documented database dictionary. This made it difficult to fully understand the meaning of each field and table and which fields accept empty values. Another issue was the lack of time and computing power to advance in further analyses. For healthcare databases, always a clinical point of view should be applied to the results of these assessment approach, because no decision can be made without a solid clinical data comprehension. This work and common effort could be a starting point to create an International Critical Data Index (ICDI). A more thorough description of the variables commonly found in the tables, documented in a standard way, would support better and wider big data, machine learning and a collaborative investigation framework. This could also improve potential interoperability between other databases. 

#Team 1 Members: 
Teresa Rincon, tarincon1@gmail.com, Boston, USA. Juan
Alfonso Soler, jsolerbarnes@gmail.com, Murcia, ESP. 
Josep Trenado jtrenado@mutuaterrassa.es, Terrassa, ESP. 
Ariel Leonardo Fernandez hardineros@hardineros.com, Buenos Aires, Argentina

#References:
1. Goldberger AL, Amaral LAN, Glass L, Hausdorff JM, Ivanov PCh, Mark RG, Mietus JE, Moody GB, Peng C-K, Stanley HE. PhysioBank, PhysioToolkit, and PhysioNet: Components of a New Research Resource for Complex Physiologic Signals. Circulation 101(23):e215-e220 [Circulation Electronic Pages; http://circ.ahajournals.org/content/101/23/e215.full]; 2000 (June 13).
2. IBM. Data quality dimensions. IBM. Retrieved November 11, 2018, from: https://www.ibm.com/support/knowledgecenter/en/SSZJPZ_11.5.0/com.ibm.swg.im.iis.ia.product.doc/topics/r_quality_indicators.html
3. Choonghyun Ryu. Data quality diagnosis. Retrieved November 11, 2018, from: https://cran.r-project.org/web/packages/dlookr/vignettes/diagonosis.html 
