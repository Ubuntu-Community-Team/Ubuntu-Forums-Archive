---
title: "Conflict between freefem++ and fglrx"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by bela83 on 2015-03-24
Hi,

I am trying to install the package freefem++ via command-line and I stumble upon a strange conflict. Indeed freefem++ is a finite element solver for PDE and I can't see why it wants to remove my graphics driver.
```

sudo apt-get install freefem++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  freeglut3 libcr0 libhwloc-plugins libhwloc5 libibverbs1 libopenmpi1.6 libtorque2 ocl-icd-libopencl1
Suggested packages:
  blcr-dkms libhwloc-contrib-plugins opencl-icd
[B]The following packages will be REMOVED:
  fglrx fglrx-amdcccle fglrx-core[/B]
The following NEW packages will be installed:
  freefem++ freeglut3 libcr0 libhwloc-plugins libhwloc5 libibverbs1 libopenmpi1.6 libtorque2 ocl-icd-libopencl1
0 upgraded, 9 newly installed, 3 to remove and 0 not upgraded.
Need to get 6 093 kB of archives.
After this operation, 264 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

I still have the ability to install it from source but I'd rather use the repository.
Any help would be greatly appreciated :D

---

### Post by bela83 on 2015-03-31
Up!

---

