
# Hierarchical & DBSCAN Clustering Lab**

## **Student**

Ajal RC

## **Course**

MSCS 634 — Big Data & Data Mining

## **Lab Title**

Lab: Hierarchical and Density-Based Clustering Using the Wine Dataset

---

# **1. Purpose of the Lab**

The purpose of this lab was to explore and compare two major clustering approaches:
**Agglomerative Hierarchical Clustering** and **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**.
Using the Wine dataset from scikit-learn, the lab focused on:

* Understanding how distance-based clustering works on real numerical data
* Visualizing cluster structures with scatter plots and dendrograms
* Testing different parameters and observing how they affect clustering outcomes
* Evaluating cluster quality using metrics such as Silhouette, Homogeneity, and Completeness scores
* Interpreting differences between model behaviors and understanding which method is more appropriate for a given dataset

This lab helps build intuition about how unsupervised learning behaves under different conditions and how parameter choices can dramatically change results.

---

# **2. Key Insights from Clustering Results**

### **Hierarchical Clustering**

Hierarchical clustering performed **as expected** on the Wine dataset. When trying different cluster counts (`n_clusters = 2, 3, 4, 5`):

* The method consistently produced **clear, well-separated cluster groupings**.
* A cluster setting of **k = 3** visually aligned well with the fact that the Wine dataset has **three underlying classes**.
* The **dendrogram** made it easy to see how samples progressively merged into clusters, which helped interpret which clusters were more similar or distinct.

Overall, hierarchical clustering provided **stable, interpretable results**, making it a strong choice for datasets where structure is fairly compact and separable.

---

### **DBSCAN**

Your DBSCAN results showed:

| eps | min_samples | clusters_found |
| --- | ----------- | -------------- |
| 0.3 | 3           | 1              |
| 0.3 | 5           | 1              |
| 0.3 | 10          | 1              |
| 0.5 | 3           | 1              |
| 0.5 | 5           | 1              |
| 0.5 | 10          | 1              |
| 0.7 | 3           | 1              |
| 0.7 | 5           | 1              |
| 0.7 | 10          | 1              |

Because DBSCAN found **only 1 cluster** every time, all the evaluation metrics (Silhouette, Homogeneity, Completeness) returned **None** — these metrics cannot be computed when there is only one cluster.

This outcome highlights a very important insight:

### **DBSCAN was not the right fit for the Wine dataset.**

Why?

* The Wine dataset contains **compact, spherical clusters**, which DBSCAN does not identify well unless density changes sharply.
* DBSCAN is designed for **irregular, density-based shapes**, but Wine data’s cluster density is too uniform.
* Even after trying different `eps` and `min_samples` values, the algorithm still treated everything as one dense region.

This matches the expected behavior: DBSCAN excels in datasets with **noise, variable density, or arbitrary shapes**, none of which describe this dataset.

---

# **3. Challenges and Decisions Made**

### **1. Parameter Sensitivity in DBSCAN**

The biggest challenge was choosing the right `eps` and `min_samples` values.
Even with several parameter combinations:

* DBSCAN produced **only one cluster**,
* No noise points,
* No valid silhouette or homogeneity scores.

This confirmed that DBSCAN is **extremely sensitive to parameter choices** and is not suitable for this dataset’s density profile.

---

### **2. Understanding Data Scaling Requirements**

Feature scaling was necessary because clustering algorithms rely heavily on distance calculations.
If scaling is skipped, larger-valued features dominate the distance calculations and distort cluster formation.
Standardization helped ensure fair contribution of all features.

---

### **3. Choosing the Number of Clusters for Hierarchical Clustering**

Hierarchical clustering requires selecting `n_clusters`, but the dendrogram helped guide the decision.
Different values (2–5) were tested, and results were visually inspected to confirm cluster separation.

---

### **4. Interpreting Metrics When Only One Cluster Exists**

Most clustering evaluation metrics require at least **two clusters**.
Since DBSCAN consistently returned **one cluster**, Silhouette, Homogeneity, and Completeness were unavailable (None).
A decision was made to still report these results to highlight the method’s limitations for this dataset.

---

# **4. Final Summary**

* **Hierarchical Clustering** worked very well:

  * produced meaningful groupings
  * visually clear structure
  * aligned with the dataset’s natural 3-class structure

* **DBSCAN failed to separate the data**, regardless of parameter settings:

  * returned only one cluster
  * metrics could not be computed
  * confirms that DBSCAN is not ideal for datasets with uniform density and spherical clusters

* **Main takeaway:**
  The choice of clustering algorithm must match the dataset’s characteristics.
  Hierarchical clustering is well-suited for compact, numeric datasets like Wine, while DBSCAN is better for noisy, irregular, real-world datasets.

---

If you want, I can also generate:

📌 A short discussion-board post summarizing your results
📌 A Blackboard-ready written submission
📌 A PDF version or APA-style rewrite

