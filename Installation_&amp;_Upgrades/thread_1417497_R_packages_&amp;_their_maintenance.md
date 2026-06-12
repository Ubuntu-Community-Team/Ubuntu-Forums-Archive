---
title: "R packages &amp; their maintenance"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Alexandre Putt on 2010-02-27
Hi!

I have a question/suggestion regarding the R distribution under Ubuntu. I noticed that there are quite a few R-related packages in Synaptic. However, this number falls short of the huge selection available at CRAN. 

Moreover, R has an internal package installation & upgrading facility which does quite well. It is integrated into the language itself. 

The problem is that most people will find at least some important R packages missing from the ubuntu repositories, and will have to use R facilities to install them anyway. Given that maintaining & packaging the full CRAN of 1000+ packages for ubuntu is not an option, wouldn't it be better not to have these optional packages in the repos at all? Their presence seems rather pointless and a complete waste of time for the developers of ubuntu. I will add that this creates a confusion as there are two overlapping sources of packages.

The distribution of R is based on R-base, R-recommended (just a few must have packages combined by the developers) and R-doc. Thus, the whole lot is reduced to three standard packages already present in ubuntu repos + a few dependencies (like gfortran, build-essential etc.).

So what do you think?

---

