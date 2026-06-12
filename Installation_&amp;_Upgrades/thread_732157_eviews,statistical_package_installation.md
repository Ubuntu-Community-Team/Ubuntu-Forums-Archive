---
title: "eviews,statistical package installation"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by shanku74 on 2008-03-22
Hi all!

I can not install statistical packages like eviews, stata, SPSS in Ubuntu 7.10. please suggest the possible ways to overcome the problem.

thanks

---

### Post by ad_267 on 2008-03-22
You could try running these programs under wine or an alternative is to use the open source statistical package R. It can be installed using the synaptic package manager and installing "r-base". R is a very powerful statistics package but it is command line based so there is a bit of a learning curve if you're used to a GUI.

Edit:
Eviews is designed for Windows, but both Stata and SPSS are available for Linux. If you have the Windows versions of these packages you should contact the supplier and ask about getting a Linux version.

---

### Post by gah789 on 2008-03-24
Few statistical packages are truly general purpose.  Each is good for some specific areas of statistics.  If your starting point is eViews, then it is likely that you are most interested in time series and similar econometric analysis.  In that case, you should look at gretl - version 1.6.5 can be installed from the standard Ubuntu repositories.  There is a more recent version but unless you need highly specific extensions then it is hardly worth going to the trouble of compiling and installing it.

The advantage of gretl is that it is open source, free and quite easy to learn.  Another time series econometrics package is Time Series Modelling (TSM - see [www.timeseriesmodelling.com](www.timeseriesmodelling.com)) - not free but not expensive.  It relies upon the Java Runtime Environment as a package that is run under the Ox language interpreter, which is free to academic users.  TSM works under Linux version of Ox though it can be a little troublesome to set it up.

Stata covers a wide range of statistics & econometrics and the Unix version works on most flavours of Linux (if necessary use the statically linked version to ensure that you get the right libraries), but it is a commercial product and it is quite expensive for non-academic users.  SPSS, SAS, S-Plus, etc are even more expensive but come in Linux versions.

R is open source and free, but the learning curve is worse than for any statistics package that I know of - I used to write statistical software and have used many different packages.  This is suitable if you want to take advantage of novel or sophisticated statistical techniques, but in my view it is entirely unsuitable for the novice user.  The cost of learning to use it is disproportionate to the potential benefits unless the cost of your time is very low.  However, for simple statistical techniques you can combine R with the add-in RCmdr package which was designed for teaching but is much easier for the novice user.  There is another interface called Rkward but I am not sure whether it works on Ubuntu.

A final remark.  If you have very large datasets - i.e. ones that are too large to store in memory - then there is really no alternative to SAS or SPSS.

---

### Post by Huss on 2008-07-13
Wow, thanks Gah.

I'm going to give Gretl a go

---

