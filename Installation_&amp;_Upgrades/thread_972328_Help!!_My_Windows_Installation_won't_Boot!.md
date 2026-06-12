---
title: "Help!! My Windows Installation won't Boot!"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Orange Luna on 2008-11-05
I downloaded Ubuntu 8.10 from my Windows installation.  I had previously downloaded the Gparted Live CD and decided to partition with it before installing Ubuntu.  Well the partitioning worked ok but now when I start the PC it stops before loading Windows.  I don't know what to do.  Can anyone help me?

---

### Post by zwygart on 2008-11-05
How was your computer before partitioning? One partition?
Now what is on your computer? NTFS,ext3 or NTFS, extended(ext3,swap)?

Can you boot from a linux (Ubuntu live CD)? If yes post back the output of fdisk -l

May be you have broken the bootloader of Windows. If yes the only way to repair is to get a windows CD. Not a upgrade CD but installation (XP or Vista), they have the same bootloader.

You may also try to continue and install ubuntu. If your ubuntu works it will be easier to help you (more tools and possibilities).
In this case post the content of /etc/fstab also.

We will try to help you. They are a lot of ways to boot a computer.

---

