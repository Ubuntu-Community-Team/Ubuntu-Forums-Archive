---
title: "problems while upgrading to 10.04 from within Kubuntu KDE"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by sumo2010 on 2010-05-04
I was upgrading to 10.04 from within Kubuntu and it had to exit on an libc6 package error. Upon exiting, almost all commands in the terminal gave segmentation faults (cd and pwd were two exceptions).

I used the Lucid LiveCD to go in and mnt the filesystem and chroot into it and the same behavior was reproduced.

My question is, how do I fix this with the LiveCD? I need to remove the libc6 package and upgrade it, but I am not able to "inside" that filesystem. 

I will probably end up just backing up all my files and configuration files and doiing a clean install. (Btw, is there a good tutorial for that?)

I would like to know how to fix it though without a clean (re)install. Thank you.

---

