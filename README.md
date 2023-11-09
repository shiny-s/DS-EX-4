# Ex-04-Multivariate-Analysis

## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
## OUTPUT:
![1](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/8ec862fe-5294-4983-9337-9efcb83a6fb8)
![2](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/34ff0e52-bb17-4a2d-8cb5-37e2fbbeb7e9)
![3](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/c2e3bfa0-4703-4e74-9b1a-f61dfe0c23ee)
![4](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/8c1c8beb-b35c-442a-ad45-b2d53756afe0)
![5](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/8bdf668f-7cec-481e-955d-24c811245508)
![6](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/66bcaf91-a38c-4e29-a53d-ee8623c4ea86)
![7](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/c41abe9d-6c5f-43b7-a108-83a5383086ad)
![8](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/91b39d2f-3508-4823-880d-714c6ef0997a)
![9](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/61f9b04e-bf5c-4ffc-9e80-88368a657834)
![10](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/cf7cc912-404f-4963-aa09-4003586c6fbc)
![11](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/c5b7876d-6944-4bcc-b428-8bbf1737b6a7)
![12](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/66664db2-8831-441c-97c8-9d22b76d6f7b)
![13](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/61c6396f-fd35-42ee-872d-15ebc02180a9)
![14](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/fe3c0413-8cac-48c3-885d-28f47e09ee2c)
![15](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/06bae3c1-d023-40d3-84f9-52e670f22a77)
![16](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/ccd81af5-0233-4b9f-b6c2-aa2b60834061)
![17](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/16f4d9dd-c67c-4238-9c28-38a7a6f0d8a0)
![18](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/4d797c90-43c7-411a-b1c5-6d1f72d10822)
![19](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/09b8b099-02d4-4c1b-aaf5-ed5e56ccd6b4)
![20](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/468924be-bc80-4a22-b251-8e9e97c0b98f)
![21](https://github.com/Krupa-Varsha-P/DS-EX-4/assets/100466625/5826ebfa-9b41-4cdc-a8f4-895c26519352)






## RESULT:
Thus the program to perform EDA on the given data set is successfully executed.
