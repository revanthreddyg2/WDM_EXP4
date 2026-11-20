### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE:20/11/26
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

df = pd.read_csv("clustervisitor.csv")

X = df[['Age']]

kmeans = KMeans(n_clusters=3, random_state=42)

df['Cluster'] = kmeans.fit_predict(X)

print(df)

for i in range(3):
    print(f"\nCluster {i}")
    print(df[df['Cluster'] == i])


```
### Output:
<img width="434" height="527" alt="image" src="https://github.com/user-attachments/assets/b00d9444-3837-4681-a6a2-1993cf794c45" />
<img width="419" height="231" alt="image" src="https://github.com/user-attachments/assets/e7d60653-bd83-4c76-8bdc-d821fd8a941f" />
<img width="421" height="217" alt="image" src="https://github.com/user-attachments/assets/265385cf-a76e-4641-835e-2ca6a71d7714" />
<img width="400" height="196" alt="image" src="https://github.com/user-attachments/assets/a94610ef-6368-4189-80f7-a94677fd3541" />

### Visualization:
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))

for i in range(3):
    cluster = df[df['Cluster'] == i]
    plt.scatter(cluster['Age'], cluster['Cluster'], label=f'Cluster {i}')

plt.scatter(
    kmeans.cluster_centers_,
    range(3),
    color='red',
    marker='X',
    s=200,
    label='Centroids'
)

plt.xlabel("Age")
plt.ylabel("Cluster")
plt.title("Visitor Segmentation using K-Means")
plt.legend()
plt.grid(True)
plt.show()
```
### Output:
<img width="692" height="448" alt="image" src="https://github.com/user-attachments/assets/639066b7-9126-4c23-b843-4ca89ba67361" />


### Result:
Thus the code has been executed succesfully
