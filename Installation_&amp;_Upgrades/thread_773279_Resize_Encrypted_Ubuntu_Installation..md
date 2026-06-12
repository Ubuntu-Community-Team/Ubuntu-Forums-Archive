---
title: "Resize Encrypted Ubuntu Installation."
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by stuman on 2008-04-28
I installed ubuntu 710 choosing the encrypted install.

This places all directories in a single file system, which is ok, but then I changed my hard drive out from 80g to 320g.  

used dd to move the system over to the the 320g.

Used gparted to increase the size of the sda2. (default partition when encrypted install).

Booted from live cd...setup software to handle encrypted drives.

Used fdisk to change sda5 to match sda2 (logical part consumes entire physical part).

Used pvresize to increase LVM Physical Volume.

So far, so good.

When I try to use lvresize, it says zero extents available.  pvdisplay shows plenty of free space.

What am I missing?

---

