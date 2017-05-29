# mp_paper_experiments
This repository contains numerical experiments for the paper 'Support recovery in unmixing problems by means of an altered Lasso-path algorithm for multi-penalty regularization'. In this work, we consider problems of the type 

  A(u+v) = y

where A is a (typical compressed sensing) sampling matrix, u is a sparse vector and v is signal noise drawn from some distribution. We are interested in recovering the support, that is the indices, of the sparse vector u. 

To fulfill this task, we use a multi-penalty regularization approach given by 

  1/2 ||A(u+v)-y||_2^2 + alpha ||u||_1 + beta/2 ||u||_2^2 -> min(u,v) (1)
  
where alpha, beta are two regularization parameters and || ||_p is the the typical lp norm. 

To produce a good solution solution to the original problem, ie. producing a tuple (u,v) where u has a 'reasonable' support that is close to the true support (the support of the u that generated the data), we need to choose regularization parameters alpha, beta. This is a difficult task, but with the help of the algorithm described in the repository https://github.com/soply/mpgraph/ , we can rather efficiently solve this functional for all possible combinations of alpha, beta. We can then use a simple criterion to chose one support of all these possible supports and compare it with the support of the u that originally generated the data y (in combination with noise v). In the given experiments, we are interested in how good the proposed approach and the multi-penalty regularization in general work.

Specifically, we consider the following experiments:

  - Experiments where we investigate if there exists any parameter combination alpha, beta such that we can recover the  support of u that generated the data y.
  - Experiments where we investigate if a simple criterion based on the signal-to-noise ratio is useful to also detect, amongst all different candidates, the support closest to the support of the generating support u.
  - As in (2) but with additional knowledge on the sparsity level of the generating support.
  - The number of support candidates that are produced by solving (1) with different combinations of regularization parameters alpha, beta.

To compare the results, we use some common compressed sensing techniques, namely:
  
  -Orthogonal Matching Pursuit
  -l1-regularization
  -iterative hard thresholding
  -a preconditioned version of l1-regularization
  
More details on the experiments is provided in the respective notebooks.
