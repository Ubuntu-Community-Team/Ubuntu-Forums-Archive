---
title: "Installing Ktorrent"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by viarand on 2008-03-10
When i try to install ktorrent 3.0.0 through terminal it gives the following error.

"CMake Error: Could not find REQUIRED package GMP"

I dont know what this error is.Please help me.

Thanks in advance

---

### Post by Jimmey on 2008-03-10
It means it couldn't find the (a) GMP package that it needs to run.

Try searching synaptic for GMP.

What version of ktorrent is available in the repositories?
```
apt-cache policy ktorrent
```

---

### Post by viarand on 2008-03-10
Installed: 2.2.5-0ubuntu1~gutsy1
This is the version i hav installed and this is the one in synaptic.Now i am trying to install ktorrent 3.0.0..

---

### Post by stoeptegel on 2008-03-11
There already is a ktorrent-kde4 package in the ppa repository, see kubuntu.org for adding this repository. No need to compile here.

---

### Post by viarand on 2008-03-13
Thank you.I have installed it with that repository.

---

