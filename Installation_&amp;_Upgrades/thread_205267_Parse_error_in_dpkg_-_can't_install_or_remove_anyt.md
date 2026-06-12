---
title: "Parse error in dpkg - can't install or remove anything"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by bepcyc on 2006-06-28
when I try to use dpkg in anyway (through apt-get, aptitude, synaptic or adept) I always get next output:

> 
dpkg: parse error, in file `/var/lib/dpkg/available' near line 33233 package `kdemultimedia-kappfinder-data':
 value for `status' field not allowed in this context

line number 33233 in this file is 

> Status: install ok installed

and it doesn't look wrong

"dpkg --configure -a" results with the same problem

help

---

