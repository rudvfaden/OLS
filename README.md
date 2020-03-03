# OLS

A small julia package to estimate ols and print out a nice formatted table.

## Usage

 `x` and `y` must be stores as arrays. Dataframes will not work.

Here is an example

```jl
# Simulation data
using OLS, Distributions
N        = 50
K        = 3
genX     = MvNormal(eye(K))
X        = rand(genX,N)
X        = X'
constant = ones(N)

epsilon    = rand(Normal(0, 2),N)
trueParams = [1,0.5,-0.3,0.9]
Y          = [constant X]*trueParams + epsilon


# Run OLS
b, se, t, R2, R2adj, F, s2, p=ols(Y,X)

# make labels
title = "My OLS"
lbly = "Dependent Var"
lblx = ["cont","var1", "Var2", "Var3"]

# print table
olstable(title,lbly,lblx,b,se,t,R2,R2adj,F,se,p)
```

![Results](https://www.dropbox.com/s/69jqbbybh4lcpk6/Screenshot%20from%202015-02-11%2012%3A36%3A40.png?dl=1 "Results of Estimation")
## Requirements
Distributions must be installed
