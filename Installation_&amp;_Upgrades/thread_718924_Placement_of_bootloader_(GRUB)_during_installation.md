---
title: "Placement of bootloader (GRUB?) during installation"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by aajax on 2008-03-08
I want to install Ubuntu 7.10 on a computer that is running others systems (Windows and DOS).  This computer has 4 drives and I know where I want to put both the root file system and the swap partition.  The ext3 partition that I want to use for the root file system is the first (only) logical drive (i.e., in an extended partition) on the fourth drive.  I already have a boot manager and I don&#8217;t want to mess with either it or the master boot record (MBR).  Therefore, I want to have a boot loader installed in the boot sector of the partition which contains the system.  I&#8217;ve done precisely this in the past with Debian (both Sarge and Woody).  However, it looks like Ubuntu prefers (? mandates) the use of GRUB rather than LILO and the installation directions for Ubuntu are quite vague with respect to boot options (if there are any).

I ran the installer and chose the manual method for partitioning.  This provided an option for installing a boot loader (I assume it meant GRUB) on a drive with a number of 0.  The drive designation did not appear to refer to a partition and therefore I deduced in meant to update the MBR on the boot drive.  Therefore, I unchecked (turned off) this option since I didn&#8217;t want this installer messing with my MBR.

The installer ran successfully but when I tried to chain load the partition that Unbuntu was installed on it behaved as if there was no boot loader on that partition.

Sorry about the lengthy explanation but I thought it necessary to try and explain just what I want to do.  By the way, what I want to do worked just fine with Woody and Sarge.

I think my specific question is, &#8220;How to I direct the installer to place a boot loader on the system (i.e., root) partition?&#8221;.

---

### Post by Pumalite on 2008-03-08
In step 8, pressing 'Advanced' tab, you can change (hd0)[MBR] for /dev of your choice.
/dev/sda2 or whatever.

---

