
# barthgn package


## Bartlett Correction and Bootstrap Adjustment Methods for Likelihood-Based Inference in the Hypergeometric-Normal Random-Effects Model for Rare Event Meta-Analysis

The hypergeometric–normal random-effects model is widely used in meta-analyses of binary outcomes, providing a direct framework for modeling arm-level data from individual studies. This approach has proven particularly effective for meta-analyses involving rare events, offering relatively accurate estimation of treatment effects. However, when the number of studies is small or when many trials include zero events, large-sample approximations may break down, and the resulting inferences can be unreliable. To address these issues, this package implements higher-order asymptotic inference for the hypergeometric–normal random-effects model using Bartlett correction and bootstrap. Two improved approaches are provided: an analytic correction method and parametric bootstrap-based approaches.



## Installation

Please download "barthgn_1.1-1.tar.gz" and install it by R menu: "packages" -> "Install package(s) from local files...".

Download: [please click this link](https://github.com/nomahi/barthgn/raw/main/barthgn_1.1-1.tar.gz)

Manual: [please click this link](https://github.com/nomahi/barthgn/raw/main/barthgn_1.1-1.pdf)




## R Example Code

```r

#  R example code for implementing the improved methods for hypergeometric-normal (HGN) random-effects model analysis

# The "barthgn" package
# GitHub webpage: https://github.com/nomahi/barthgn/

###

# Download the R package file from the following URL:
# https://github.com/nomahi/barthgn/raw/main/barthgn_1.1-1.tar.gz

# Then, install the package (tar.gz format) by R menu: "packages" -> "Install package(s) from local files...".

###

pkgCheck <- function(pkg) {
  if (!requireNamespace(pkg, quietly = TRUE)) install.packages(pkg)
  suppressPackageStartupMessages( library(pkg, character.only = TRUE) )
}

pkgCheck("doSNOW")				# load or/and install the depended packages
pkgCheck("doParallel")
pkgCheck("parallel")
pkgCheck("foreach")
pkgCheck("BiasedUrn")

##

# Analyzing the example dataset "rosiglitazonemi" using the HGN model

library("barthgn")					# load the "barthgn" package

data("rosiglitazonemi")

print(rosiglitazonemi)
attach(rosiglitazonemi)

exact_hgn_RE(d1, n1, d2, n2)

LRCI_mu_RE(d1, n1, d2, n2)
LRCI_mu_RE_Bartlett(d1, n1, d2, n2)
LRCI_mu_RE_bartbs(d1, n1, d2, n2)
LRCI_mu_RE_boot(d1, n1, d2, n2)
ESCI_mu_RE_boot(d1, n1, d2, n2)

detach(rosiglitazonemi)
