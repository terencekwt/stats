---
title: "The Efficient Frontier"
subtitle: "Deriving Markowitz's equation"
author: Terence Tam
date: 2015-06-07 12:00:00
layout: post
header-img: "img/post-bg-06.jpg"
---

We all have to deal with 401K allocation some point in our life right? We are very indecisive in choosing the best subset from a basket of securities that will give us the highest return, yet minimizing the risk. The efficient frontier by Markowitz can help us decide by showing us the minimum risk for each level of expected return and vice versa.

Let's say you have three funds to choose from. Security $A$ tracks the S&P500, Security $B$ tracks the NASDAQ and prices of the technology sector, and Security $C$ is an indicator of the energy sector. Given we have historical records (daily stock price, daily % return) of these securities, we could find the variance and the covariance for these stocks. The variance of one stock would be the fluctuating price of that particular stock, where a higher variance would indicate the stock has a higher risk because the %return is not guaranteed or fixed. Covariances, on the other hand, indicates how much two stocks follow similar movements. For instance, two stocks both from U.S. market would go down if the broader U.S. market is on a downward trend.

In our example example, let's say the four securities takes on four random variables. Then the expected % return for the securities are

$$ \bar{Z} = \begin{pmatrix} E(A) \\ E(B) \\ E(C) \\ E(D) \end{pmatrix} = \begin{pmatrix} 14 \\ 12 \\ 15 \\ 7 \end{pmatrix}$$

where 14 stands for 14% average expected return for stock $A$, 12% for stock $B$, and so on.

Then, we also define the sets of weights for the portfolio
$$ W = \begin{pmatrix} w_A \\ w_B \\ w_C \\ w_D \end{pmatrix} $$

such that $w_A+w_B+w_C+w_D=$ the amount of money in total we are investing

The total average expected return of a portolio would be

$$E(P) = W^{T}\bar{Z}$$

The variance of the portfolio will be

$$Var(P) =  Var(W^{T}\bar{Z}) = W^{T}Var(\bar{Z})W^{T} = W^{T}\Sigma W^{T}$$


Let's run a simple R program to generate the efficient frontier for our particular choices of securities.


{% highlight r %}
zbar <- c(14, 12, 15, 7)
S <- matrix(c(185, 86.5, 80, 20, 86.5, 196, 76, 13.5, 80, 76, 411, -19, 20, 13.5, -19, 25), 4)
S
{% endhighlight %}



{% highlight text %}
##       [,1]  [,2] [,3]  [,4]
## [1,] 185.0  86.5   80  20.0
## [2,]  86.5 196.0   76  13.5
## [3,]  80.0  76.0  411 -19.0
## [4,]  20.0  13.5  -19  25.0
{% endhighlight %}

You can also embed plots, for example:

![plot of chunk unnamed-chunk-2](/figures/unnamed-chunk-2-1.svg) 

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
