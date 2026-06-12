---
title: "Installing Ubuntu 11.10 Alongside Windows 7 64 Bit"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by grahamcrackeh on 2012-03-12
I've installed and used Ubuntu before on my laptop and ended up removing it. I've changed my mind and want it back. Last time when I installed I was given the option of installing Ubuntu alongside Windows 7, but this time It only lets me manually partition or wipe the drive completely.  How do I get Ubuntu to recognize Windows7 when installing?

---

### Post by Mark Phelps on 2012-03-12
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Suparious on 2012-03-12
Although Mark Phelps' solution is probably the "best practice", an alternative option is to use the live CD install, and/or install ubuntu permanently to a bootable USB drive that you can boot into.

---

### Post by darkod on 2012-03-12
To get more details, you can also run the boot info script from the link in my signature. You can do all that from live mode. Post the results as explained there if you want.

It might be that it doesn't see the partitions correctly, this can happen if there is an error in the partition table. Or if the disk is Dynamic in windows, as already mentioned.

The script will show many details.

---

