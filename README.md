# Hyderabad Salaried Employee Segmentation Project

This project performs a comprehensive employee segmentation analysis on the `hyderabad-salaried-employees.csv` dataset. By leveraging unsupervised machine learning techniques, the analysis aims to identify distinct employee segments based on their experience and salary. The resulting clusters can provide valuable, data-driven insights for optimizing human resources strategies such as talent management, compensation, and retention.

---

### Project Overview

The analysis follows a standard data science pipeline, meticulously detailing each step from initial data exploration to final business recommendations.

1.  **Data Loading & Preprocessing:** The raw dataset is loaded, and a series of cleaning steps are performed to handle missing values and prepare the data.
2.  **Feature Engineering:** Raw, string-based features for experience and salary are transformed into clean, numerical formats.
3.  **Dimensionality Reduction:** Principal Component Analysis (PCA) is applied to reduce the data to a 2D space for effective visualization and more efficient clustering.
4.  **Clustering Analysis:** Two different clustering algorithms—K-Means and Agglomerative Clustering—are implemented and compared.
5.  **Model Evaluation & Comparison:** Multiple statistical metrics (Silhouette, Calinski-Harabasz, and Davies-Bouldin scores) are used to evaluate and compare the performance of the clustering models.
6.  **Business Insights:** The final, most robust clusters are profiled to provide actionable, strategic insights for the business.

---

### Requirements

To run this analysis, you must have the following Python libraries installed:

* `pandas`
* `numpy`
* `scikit-learn`
* `matplotlib`
* `seaborn`
* `missingno`
* `re`
* `scipy`

---

### Analysis Breakdown

#### Data Preprocessing & Feature Engineering

The initial dataset contains unstructured text and missing values. The following steps were performed to prepare the data:

* **Custom Functions:** Robust functions were created to convert complex strings like `"2 Year(s) 1 Month(s)"` and `"Rs. 6.71 lacs"` into numerical formats (`experience_years` and `salary_lacs`).
* **Missing Value Imputation:** Rows with critical missing values were dropped, while less critical ones (e.g., in `qualificationMas`) were filled with a placeholder.
* **Categorical Encoding:** `LabelEncoder` was applied to transform the remaining categorical columns (`companyName`, `designation`, etc.) into numerical values that the clustering algorithms can process.
* **Data Scaling:** The data was normalized using `StandardScaler` to ensure all features contributed equally to the clustering process, preventing features with a larger value range from dominating the distance calculations.

#### Dimensionality Reduction with PCA

To simplify the high-dimensional data and facilitate visualization, **Principal Component Analysis (PCA)** was used. The original features were projected onto two principal components that capture the maximum amount of variance, allowing us to visualize the clusters in a 2D scatter plot.



#### Clustering Models & Evaluation

Both K-Means and Agglomerative Clustering were performed with `n_clusters=5`, a number determined to be optimal by the Elbow Method, Silhouette Analysis, and dendrogram visualization.

* **K-Means Clustering:** A partitioning algorithm that groups data points by their proximity to cluster centroids.
* **Agglomerative Clustering:** A hierarchical, bottom-up algorithm that progressively merges the closest clusters.

The dendrogram below illustrates the merging process of hierarchical clustering and visually confirms the choice of 5 clusters.



---

### Model Comparison & Insights

A direct comparison of the clustering models was performed using key evaluation metrics.

#### Model Performance Comparison

| Metric                    | K-Means   | Agglomerative |
| ------------------------- | --------- | ------------- |
| **Silhouette Score** | 0.6125    | **0.6506** |
| **Calinski-Harabasz** | 3591.3191 | **4325.3211** |
| **Davies-Bouldin** | 0.5367    | **0.4932** |

**Conclusion:** The Agglomerative Clustering model consistently outperforms K-Means across all metrics, producing more distinct and well-separated clusters. This model's results are used for generating the final business insights.

#### Business Insights from Agglomerative Clusters

1.  **Cluster 0: Senior Leadership**
    * **Profile:** High average salary and moderate experience.
    * **Recommendation:** Focus on retention with personalized non-monetary benefits and leadership development opportunities.

2.  **Cluster 1: Entry-Level Professionals**
    * **Profile:** Low average experience and salary.
    * **Recommendation:** Invest in structured training, clear career paths, and mentorship programs to retain this vital talent pool.

3.  **Cluster 2: High-Caliber Executives**
    * **Profile:** An outlier group with an exceptionally high salary, likely specialized, top-tier talent.
    * **Recommendation:** Provide highly personalized compensation packages and exclusive perks to secure their loyalty.

4.  **Cluster 3: Mid-Career Specialists**
    * **Profile:** Balanced experience and salary. A crucial group for day-to-day operations.
    * **Recommendation:** Offer skill enhancement opportunities and promotions to prevent them from stagnating and to keep them engaged.

5.  **Cluster 4: Experienced Staff**
    * **Profile:** High experience with a moderate salary.
    * **Recommendation:** Acknowledge their loyalty and contributions with special bonuses or long-service recognition programs.
