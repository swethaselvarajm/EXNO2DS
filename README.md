# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/fb53c826-c322-4048-aa0e-5be94f93b46b)

```
df.info()
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/556fcaa2-66be-43cd-be60-4c39ab0bebb8)

```
df.set_index("PassengerId",inplace =True)
df.shape
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/3e4e3dba-4e45-40e0-a9db-711c6d58aca1)

```
df.nunique()
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/94d5229b-21d2-497d-a85c-863ffd1a787f)

```
df["Survived"].value_counts()
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/28af9088-03cd-4840-8055-70642d83323c)

```
per=(df['Survived'].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/a0a3f07d-8110-46b3-ad3f-3a4a54ea4e22)

```
sns.countplot(data=df,x="Survived")
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/e2a87a26-8915-4ef3-8c1d-8b5d89a34560)

```
fig, ax1 = plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x= 'Survived', data=df)
graph.set_xticklabels (graph.get_xticklabels (), rotation=90)
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2., height + 0.1, height,ha="center")
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/bb472590-a60b-4c21-a3b6-0ce1e5f3ad5c)

```
df.Pclass.unique()
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/e17da48a-01de-4931-a084-6f5c5e46774a)

```
df.rename(columns = {'Sex':"Gender"},inplace=True)
df
```

```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/8aeef7e3-f7e7-40c6-bc93-bbf55d87de33)

```
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/aaabd4a3-fbac-45ff-a06c-f64429f85c05)

```
fig, ax1 = plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=df,x="Survived", hue="Pclass", palette="rainbow")
graph.set_xticklabels (graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height+ 20.8, height,ha="left")
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/df255f97-6f55-4058-b682-c78badb02382)

```
df.boxplot(column="Age",by="Survived")
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/30150408-f147-4bbb-bc8f-27a83892036f)

```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/0b80db12-3099-4383-823d-8d7b5ec5b86d)

```
sns.jointplot(x="Age",y="Fare",data=df)
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/07541157-1db3-44a8-828d-454e52439238)

```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue="Gender",data=df)
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/306e6aec-811f-4e27-b8ec-3cd000da0bac)

```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/a16384e3-ffbe-4201-8a68-dd9a4cc77e4b)

```
g= sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass", kind = "count", legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax =g.facet_axis(0,0)
for p in ax.patches:
ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/9b8372e2-e6d8-43e6-9ed1-9c8770e02cbd)

```
corr=df.corr()
sns.heatmap(corr,annot=True)
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/5ed76665-d728-42ff-8ea4-4f5636b0cb02)

```
sns.pairplot(df)
```
![image](https://github.com/swethaselvarajm/EXNO2DS/assets/119525603/31bbc5fd-c168-430b-aba0-f8b028d21c45)

```

# RESULT
Thus, the outputs verifies that the data set has been applied the EDA process and methods.
