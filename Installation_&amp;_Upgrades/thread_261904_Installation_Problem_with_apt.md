---
title: "Installation Problem with apt"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by borncrusader on 2006-09-20
Hi all!

When I try to install something, I get this error message! Is there any way to overcome it???

```
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  gnucap
0 upgraded, 1 newly installed, 0 to remove and 200 not upgraded.
Need to get 943kB of archives.
After unpacking 2896kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/universe gnucap 1:0.34-4 [943kB]
Fetched 943kB in 28s (32.8kB/s)
dpkg: error processing /var/cache/apt/archives/gnucap_1%3a0.34-4_i386.deb (--unpack):
 subprocess dpkg-deb --control killed by signal (Segmentation fault)
Errors were encountered while processing:
 /var/cache/apt/archives/gnucap_1%3a0.34-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I checked in the archives folder and the package was there!

---

### Post by aysiu on 2006-09-21
I'm not sure if [this](http://ubuntuforums.org/showthread.php?t=76896) helps, but since no one else has answered, it's worth a shot.

---

