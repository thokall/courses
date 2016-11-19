---
title: "Working with selected R functions"
output:
  html_document: default
  pdf_document: default
layout: default
---

# Introduction<a id="orgheadline1"></a>

There is a number of R functions available in the basic, pre-loaded packages, such as *base*, *utils* or *stats* and there is a huge number of functions available via third-party packages. Today, we will work a bit with some of the functions that are commonly used by R users coming from different disciplines. In particular, we will:

-   Learn how to work with sets.
-   Work with polynomials.
-   Learn how to define and work with functions.
-   Do some basic calculus.
-   Learn about *formulas*.
-   Work with some selected statistical tests.
-   Learn more about setting up a statistical analyses workflow by fitting a linear model to  example data.

## Exercise FNS1. Create and work with sets<a id="orgheadline4"></a>

1. Open R-studio and create three sets of genes: G1 = {'ANK-1', 'ANK-c', 'GALNTL-1'}; G2 = {'ANK-1', 'FMA', 'RHO', 'GRP'}; G3 = {'GALNTL-1', 'ANK-c', 'HQX'}. Visualise membership relations between all elements of the sets using Venn diagram. Use package *venn*.

<details>
<summary>:key: Click to see an example of how to do this in R</summary>
{% highlight R %}
library('venn')
G1 = c('ANK-1', 'ANK-c', 'GALNTL-1')
G2 = c('ANK-1', 'FMA', 'RHO', 'GRP')
G3 = c('GALNTL-1', 'ANK-c', 'HQX')
venn(list(G1=G1, G2=G2, G3=G3))
{% endhighlight %} 
</details>

2. What is the:
- Union of G1 and G3?
- Union of intersections: G1 with G2 and G1 with G3?
- Difference between G2 and G3?
- Is union of G1 and G2 equal to the intersection of G2 with G3?
- Are genes *ANK-c* and *GALNTL-1* members of the intersection of G1 with G3?

  <details>
  <summary>:key: Click to see an example of how to do this in R</summary>
  {% highlight R %}
  union(G1, G3)
  union(intersect(G1, G2), intersect(G2, G3))
  setdiff(G2, G3)
  setequal(union(G1, G2), intersect(G2, G3))
  is.element(c('ANK-c', 'GALNTL-1'), intersect(G1, G3))
  {% endhighlight %} 
  </details>  

## Exercise FNS2. Define and work with polynomials<a id="orgheadline5"></a>
1. Define the following polynomials p1 and p2: $5x^3 + 4x^2 + 7$ and $2x^2 + 3x - 11$.
  <details>
  <summary>:key: Click to see an example of how to do this in R</summary>
  {% highlight R %}
  library(polynom)
  p1 <- polynomial(c(7, 0, 4, 5))
  p2 <- polynomial(c(-11, 3, 2)) 
  {% endhighlight %} 
  </details>  
  
2. Define a polynomial (p3) with the following zeros: -3, 4, 7.
  <details>
  <summary>:key: Click to see an example of how to do this in R</summary>
  {% highlight R %}
  library(polynom)
  p3 <- poly.calc(c(-3, 4, 7))
  {% endhighlight %} 
  </details>  

3. Define a polynomial (p4) passing through the following points: $A(-3,7)$, $B(24,-9)$, $C(7,4)$.
  <details>
  <summary>:key: Click to see an example of how to do this in R</summary>
  {% highlight R %}
  p4 <- poly.calc(c(-3, 24, 7), c(7, -9, 4))
  {% endhighlight %} 
  </details>  

4. Find approximate maximum (value) of the $p4$ polynomial using its visualisation.
  <details>
  <summary>:key: Click to see an example of how to do this in R</summary>
  {% highlight R %}
  plot(p4, ylim=c(-1, 8))
  {% endhighlight %} 
  The maximum is between 6 and 8.
  </details>  

5. Perform the following operations:
- Find the sum of $p1$ and $p3$.
- Divide $p4$ by $p2$.
- Find the area under $p4$ on the $[-10, 0]$ interval.
- Find the second order derivative of $p1$.
- Find the Greatest Common Divisor of $p1$ and $p2$.
- Find the Least Common Multiple of $p1$ and the sum of $p2$ and $p3$.
  <details>
  <summary>:key: Click to see an example of how to do this in R</summary>
  {% highlight R %}
  p1 + p3
  p4 / p2
  integral(p4, c(-10, 0))
  deriv(deriv(p1))
  GCD(p1, p2)
  LCM(p1, p2 + p3)
  {% endhighlight %} 
  </details>  
