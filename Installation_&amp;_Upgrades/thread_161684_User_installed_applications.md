---
title: "User installed applications"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by asundaresan on 2006-04-17
Hi,

I installed quite a few applications using apt-get after selecting a workstation install during the install process. I'd like to find out which applications I installed.

I know that I can get a list of applications using 
```
dpkg --get-selections > selections.txt
```

but this gives me _all_ programs installed during the OS install. Is there any place I can get a list of the packages installed by default for breezy, so that I can do a diff to find out the programs that _I personally_ installed?

Thanks,
Aravind.

---

### Post by Shutdownrunner on 2006-04-17
Try to check dependencies of ubuntu-[sth] packages e.g. ubuntu-minimal, ubuntu-base, ubuntu-desktop or whatever you have installed. I don't know how to check dependencies of a package in command line, but I think that using apt-cache plus some parameter should do. Check man apt-cache for more information.

---

### Post by Qrk on 2006-04-17
If you installed them using synaptic/apt-get, you can check /var/cache/apt/archives for every .deb package you've installed. These are the packages themselves, not just a list. 

If you use aptitude (like me) it will save a list. This is available in the file /var/log/aptitude.

---

