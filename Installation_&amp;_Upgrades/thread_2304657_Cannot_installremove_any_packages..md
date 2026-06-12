---
title: "Cannot install/remove any packages."
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by misero on 2015-11-28
Attempting to modify any package gives an error. Example:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'unity' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
Any help?

---

### Post by ian-weisser on 2015-11-28
By default, 15.04 (Vivid) uses systemd, not Upstart.
If you haven't switched back to Upstart, then the failure seems expected.

---

