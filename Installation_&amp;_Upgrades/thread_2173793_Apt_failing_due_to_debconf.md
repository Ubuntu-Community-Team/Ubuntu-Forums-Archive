---
title: "Apt failing due to debconf"
date: 2013-09-11
forum: Installation &amp; Upgrades
---

### Post by JaySeeJC on 2013-09-11
Apt is failing to install tzdata correctly. Attempting to reinstall it causes more errors.

```
# sudo apt-get install --reinstall tzdata                                                                                                                                                     100 &#8629;Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libdrm-nouveau1a
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 15 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for tzdata:amd64

```

It seems tzdata isn't on the ubuntu packages site either. [http://packages.ubuntu.com/search?searchon=contents&keywords=tzdata&mode=exactfilename&suite=raring&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=tzdata&mode=exactfilename&suite=raring&arch=any)

---

