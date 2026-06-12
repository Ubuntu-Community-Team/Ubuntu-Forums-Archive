---
title: "Trying to upgrade, but can't find:"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by eliotc on 2008-01-29
Going from Feisty to Gutsy, each time I try I am told that system can't find the following files - same thing when i try and update sources, any ideas? computer is a samsung laptop something or other running some microchips 


[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found

---

### Post by Pumalite on 2008-01-29
To uypgrade you first have to comment out (put # in front) all lines that belong to third parties in your sources.list, including Medibuntu, Automatix if you have it and others. Backup your file first.

---

