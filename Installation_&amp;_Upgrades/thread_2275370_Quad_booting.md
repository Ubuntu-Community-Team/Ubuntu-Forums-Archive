---
title: "Quad booting"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Mike_Hughes on 2015-04-25
I have a box I want to set up with the following Linux distros. Ubuntu, Arch, Fedora and Ziron. How would you go about setting up to do that?

Mike

---

### Post by oldfred on 2015-04-25
Better to have more than one drive.
I have had multiple versions of Ubuntu on one drive all in 20 or 25GB / (root) partitions.
Only use  Something Else and manually choose partition. 
I think Fedora likes to default to LVM, better to just use ext4 and no separate /boot.
Better to have small system partitions, and keep all data in one larger data partition, but not sure if others set user as 1000. If not then perhaps issues unless you change user to be 1000.

Whichever system you expect to use the most should be the one in the MBR.
If UEFI they may all install separate folders in efi partition. 

I could only keep track of which system had which install in which MBR as I have several drives by running either Boot-Repair or bootinfoscript.

Start with just one. Creating partitions and leaving space for other installs and/or data partitions. Then once you have one working well and know how to reinstall its boot loader if desired then you can start on the others.

---

