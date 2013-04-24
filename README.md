Introduction
------------
Subnet is implemented by Python and it is designed to detecting disease related subnetwork from a large biological network (PPI, metabolic network) combined with gene expression data.

Pre-installtalation
-------------------
Python version 2.7 or later (http://www.python.org/)

Python packages:

* Biopython (http://biopython.org/wiki/Main_Page)
* NetworkX (http://networkx.github.io/)
* SciPy (http://www.scipy.org/)
* Numpy (http://www.numpy.org/)
* scikit-learn (http://scikit-learn.org/stable/)

Running ChIPdenovo
------------------
#### Command-line usage:
    python subnet.py -n <network_file> -g <gene_matrix_file> -o <output_file> [opts]
#### Options:
	-m <int>	:method of classification or regression (default: class)
	-t <float>	:percentage of top selected gene for searching (default: 1, no sort)
	-s <float>	:score cutoff for printing selected subnetwork (default: 0.6)
	-f <pickle>	:saved subnetwork python object used for visualization (default: subnetwork.py)
	-r <txt>	:saved gene list ranked by two measuring methods (default: gene_rank.txt)
	-h      	:produce this menu
#### Example:
    python subnet.py -n sample_data/HumanBinaryHQ_HINT.txt -g sample_data/GSE18864_classification.txt -o HINTclass_svm.txt -f HINTclass_svm.pk -r HINT_class_svm_rank.txt
Example data are provide in the directory *sample_data/*

Input and Output File
------
1. network file is the adjacency list format
2. gene matrix file starts with gene name or entrize id as first column and expression values for other columns, the last row starts with "outcome" and labels for each sample
3. the output files contain the ranked subnetwork by predicting accuracy and ranked genes names using m1 and m2 metric.
 m1 = m
 m2 = m*s*i
where m is total number of subnetwork contained gene, s is the score of each subnetwork and i is the importance of gene.

Visualize subnetwork
-------------------
Selected subnetwork can be plotted using as followed:

    python drawnet.py mark_gene diff_gene network_obj gene_matrix_file node

#### Example:
    python drawnet.py sample_data/breastcancer.gene sample_data/diffexpress.gene HINTclass_svm.pk sample_data/GSE18864_classification.txt 675

Contact us
----------
Questions, suggestions, comments, etc?

Author: Rendong Yang

Send email to cauyrd@gmail.com

Referencing Subnet 
----------------------
updating soon!
