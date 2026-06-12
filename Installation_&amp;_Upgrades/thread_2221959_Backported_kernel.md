---
title: "Backported kernel"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by cogset on 2014-05-04
I've been using this kernel **linux-image-3.0.0-20-generic** for a long time now in Lucid to solve some issues with the 2.6.x line of kernels:it worked,so I did not give it much thought after installing-now,leaving other considerations aside,I've seen updates available for the 2.6.x kernel and this got me thinking whether there were updates for my current kernel too.
As it turns out,I'm not even sure where it came from,because dpkg says 
```
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-lts-backport-oneiric
```
and I indeed have backports enabled
```
deb http://archive.ubuntu.com/ubuntu lucid-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu lucid-backports restricted main multiverse universe
```
but I also remember adding this ppa
```
deb http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu lucid main
```so where this kernel came from?
I seem to remember that simply enabling backports did not make it available and that I installed it only after adding that kernel ppa above,but frankly I'm not sure.

So,the next question would be:where I can (eventually) find updates for that kernel?
I can see some available but are kinda old too,given that these comes from Oneiric,I suppose the logical answer could be backports from Quantal,but do they exist at all for Lucid?
I've read somewhere that this was planned,i.e. backporting kernels from Quantal to Lucid,but has it been done?

---

