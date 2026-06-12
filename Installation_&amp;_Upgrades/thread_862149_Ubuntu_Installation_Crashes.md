---
title: "Ubuntu Installation Crashes"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by LesFromIL on 2008-07-17
I am trying to install 8.04 on a desktop PC (2.6 GHZ P4, 2MB RAM, Gigabyte MB). I boot to the Live CD (which was media checked), click on Install. The install starts and continues almost to the end and then it simply crashes back to the Live CD Desktop.

Funny thing is, that I have installed Ubuntu on this machine before with this same hardware configuration with the possible exception of a larger hard drive and more memory.

Here's the kicker. I happen to have an extra 160 GB SATA drive lying around, so I installed it as the 2nd hard drive, booted the SAME Live CD as before and the installation works fine!

My original installation attempt is to a 500 GB SATA drive (Seagate), which dual boots with XP.

I manage the partitioning and mount points myself. I have a partition for / (root), a separate partition for /home and a swap partition.

How can I find out what is causing the installation on the "dual-boot" drive to crash?

I have installed Ubuntu many times before on this and other machines without any problem and am fairly competent with this kind of stuff.

Any ideas on how to proceed?

I do not want to keep both drives in the system as I have plans for the drive I temporarily installed (which now contains the working copy of Ubuntu).

Thanks for any help.

Les

---

### Post by wpshooter on 2008-07-17
Have you tried doing scandisk and defrag on the drive prior to doing the Ubuntu installation attempt ?

---

### Post by LesFromIL on 2008-07-17
Ran chkdsk on all partitions and defragged all partitions.

Rebooted to Ubuntu Cd, install started and crashed just like before.

It gets to "Checking for packages to remove..." and then crashes; eventually the LiveCD desktop re-appears,

---

