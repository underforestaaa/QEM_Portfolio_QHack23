# QEM_Portfolio_QHack23
 Error-Mitigated Quantum and Quantum-Inspired Portfolio Optimization

# Introduction

Portfolio optimization is considered to be one of the first tasks to benefit from the development of quantum computers. 
The idea behind portfolio optimization is to set up the best configuration of the given assets in terms of risk-to-return ratio. 
Mathematically this task is a Quadratic Unconstrained Binary Optimization (QUBO), which is perfectly mapped on Ising Hamiltonian.
There are several ways to tackle this problem: classical optimization algorithms, as well as quantum-inspired, gate-based VQE or QAOA algorithms, and quantum annealing. 
The experiments with real-data, due to its sparce and high-rank nature, show modest results, when are executed with quantum methods. 
Quantum Error Mitigation (QEM) method may improve the performance of NISQ algorithms for real-data use. In this project, we aim to evaluate such enhancement
for three algorithms: VQE, quantum annealing and quantum-inspired annealing (simulation of coherent ising machine). QEM for quantum-inspired algorithm here
represents our quantum-inspired postprocessing method, which we will test and benchmark in this project.


# Data preparation
For various portfolio theories, the risk and return are derived differently. For simplicity, we will use Modern Portfolio Theory (MPT), 
where risk is a covariance matrix between assets in a string $s$, and return is a $ln(mean_return)$ over 100 days before considered date.
So, to calculate elements of a QUBO, a list of asset prices during these 100 days is required. To obtain it, we use 
pandas_datareader and yfinance Python libraries. The code, obtaining data for S&P 500 assets is contained in "Data" folder, and the resulting lists of prices
is in the file "S&P_500.csv". This data is extracted later for MPT realization. 

# Quantum-inspired Algorithm

In this work we chose the algorithm, simulating the Coherent Ising Machine. The QEM-free QUBO solver is in Jupyter Notebook "Inspired annealing".
The algorithm is similar to the one, published in this article: https://doi.org/10.1364/OE.27.010288. Our QEM scheme is TBA. 

# VQE algorithm

In this project we will test VQE algorithm, executing it on IonQ computer. The IonQ device is chosen due to its high fidelity of operations and all-to-all connectivity, as it is especially important for high-rank real data.
We chose Measurement EM, as we have explicit data on errors in IonQ. 

# Quantum annealing

We will repeat QEM method, proposed in this article: arXiv:2210.08862 , to evaluate its results on real-data and with several hardwares.  