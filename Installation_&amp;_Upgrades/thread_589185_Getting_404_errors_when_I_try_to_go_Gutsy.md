---
title: "Getting 404 errors when I try to go Gutsy"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by CheshireMac on 2007-10-24
Hey folks. I'm trying to upgrade to Gutsy and I keep getting this message in the initial stages: 
```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 404 Not Found
```

I've seen this before, when I try to do anything with apt-get. It never got in the way of anything essential before, but I have a feeling I'm not quite done setting up this distro before I go anywhere with the new one.
A little assistance would be greatly appreciated.

---

### Post by linuxwizard on 2007-10-24
Try removing or disable extra repos you added to your source list. I also have seen other post about medibuntu servers being down that is why 404 errors.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or [COLOR="Blue"]complicate your upgrade[/COLOR].
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

