---
title: "Minimum disk size for automatic partitioning?"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by CraigThomas on 2010-12-23
A bit of background:
I want to create several virtual machines based on a minimal (no GUI) Ubuntu installation.  I'm using VirtualBox (on Windows 7), the VMs are being created with 256MB RAM and using the Ubuntu Minimal CD Image ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

The issue:
Because I want 4-5 of these virtual machines I want to use minimal disk space for storage too, which means restricting the virtual hard disk size for each.  My first attempt was to limit it to 300MB, but when I got to the partitioning section of the installer it would not allow me to do automatic partitioning and forced me to do manual partitioning, it did moan about the size of the disk.  So I started again with a 1GB virtual hard disk, this time the installer was quite happy to do the automatic partitioning.  My question is how small can I make my virtual hard disk without having to do manual partitioning?

Ps. I don't have a problem with doing the partitioning manually but for easiness I just want to do it automatically and find it strange the acceptable size isn't mentioned anywhere (that I could find).

Craig

---

### Post by CraigThomas on 2010-12-26
Is the partitioning section of the install an actual application that I can look at to find more details?  Is it or does it use gparted?

---

