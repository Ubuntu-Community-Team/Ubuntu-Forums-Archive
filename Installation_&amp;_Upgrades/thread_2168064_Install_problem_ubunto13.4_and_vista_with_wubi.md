---
title: "Install problem ubunto13.4 and vista with wubi"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by Sulon on 2013-08-16
So I installed ubunto 13.4 with the iso downloaded from the ubunto web site.  It seemed to run fine.  When I select ubunto from the operating system list I get windows fail to start.  
File : \ubuntu\winboot\wubildr.mbr
Status: 0xc000000
Info: the selected entry could not be loaded becouse teh application is missing or corrupt.

I am trying to install on a new partition that only has ubunto on it.

Does anyone have a clue what I am doing wrong?  :)

---

### Post by Mark Phelps on 2013-08-16
Yes ... you're mixing your installation approaches.  Wubi is designed to be installed using an EXISTING Windows filesystem partition.  IT does not have its own partition and thus, is generally used when partitioning would be a problem.  

Installing to a separate partition is done by booting from the Ubuntu installation media; NOT from inside Windows.

Also, Wubi support was dropped starting with Ubuntu 13.04, so you're installing in a manner that is no longer supported.

---

