# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
 1.Import pandas and matplotlib.pyplot
 
 2.Read the dataset and transform it
 
 3.Import KMeans and fit the data in the model
 
 4.Plot the Cluster graph

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: s.rohith kumar
RegisterNumber: 24004371 
*/
```
import pandas as pd

import matplotlib.pyplot as plt

data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans

wcss = [] #Within-Cluster Sum of Square

#It is the sum of squared distance between each point & the centroid in a cluster.

for i in range(1,11):

kmeans = KMeans(n_clusters = i,init = "k-means++")

kmeans.fit(data.iloc[:,3:])

wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)

plt.xlabel("No. of Clusters")

plt.ylabel("wcss")

plt.title("Elbow Method")

km = KMeans(n_clusters = 5)

km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])

y_pred

data["cluster"] = y_pred

df0 = data[data["cluster"]==0]

df1 = data[data["cluster"]==1]

df2 = data[data["cluster"]==2]

df3 = data[data["cluster"]==3]

df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="Cluster 0")

plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="Cluster 1")

plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="Cluster 2")

plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="Cluster 3")

plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="Cluster 4")

plt.legend()

plt.title("Customer Segments")



## Output:
![K Means Clustering for Customer Segmentation](sam.png)

![Screenshot (75)](https://github.com/user-attachments/assets/56c04480-2775-4207-bf28-892706470e7b)
![Screenshot (76)](https://github.com/user-attachments/assets/584f5ed2-e8a7-4809-a9ee-10f17071bed0)
![Screenshot (76)](https://github.com/user-attachments/assets/bac545f5-f3ac-40dc-b93a-3ec0334bd0e5)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
