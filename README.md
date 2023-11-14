# EXNO-08-Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start the program
2. Import the necessary python libraries
3. Read the dataset of Mall_Customers csv file
4. From sklearn libraary select the cluster and import KMeans Clustering
5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method
6. Plot the graph x and y as Number of Clusters and wcss respectively
7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)
8. Stop the program


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: JAYABHARATHI S
RegisterNumber:  212222100013
*/
```
```python

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

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
data["cluster"] = y_pred

df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="olive",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")

```

## Output:
## Data Head()
![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/2f6a91bf-ce74-4a4d-954b-f13e71cde921)

## Data.info()
![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/4423bf1a-4930-4bc1-9b3d-4d38b9895e44)

## Null Values
![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/d1404b73-ee55-4354-808f-dc0bb2f4d9e8)

## Elbow Graph
![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/f6606dcf-8669-45eb-b929-f06c1a732a7b)

## K-Means Cluster Formation
![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/9b49f689-6e11-49db-acc0-cfcbb5e3b589)

## Predicted Value

![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/f4e033a9-57a5-4874-a465-bf2df698b1f8)

## Final Graph

![image](https://github.com/Jayabharathi3/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120367796/375ea230-04a8-4cbe-9bc9-a4bd3967996d)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
