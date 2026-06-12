---
title: "Cannot upgrade kernel"
date: 2018-01-21
forum: Installation &amp; Upgrades
---

### Post by abovebeyondg on 2018-01-21
Hi all,
I'm trying to upgrade the kernel on one server with no success 

Currently on : 3.13.0-61-generic

Wanted version: 3.13.0.139.148

Tried with: 
$ sudo apt-get update
$ sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic linux-headers-virtual
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Also tried the 
apt-get autoremove but no sucess, no kernel upgrade 

Any suggestions? Thanks!

---

### Post by cruzer001 on 2018-01-21
Hello

Is it installed?```


apt-cache policy linux-image-3.13
```

---

### Post by Impavidus on 2018-01-21
Maybe the meta-package that's supposed to pull in the kernel upgrade isn't installed for some reason. Try```
sudo apt-get install linux-generic
```
I assume you're on 14.04, right?

---

