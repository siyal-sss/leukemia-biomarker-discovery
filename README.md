# leukemia-biomarker-discovery
Genomic data science project using Google Colab to analyze and classify ALL/AML leukemia samples from transcriptomic profiles. Implements PCA for dimensionality reduction, random forest for predictive modeling, and hierarchical clustering heatmaps to visually discover key diagnostic gene biomarkers.

Project Context & Biological Challenge
In microarray and RNA-Sequencing analysis, datasets typically present a severe challenge known as the "curse of dimensionality" (where the number of features, p, is vastly greater than the number of clinical samples, n). This specific workflow analyzes the classic Golub et al. leukemia dataset, which profiles thousands of gene expression levels across human bone marrow samples to differentiate between two major hematological malignancies: Acute Lymphoblastic Leukemia (ALL) and Acute Myeloid Leukemia (AML). Accurate computational classification is critical because these sub-types require entirely different therapeutic strategies.

Technical Architecture & Implementation
The pipeline is constructed sequentially to simulate a professional bioinformatics research workflow:

Data Preprocessing and Tidy Restructuring: Raw expression matrix inputs contain a mixture of numeric values and qualitative call flags (A/P/M). The pipeline filters out non-numeric indicator tags, isolates gene descriptive data, and transposes the high-dimensional feature matrix so that patient samples represent rows and individual gene accessions act as columns.

Feature Standardization: To counteract variance distortions from heavily overexpressed genes, Z-score normalization is applied across the feature space, ensuring equal weight during mathematical transformations.

Dimensionality Reduction (PCA): Using Principal Component Analysis, the 7,129-dimensional gene expression space is projected down into a two-dimensional coordinate system. This unsupervised step visually evaluates the strength of the biological signal by observing whether ALL and AML samples naturally segregate into distinct clusters based purely on transcriptomic variance.

Machine Learning Classification: A Random Forest Classifier is trained on the structured expression matrix. Random Forests are uniquely resilient to overfitting in low-sample, high-feature biomedical profiles due to their ensemble nature and feature bagging mechanics. The model is rigorously evaluated using classification reports, macro-accuracy metrics, and custom confusion matrix heatmaps.

Unsupervised Hierarchical Clustering (Clustermaps): To identify overarching genetic patterns, the pipeline isolates the top 50 most highly variable genes across all patient cohorts. It constructs a dual-dendrogram heatmap that hierarchically clusters both the patient cohorts (revealing disease subtypes) and the genes simultaneously (revealing co-expressed gene networks).

Diagnostic Biomarker Identification: Leveraging the trained classifier's internal feature importance mechanics, the pipeline calculates, ranks, and outputs the top diagnostic gene drivers. This automates the discovery of candidate oncogenes, transcription factors, or surface markers that statistically dictate the boundary between ALL and AML.
