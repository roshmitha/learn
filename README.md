# learn
# Correlation code to try
#!/usr/bin/env python
# coding: utf-8

# In[ ]:


import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np



test = your train data


# In[ ]:


def correlation(df,threshold):
    # CREATING A CORRELATION MATRIX
    correlation_matrix = df.corr()
    # CREATING A CORRELATION HEATMAP
    plt.subplots(figsize=(20,15))
    sns.heatmap(correlation_matrix,annot=True,cmap="coolwarm")
    plt.title("Correlation Plot")
    plt.show()
     # CREATING A DF WITH CORRELATION PAIRS SORETED ON CORRELATION COEFF.
    corr_pairs = correlation_matrix.unstack()
    sorted_pairs = corr_pairs.sort_values(kind="quickstart")
    strong_pairs = sorted_pairs[abs(sorted_pairs)> threshold]
     # CREATING A LIST WITH HIGHLY CORRELATED PAIRS
    high_corr_var=np.where(correlation_matrix.abs()>threshold)
    high_corr_var=[(correlation_matrix.columns[x],correlation_matrix.columns[y]) for x,y in zip(*high_corr_var) if x!=y and x<y]
    #Creating a list of columns to be deleted 
    upper = correlation_matrix.where(np.triu(np.ones(correlation_matrix.shape), k=1).astype(np.bool))
    to_drop = [column for column in correlation_matrix.columns if any(correlation_matrix[column] > threshold)]
    

train_corr = train_data

correlation(train_corr,0.4)
print(correlation_matrix)
print(corr_pairs)





