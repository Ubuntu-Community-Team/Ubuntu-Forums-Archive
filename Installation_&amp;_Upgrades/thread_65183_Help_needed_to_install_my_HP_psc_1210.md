---
title: "Help needed to install my HP psc 1210"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by cjmdoire on 2005-09-13
I try to configure my HP pcs 1210 with Ubuntu 5.04. I can get the printer to work, but xsane cannot see any scanner. I read that I should download hpoj, but the installation is really not clear to me. Plus I cannot connect [http://localhost:631](http://localhost:631) whatever login and password I use (???????). Can anybody describe step by step that process so xsane can see my HP?
thanks

---

### Post by KingBahamut on 2005-09-13
from linuxprinting dot org 

>  Scanning works using the HPOJ  low-level driver together with its SANE  backend "hpoj". However, note that when using the current version (0.9) you can only scan, and when you don't use HPOJ at all you can only print. To fix this so you can both print and scan, you MUST install libusb and upgrade to the CVS version of HPOJ.

I had a similar problem with my 1350. I found the fix a bit more problematic than was capable of being handled, but after much futzing around, got it to work.

---

