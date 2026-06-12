---
title: "synaptic package manager error"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by hobbes_dmS on 2005-12-06
Hi, whenever I try to install a package using Synaptic I get the following error:
E: /var/cache/apt/archives/cvs_1-0x1.6e7820000004ep-1361.12.9-9ubuntu0.1_i3 86.deb:  unable to open files list file for package `liba52-0.7.4': Input/output error 
 
this file (cvs_1-0x....) doesn't even exist. 
when I use the shell, it looks like this:

```
sudo apt-get install cvs
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  cvs
0 upgraded, 1 newly installed, 0 to remove and 127 not upgraded.
Need to get 0B/1434kB of archives.
After unpacking 3097kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  cvs
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/cvs_1%3a1.12.9-9ubuntu0.1_i386.deb (--unpack):
 unable to open files list file for package `liba52-0.7.4': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/cvs_1%3a1.12.9-9ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
wolf@spiff:/var/cache/apt/archives$

```

anybody any idea?

thx in advance
hobbes_dmS

---

