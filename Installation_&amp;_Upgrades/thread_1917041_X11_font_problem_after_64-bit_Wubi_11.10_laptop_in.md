---
title: "X11 font problem after 64-bit Wubi 11.10 laptop installation"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by lmlahti on 2012-01-29
Dear,

I installed the new 64-bit 11.10 Ubuntu using WUBI on my HP2540p laptop. Then I installed manually R-2.14.1. When trying to do standard plots in R I get the following error message which hints at more general system issue:

> barplot(seq(5))
Error in axis(if (horiz) 1 else 2, cex.axis = cex.axis, ...) : 
  X11 font -adobe-helvetica-%s-%s-*-*-%d-*-*-*-*-*-*-*, face 1 at size 12 could not be loaded

The same problem does not occur on my fresh Workstation installation with 64-bit Ubuntu 11.10 (NO Wubi) on HP Z400, so I thought this might be Wubi-related issue. 

I have tried to search the forums and install various extra packages but nothing seems to help. Is there an easy fix to this?

---

### Post by lmlahti on 2012-01-30
Sorry, the same problem occurs also in my HP Z400 workstation which was installed cleanly without Wubi.

So this seems to be 64-bit or 11.10-related issue.

---

### Post by lmlahti on 2012-01-30
Dear list, 

I was able to install R-2.14.1 successfully with system installation with the following steps:

Add the following lines in /etc/apt/sources.list
deb [http://cran-mirror.cs.uu.nl/bin/linux/ubuntu](http://cran-mirror.cs.uu.nl/bin/linux/ubuntu) oneiric/
deb [http://cran-mirror.cs.uu.nl/](http://cran-mirror.cs.uu.nl/) oneiric-backports main restricted universe 

Then run in terminal:
sudo apt-get update
sudo apt-get install r-base

No more font problems. However, the font problem still seems to be a problem with manual installation from the R-2.14.1.tar.gz tarball but I can skip this part for now.

---

