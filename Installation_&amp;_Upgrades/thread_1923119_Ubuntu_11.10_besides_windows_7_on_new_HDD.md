---
title: "Ubuntu 11.10 besides windows 7 on new HDD"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by LinuXofArabiA on 2012-02-10
Hello everyone, just wondering if I want to add a new hdd to already existing Windows 7 PC to install Ubuntu 11.10 and grub on it, what is the best way to proceed. I have a liveCD but cant make it work. When  i chose the new hdd for installation (sdc1) it says "No root file  system is defined. Please correct this from the partitioning menu." What  should i do to make it work_

Thanks

---

### Post by Rodney9 on 2012-02-10
If you wish to use the entire drive for Ubuntu, the easiest way, go through the set up again and follow this - 

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Rodney

---

### Post by darkod on 2012-02-10
You seem to be using the manual partitioning (which is the option I always recommend), but not specifying the mount point /.

When you start creating the partition, you select the size, whether it's primary or logical, the filesystem (usually ext4) and you also need to select the mount point.

For the system root partition the mount point is /. For swap there is no mount point, when you select swap area as filesystem type, the mount point will be greyed out.

If you want to use separate /home partition the mount point is /home.

---

### Post by Mark Phelps on 2012-02-10
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by darkod on 2012-02-10
@Mark, we are talking about installing ubuntu on second, new hdd. :)

---

