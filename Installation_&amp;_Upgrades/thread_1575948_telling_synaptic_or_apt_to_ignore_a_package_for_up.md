---
title: "telling synaptic or apt to ignore a package for upgrade?"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by surferX on 2010-09-16
I rebuild the stock kernel that comes with Ubuntu 10.04 with some code as modules, rather than compiled inline. This works fine, and install and the kernel work perfectly, I install it by:

dpkg -i linux-image-2.6.32-24-generic_2.6.32-24.39_i386.deb

however synaptic or apt does not think I have the kernel installed, and keeps on telling me I need to upgrade to the same version, etc.

I only want to upgrade if there is security flaw. Is there away of telling apt or synaptic that I have installed the standard ubuntu package (just that I build it myself) and to only alert me when there is a security fix required?

---

### Post by surferX on 2010-09-20
bump ?

---

### Post by perspectoff on 2010-09-20
Yeah, I think this would be a great feature.

Many automatic upgrades break something of mine, and I would like to choose which ones to be excluded from the automatic upgrade process.

This should be added to the brainstorm list.

Other than by manually choosing which updates to allow, which is tedious when you only want to exclude one or two packages from upgrades, I don't think this option exists.

---

### Post by JanKanis on 2010-09-23
I'm having nearly the same problem. I installed mercurial from source, and now I want to install hgview from the package system, but apt keeps insisting I have to install the mercurial dependency package. 

Anyone know some way of telling apt to pretend a certain package is installed?

---

