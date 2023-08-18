# Clustering

## Crime Data Problem Statement :-

Perform Clustering(Hierarchical, Kmeans & DBSCAN) for the crime data and identify the number of clusters formed and draw inferences.

## Airline Problem Statement :-

Perform clustering (hierarchical,K means clustering and DBSCAN) for the airlines data to obtain optimum number of clusters. 
Draw the inferences from the clusters obtained.

# Clustering Method using K-Means, Hierarchical and DBSCAN (using Python)

**Clustering** is a set of techniques used to partition data into groups, or clusters. Clusters are loosely defined as groups of data objects that are more similar to other objects in their cluster than to data objects in other clusters. Clustering refers to a very broad set of techniques for finding subgroups or clusters in a data set. This is unsupervised problem because we are trying to discover structure, in this case, distinct clusters on the basis of a dataset.

There are three basic types of clustering algorithms : partitional, hierarchical and density based algorithms.

+ **Partitional Clustering :** divides data objects into nonoverlapping groups. In other words, no object can be a member of more than one cluster, and every cluster must have at least one object. Example : K-Means and K-Medoids.

+ **Hierarchical Clustering :** determines cluster assignments by building a hierarchy. This is implemented by either a bottom-up or a top-down approach. These methods produce a tree-based hierarchy of points called a dendrogram. Example : Agglomerative clustering and divisive clustering.

+ **Density Based Clustering :** determines cluster assignments based on the density of data points in a region. This approach doesn’t require the user to specify the number of clusters. Instead, there is a distance-based parameter that acts as a tunable threshold. Example : DBSCAN (Density-Based Spatial Clustering of Applications with Noise) and OPTICS (Ordering Points To Identify the Clustering Structure).

Since clustering is popular in many fields, there exist a great number of clustering methods. In this section we focus on perhaps the three clustering approaches : K-means clustering, Hierarchical clustering and DBSCAN.

## K-Means Clustering

The K-Means Clustering takes the input of dataset D and parameter k, and then divides a dataset D of n objects into k groups. This partition depends upon the similarity measure so that the resulting intra cluster similarity is high but the inter cluster similarity is low. Cluster similarity is measured regarding the mean value of the objects in a cluster, which can be showed as the cluster’s mean.

![k-means algorithm](https://github.com/yagniksorathiya/Clustering/assets/129974278/4ba03f2b-0322-47b6-8fab-dbb93d892f2e)


The quality of the cluster assignments is determined by computing the sum of the squared error (SSE) after the centroids converge, or match the previous iteration’s assignment. The SSE is defined as the sum of the squared Euclidean distances of each point to its closest centroid. Since this is a measure of error, the objective of k-means is to try to minimize this value.

## Hierarchical Clustering

Hierarchical clustering involves creating clusters that have a predetermined ordering from **top to bottom.** There are two types of hierarchical clustering, Agglomerative and Divisive.

![Hierarchical clusterinf type](https://github.com/yagniksorathiya/Clustering/assets/129974278/df702b76-5b53-4941-91a2-787309d2b632)

+ **Divisive Clustering :** the type of hierarchical clustering that uses a top-down approach to make clusters. It uses an approach of the partitioning of 2 least similiar clusters and repeats this step until there is only one cluster. Divisive clustering is not commonly used in real life.

+ **Agglomerative Clustering :** the type of hierarchical clustering which uses a bottom-up approach to make clusters. It uses an approach of the partitioning 2 most similiar clusters and repeats this step until there is only one cluster.

## DBSCAN

**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** is a density based clustering algorithm. The main concept of DBSCAN algorithm is to locate regions of high density that are separated from one another by regions of low density.

DBSCAN can identify clusters in a large spatial dataset by looking at the local density of corresponding elements. The advantage of the DBSCAN algorithm over the K-Means algorithm, is that the DBSCAN can determine which data points are noise or outliers. DBSCAN can identify points that are not part of any cluster (very useful as outliers detector). But it slower than agglomerative clustering and k-means, but still scales to relatively large datasets.

There are two parameters in DBSCAN: minPoints and eps :

+ eps: specifies **how close points should be to each other to be considered a part of a cluster.** It means that if the distance between two points is lower or equal to this value (eps), these points are considered to be neighbors.

+ minPoints: **the minimum number of data points to form a dense region/ cluster.** For example, if we set the minPoints parameter as 5, then we need at least 5 points to form a dense region.

![DBSCAN type](https://github.com/yagniksorathiya/Clustering/assets/129974278/5e73dce8-f6fc-4cf2-9526-45346cbb2d69)

Based on the two parameters, the points are classified as **Core point, Border point** and **Noise point.**

![parameters](https://github.com/yagniksorathiya/Clustering/assets/129974278/86884502-d7c8-45ff-8d70-d83a50e89862)


#### Core Point

+ A point is a core point if it has more than a specified number of minPoints within eps radius around it or |N (p)|≥ minPoints .
+ Core Point always belongs in a dense region.
+ For example, let’s consider ‘p’ is set to be a core point if ‘p’ has ≥ minPoints in an eps radius around it.

#### Border Point

+ A point is a border point if it has fewer than minPoints within eps, but is in the neighborhood of a core point.
+ For example, p is set to be a border point if ‘p’ is not a core point. i.e ‘p’ has < minPoints in eps radius. But ‘p’ should belong to the neighborhood ‘q’. Where ‘q’ is a core point.
+ p ∈ neighborhood of q and distance(p,q) ≤ eps .

#### Noise Point

+ A noise point is any point that is not a core point or a border point.

Before we go through the DBScan algorithm, we should understand about **the Density Edge** and **the Density Connected Points :**
 
![Noise point](https://github.com/yagniksorathiya/Clustering/assets/129974278/15d843a7-0f5f-4995-845e-41cf21f0e3dd)

#### Density Edge:
If p and q both are core points and distance between (p,q) ≤ eps then we can connect p, q vertex in a graph and call it **“Density Edge”.**

#### Density Connected Points:
Two points p and q are said to be density connected points if both p and q are core points and they exist a path formed by density edges connecting point (p) to point(q).