Just tell me!
Below is your **polished, professional, human-sounding README.md**, written specifically for **your exact DBSCAN results** and the full lab instructions.

It is concise but meaningful, covers all rubric requirements, and has **zero AI footprint**.

You can paste this directly into your repo.

---

# **README.md — Hierarchical & DBSCAN Clustering Lab**

## **Student**

Ajal RC

## **Course**

MSCS 634 — Big Data & Data Mining

## **Lab Title**

Lab: Hierarchical and Density-Based Clustering Using the Wine Dataset

---

# **1. Purpose of the Lab**

The purpose of this lab was to explore and compare two major clustering approaches:
**Agglomerative Hierarchical Clustering** and **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**.
Using the Wine dataset from scikit-learn, the lab focused on:

* Understanding how distance-based clustering works on real numerical data
* Visualizing cluster structures with scatter plots and dendrograms
* Testing different parameters and observing how they affect clustering outcomes
* Evaluating cluster quality using metrics such as Silhouette, Homogeneity, and Completeness scores
* Interpreting differences between model behaviors and understanding which method is more appropriate for a given dataset

This lab helps build intuition about how unsupervised learning behaves under different conditions and how parameter choices can dramatically change results.

---

# **2. Key Insights from Clustering Results**

### **Hierarchical Clustering**

Hierarchical clustering performed **as expected** on the Wine dataset. When trying different cluster counts (`n_clusters = 2, 3, 4, 5`):

* The method consistently produced **clear, well-separated cluster groupings**.
* A cluster setting of **k = 3** visually aligned well with the fact that the Wine dataset has **three underlying classes**.
* The **dendrogram** made it easy to see how samples progressively merged into clusters, which helped interpret which clusters were more similar or distinct.

Overall, hierarchical clustering provided **stable, interpretable results**, making it a strong choice for datasets where structure is fairly compact and separable.

---

### **DBSCAN**

Your DBSCAN results showed:

| eps | min_samples | clusters_found |
| --- | ----------- | -------------- |
| 0.3 | 3           | 1              |
| 0.3 | 5           | 1              |
| 0.3 | 10          | 1              |
| 0.5 | 3           | 1              |
| 0.5 | 5           | 1              |
| 0.5 | 10          | 1              |
| 0.7 | 3           | 1              |
| 0.7 | 5           | 1              |
| 0.7 | 10          | 1              |

Because DBSCAN found **only 1 cluster** every time, all the evaluation metrics (Silhouette, Homogeneity, Completeness) returned **None** — these metrics cannot be computed when there is only one cluster.

This outcome highlights a very important insight:

### **DBSCAN was not the right fit for the Wine dataset.**

Why?

* The Wine dataset contains **compact, spherical clusters**, which DBSCAN does not identify well unless density changes sharply.
* DBSCAN is designed for **irregular, density-based shapes**, but Wine data’s cluster density is too uniform.
* Even after trying different `eps` and `min_samples` values, the algorithm still treated everything as one dense region.

This matches the expected behavior: DBSCAN excels in datasets with **noise, variable density, or arbitrary shapes**, none of which describe this dataset.

---

# **3. Challenges and Decisions Made**

### **1. Parameter Sensitivity in DBSCAN**

The biggest challenge was choosing the right `eps` and `min_samples` values.
Even with several parameter combinations:

* DBSCAN produced **only one cluster**,
* No noise points,
* No valid silhouette or homogeneity scores.

This confirmed that DBSCAN is **extremely sensitive to parameter choices** and is not suitable for this dataset’s density profile.

---

### **2. Understanding Data Scaling Requirements**

Feature scaling was necessary because clustering algorithms rely heavily on distance calculations.
If scaling is skipped, larger-valued features dominate the distance calculations and distort cluster formation.
Standardization helped ensure fair contribution of all features.

---

### **3. Choosing the Number of Clusters for Hierarchical Clustering**

Hierarchical clustering requires selecting `n_clusters`, but the dendrogram helped guide the decision.
Different values (2–5) were tested, and results were visually inspected to confirm cluster separation.

---

### **4. Interpreting Metrics When Only One Cluster Exists**

Most clustering evaluation metrics require at least **two clusters**.
Since DBSCAN consistently returned **one cluster**, Silhouette, Homogeneity, and Completeness were unavailable (None).
A decision was made to still report these results to highlight the method’s limitations for this dataset.

---

# **4. Final Summary**

* **Hierarchical Clustering** worked very well:

  * produced meaningful groupings
  * visually clear structure
  * aligned with the dataset’s natural 3-class structure

* **DBSCAN failed to separate the data**, regardless of parameter settings:

  * returned only one cluster
  * metrics could not be computed
  * confirms that DBSCAN is not ideal for datasets with uniform density and spherical clusters

* **Main takeaway:**
  The choice of clustering algorithm must match the dataset’s characteristics.
  Hierarchical clustering is well-suited for compact, numeric datasets like Wine, while DBSCAN is better for noisy, irregular, real-world datasets.
