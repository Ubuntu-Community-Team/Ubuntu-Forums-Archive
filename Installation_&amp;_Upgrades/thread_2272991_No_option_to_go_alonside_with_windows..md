---
title: "No option to go alonside with windows."
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by jack132 on 2015-04-10
Hello! I just have the demo at the current moment, but when I try to install Ubuntu I only get two options not three. The options are to erase everything (Dont want to do) or Something else (too advanced for me). I want to go alongside with windows (I am using Windows 7 64 bit). I am trying to install Ubuntu 14.04.2 LTS. Did I download the wrong version or??? Can someone help me?

---

### Post by Mark Phelps on 2015-04-10
If your machine came preinstalled witn Win7, it's likely that (1) the drive is completely full (leaving no room for Ubuntu) and (2), there are already the maximum of 4 partitions allocated on the drive (preventing the creation of any more).

To see what's there, when you're in the Ubuntu desktop, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here.

---

