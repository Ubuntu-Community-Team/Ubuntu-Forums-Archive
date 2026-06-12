---
title: "Need ld-linux.so.2"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2007-05-24
Hi:
feisty fawn amd 64, migrating from slackware and redhat
I'm attempting to install a binary not in the repositories, it appears that
ld-linux.so.2 is needed. 
1)Where can I get this shared library?
2)If this shared library is part of a package is there a way to query ubuntu 
   for a specific shared library?
Edit: 
  Some googling indicates that this is part of the dynamic linker...
I tried the following:
"""
 sudo apt-get install ldso
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ldso is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6-dev libc6
E: Package ldso has no installation candidate
"""
don't know where to go from here....
Thanks
Tim

---

