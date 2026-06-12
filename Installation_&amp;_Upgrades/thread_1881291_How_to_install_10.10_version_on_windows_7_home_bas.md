---
title: "How to install 10.10 version on windows 7 home basic 64 bit edition?"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by linux_surender on 2011-11-15
Dear all,

I have purchased a new laptop. it have windows 7 home basic 64 bit edition pre-install. I want to just install ubuntu 10.10 over windows 7 as dual boot.

Hard disk is divided into 2 drives viz C and D.

Please help me to install ubuntu side by side windows 7.

Thanks & Regards,
Surender Singh

---

### Post by Mark Phelps on 2011-11-15
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

