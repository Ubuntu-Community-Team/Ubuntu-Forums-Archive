---
title: "Weird installation problem"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by Rinchwind on 2005-03-09
I'm trying to install Ubuntu on my AMD athlon 64.
I downloaded "warty-release-install-amd64.iso" using bittorrent, and verified its MD5SUM.

when I try to install it everything works perfectly until it tries to install the kernel (during the base package install), then it complain that it can't install "linux-amd64-generic" and the installation stops.

in the debug console it shows that there was an I/O error opening "dists/warty/main/binary-amd64/Packages.gz" and it can't open "dists/warty/main/binary-amd64/Packages"

a verification of the CD complains about MD5SUM failure for these files.
However, when I try to read them in windows they work fine and their MD5SUM checks out fine.

I tried to burn another CD, but I still got the same problem.

Anyone has any idea on how to solve this problem?

Rinchwind.

---

### Post by hal8000 on 2005-03-09
The only thing I can suggest is next time you create the Ubuntu CD, burn it at a lower speed. If you have a 40x writer, set it to burn at 8x, don't know if it will help, but it does suggest this somewhere on the Ubuntu help page.

---

