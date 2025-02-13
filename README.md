# Relevance-Feedback-Using-Rocchio-Algorithm
Implement and test methods for relevance feedback and apply explicit relevance feed- back methods, using relevance judgements of the Cranfield collection

# Dataset
The Cranfield collection is used for this project. The Cranfield Collection is a popular and commonly used dataset for IR projects and 
experiments. It was created in the 1960’s to study the effectiveness of IR systems. The dataset 
serves as a good example of a test collection because it has indexed documents, a set of test 
queries, and predefined relevance judgements. The Cranfield Collection is often referred to as a 
standardized dataset because of its well-defined structure that allows for consistent and 
reproducible experiments. Results from experiments on the Cranfield Collection are often 
comparable across studies due to its standard nature. 

# Methodology 
The documents and queries are preprocessed to remove punctuation, non-alphanumeric characters, and stop words. Documents and queries are then transformed into vectors using Sklearn library functions (TfidfVectorizor). The initial retrieval method finds the top 5 queries for each document using cosine similarity. Then the Rocchio algorithm is used to impliment relevance and explicit feedback by incorporating relevance judgements provided by the Crandfield collection.  The Rocchio algorithm modifies the original query by incorporating vectors from relevant and non-relevant documents, aiming to move the query closer to relevant documents and farther from non-relevant ones in the vector space. This approach effectively balances the original query intent with insights from user-provided relevance judgments. With the relevant and non-relevant documents identified, the Rocchio update is calculated. The updated query vector is computed by combining the original query vector (scaled by alpha), the mean vector of relevant documents (scaled by beta), and the mean vector of non-relevant documents (scaled by gamma). Instances where there are no relevant or non-relevant documents are skipped and do not contribute to the updated query vector. The resulting vector is reshaped into a two-dimensional format to ensure compatibility with subsequent processing. Each updated query vector is then appended to a list, which holds all modified query representations. Finally, the retrieval process is re-run using the updated query vectors to observe the impact of relevance feedback. The cosine similarity is calculated for each updated query vector, with all document vectors to determine the most relevant documents. 

# Results
The Rocchio algorithm had a notable impact on retrieval performance when comparing the updated retrieval metrics to the initial retrieval metrics. Initial retrieval showed low precision (0.0080), recall (0.0021), and F1 score (0.0033) with MAP 0.010481. The updated retrieval, after applying the Rocchio algorithm, showed higher precision (0.1937), recall (0.2577), and F1 score (0.1988) with MAP 0.287123. The retrieval metrics have significantly improved, indicating that the relevance feedback has been successfully applied, and the ranking of documents has been reordered to prioritize relevant documents.


![Screenshot 2024-12-19 225339](https://github.com/user-attachments/assets/60e2fd6e-342d-4514-98d6-3ad11e505ab6)

![PRECISION_RECALL_F1_SCORE](https://github.com/user-attachments/assets/0cb16289-6a3e-4b73-b152-2b933763fe0b)
![MAP_comparison_across_queries](https://github.com/user-attachments/assets/13757026-d61a-4a31-abea-e12ec20edea5)

![PRECISION-RECALL_CURVE_COMPARISON](https://github.com/user-attachments/assets/f667faa0-2584-4069-aa61-257d18a7fcd4)
![CONFUSION_MATRIX_DOC_REL](https://github.com/user-attachments/assets/3de7c767-b632-40fc-aac2-89ca4d1a38e0)
