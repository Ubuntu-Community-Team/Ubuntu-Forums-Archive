---
title: "Error during update 7.04-7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by wolf3pk on 2007-10-19
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://packages.freecontrib.org/plf/dists/feisty/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found Failed to fetch [http://packages.freecontrib.org/plf/dists/feisty/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found

How do I  get this fixed?
Thanks

---

### Post by Sef on 2007-10-19
I would comment out that source list.  To comment it out, just put a # infront of it.

Applications > Accessories > Terminal

Then type or copy and paste this command:

gksudo gedit /etc/apt/sources.list

Find the file and comment it out.

---

