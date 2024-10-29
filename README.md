# ALLIGNN for magnetic moments

ALIGNN-mm is a modified version of [ALIGNN](https://github.com/usnistgov/alignn) to provide functionality for making 
atomwise predictions of local magnetic moments. ALIGNN-mm is based on this [release](https://github.com/usnistgov/alignn/tree/v2024.1.14) of ALIGNN.
Note that installing this package will overwrite the alignn package in a python environment, so it is recommended to use a
virtual environment for the use of this package.

## Differences

### alignn_atomwise.py

`alignn_atomwise.py` is modified such that instead of having an atomwise output and a separate graphwise output, the `alignn_atomwise`
will instead have its global output be determined by the atomwise output given by the following formula:

$G(S) = \sqrt{\sum_{i\in S} \sum_{j=0}^N (\nu^i_j(S))^2}$

Here $G(S)$ is the graphwise output for a graph $S$, $\nu_j^i$ is the $j$-th component of the nodewise output of the $i$-th node,
and $N$ is the size of the nodewise output vectors. Note that in the case of magnetic moments, where $j \in \{x,y,z\}$, this
can be rewritten as the magnetude of the sum of the atomwise magnetic moments. That is:

$G(S) = |\sum_{i\in S} \boldsymbol{\mu}_S^i|$

Here $\boldsymbol{\mu}_S^i$ is the local magnetic moment vector at atom $i$.