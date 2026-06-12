---
title: "HowTo upgrade to a newer kernel"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by bc.haynes on 2014-02-07
What I found on the web was:
```
apt-cache search linux-image

Pick the one you want and then do:

sudo apt-get install linux-image-your_version_choice
```
That worked!

Is the kernel upgraded by the Update Manager automatically?   YES!

EDIT: Found the solution. I entered the wrong thing for **sudo apt-get install linux-image-your_version_choice**, the first time.

---

### Post by bcschmerker on 2014-02-07
The Ubuntu® Repositories carry Meta-Packages for upgrade LinUX Kernels.  For instance, LinUX Kernel 3.5.0-*-generic as released for Ubuntu® 12.10 would be listed for 12.04.4-LTS as linux-image-generic-lts-quantal; Kernel 3.8.0-*-generic, as linux-image-generic-lts-raring; and Kernel 3.11.0-*-generic, as linux-image-generic-lts-saucy. 

12.04.4-LTS cannot backport LinUX Kernel 3.13.0-*-generic as of 7 February 2014, as it is reserved for Ubuntu® Trusty Tahr™ development (14.01a2 as of 7 February 2014).

---

