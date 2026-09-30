# MSCS 634 Lab 5: Hierarchical and DBSCAN Clustering

Rohail Shaikh

## Purpose

Compare agglomerative hierarchical clustering and DBSCAN on the 178-row, 13-feature Wine dataset bundled with scikit-learn. The notebook explores the data, standardizes the features, tests parameters, plots clusters and a dendrogram, and reports silhouette, homogeneity, and completeness scores.

## Files and running the lab

- `MSCS_634_Lab_5_Rohail_Shaikh.ipynb`: notebook with code, results, and plots.
- No separate dataset download is needed; the notebook calls `sklearn.datasets.load_wine()`.

Open the notebook in Jupyter Notebook or JupyterLab. If needed, install `pandas`, `numpy`, `matplotlib`, `scipy`, and `scikit-learn` in your Python environment. Choose **Kernel > Restart & Run All** to reproduce the saved results.

## Results and decisions

- Ward hierarchical clustering was tested with 2, 3, and 4 clusters. Three clusters gave the best tested silhouette (0.277) and completeness (0.783), with homogeneity 0.790. The dendrogram shows three broad groups at the marked cut.
- DBSCAN was tested with `eps` 2.0, 2.3, and 2.6 and `min_samples` 5 and 8. At `eps=2.3`, `min_samples=5`, it found 2 clusters and 42 noise points. Silhouette was 0.331 on 136 assigned wines; homogeneity 0.462 and completeness 0.492 count noise as a label across all wines.
- DBSCAN's parameter choice was the main challenge: a smaller radius marked many wines as noise, while a larger radius merged assigned wines into one cluster. A single assigned cluster has no silhouette score. The scatter plots use two PCA axes for display, but clustering uses all 13 standardized features.
