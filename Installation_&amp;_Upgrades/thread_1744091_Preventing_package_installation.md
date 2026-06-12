---
title: "Preventing package installation"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Worp8d on 2011-04-30
I'm in the process of installing the usual Python/Numpy/Scipy/Matplotlib combination.  I'm using the installed version of Python (2.7) (Ubuntu 11.04) but I've compiled Numpy and Scipy (and ATLAS/LAPACK etc.) from source.  I now want to install matplotlib from the repositories but every time I do python-numpy is installed as a dependency of python-matplotlib.  I've tried "apt-get hold python-numpy etc." and locking the version of each package in Synaptic but both synaptic and apt-get will happily install the packages when requested, I assume because hold/lock version don't work on packages that aren't yet installed.

How can I prevent these packages being installed?  Or is there a way to tell Ubuntu that I already have versions?

---

### Post by Worp8d on 2011-05-01
According to a poster on another forum synaptic on their distro will not installed uninstalled packages that are on hold.  Is this a bug?

Also bump.

---

### Post by Yudley on 2011-10-18
i also wanna install blas+lapack+atlas+numpy+scipy+matplotlib on oneiric (11.10)

I'd either wanna install all of them through apt-get, 

or all of them through sources, in which case I'd wanna keep it isolated from the rest of the system as much as possible (probably a home-directory install)

mix-n-match of apt-get and sources sounds dangerous to me

from googling, I see that one of the packages to be installed is atlas-sse2-* or similar, but I find no package in oneiric that has both the words "atlas" and "sse2" in the package name

maybe the packages are not available yet owing to the freshness of the oneiric release

---

