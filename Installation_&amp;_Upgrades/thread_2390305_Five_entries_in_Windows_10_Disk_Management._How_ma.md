---
title: "Five entries in Windows 10 Disk Management. How many are partitions?"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by Randy M on 2018-04-27
I just bought a new laptop (the old one is dying bit by bit) and I want to dual boot Windows 10 and Ubuntu 16.04. When I run Disk Management to shrink the primary drive (C: ), it shows 5 entries.
 
(Disk 0 Partition 1)
(Disk 0 Partition 4)
Recovery (D: )
Recovery (D: )  NTFS
Windows (C: )   NTFS

All are Basic and Simple.

I remember from days gone by that there's a limit on the number of partitions that can exist and still install Ubuntu. How many of these are actual partitions, and can I safely shrink C: and proceed with the install. I've created the recovery media on a thumb drive, just in case.

The laptop is an HP with an Intel Core i3-7100U @ 2.4G with 6 Gig of Ram.

Thanks for any and all help.

---

### Post by Mark Phelps on 2018-04-27
My own experience with recent HP systems is that if you touch the partitioning, then Recovery simply does not work, anymore.  I had to use a recovery USB stick after I had done that -- to reset the laptop.

My own choice, as I have done with my systems, is to do the following:
1: Forget about using the HP built-in recovery process or the HP Recovery media (disks or USB stick)
2) Shrink the OS partition to the size you want
3) Download and install Macrium Reflect Free
4) Use MR free to do a recovery image backup to USB stick
5) Use the MR option to create Rescue Media in the form of a USB stick -- you will need this to boot from if the boot loader on the drive ever gets corrupted

Once you have those, you no longer need the Recovery partitions, can remove them, and reuse the space.

---

### Post by oldfred on 2018-04-27
it was the old MBR(msdos) partitioning that had a 4 primary partition limit, but one primary could be an extended partition and then unlimited number of logical partitions.

With UEFI and gpt partitioning you have a soft limit of 128 partitions. Only one type so in effect all are primary. And as soft limit user can reconfigure partition table to add more partitions (have not seen, nor know details).

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

