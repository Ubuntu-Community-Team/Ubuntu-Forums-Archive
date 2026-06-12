---
title: "I Can't Upgrade!"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by bswalsh on 2007-10-19
So far, every time I try to upgrade I get the following warning:

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz) 302 Found

Anyone have an idea what's wrong? Thanks so much in advance for your help.

---

### Post by lalodb on 2007-10-19
same 302 error, but different packages / repos

I downloaded the alternate cd and upgraded from cd


maybe not the best solution but worked for me...

:)

---

### Post by bswalsh on 2007-10-19
My hope is that it's just a network traffic issue. I hope I don't need the CD, my burner is dead.

---

### Post by rhankins on 2007-10-19
Got the same problem on a dual boot laptop.   Here's my errors:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

The desktop that I have with only Ubuntu went fine.  Took a long time, but it at least upgraded.

It appears that my previous attempts left me midway between 7.04 and 7.10.

Any help is greatly appreciated.

---

### Post by marshall.robert on 2007-10-19
im getting the same

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

wierd because the boot i made up from cli to gui on the same machine (desktop) works fine, and the boot on my craptop i also built up from cli to gui complaints i dont have (K/X)ubuntu-desktop installed to see what version i have (also not installed on my desktop), but thats for another day.

but if anyone knows why, or how to get round this (or both) then please please say

-rob

---

### Post by marshall.robert on 2007-10-21
since noone knows, may as well download the alternate cd, since its a smaller download and can use a dl manager too.

---

