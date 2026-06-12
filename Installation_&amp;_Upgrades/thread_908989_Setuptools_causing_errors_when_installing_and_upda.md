---
title: "Setuptools causing errors when installing and updating packages"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by WinterWeaver on 2008-09-03
Something really annoying.

Whenever I install new packages or upgrade my system, I would get this error:
(running Hardy)

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-setuptools (0.6c8-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-setuptools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Anyone know what is going on here?

tx

WW

---

