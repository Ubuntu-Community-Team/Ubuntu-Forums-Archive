---
title: "gparted: not recognizing the whole partition size."
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by vinooj on 2007-10-07
System Information
OS: Ubuntu 6.06 LTS
CPU: AMD Dual core 2800
Kernel: 2.6.15-27-k7 with SMP

I was trying to install a second Maxtor 320GB SATA harddrive in my ubuntu box. I was planning on using 'gparted' to accomplish the task. However I found that gparted was not able to recognize my harddrive completely, eventhough fdisk did. 

Before using 'cfdisk' to partition the dirve.
-------------------------------------------------
user@my-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

After running cfdisk and creating 2 primary partision, fdisk -l shows
-----------------------------------------------------------------------------------
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19452   156248158+  83  Linux
/dev/sda2           19453       38913   156320482+  83  Linux

However in gparted( ver 0.1) and I only see 
/dev/sda1: 149.01 GB
/dev/sda2: 149.08 GB
Note: Even before I partition my drive, gparted was recognising only 299GB of 320GB.

Any recomendations?

Thanks in advance.

---

### Post by logos34 on 2007-10-07
299 GB -- That's correct. Drive manufacturers advertise hard disk capacity as 1 GB=1,000,000,000 bytes, but the [operating system]("http://www.hardwaresecrets.com/printpage/482/1") sees capacity in binary form, where 1 GB=1,073,741,824 bytes.

But why fdisk reports capacity in decimal format is beyond me.

---

### Post by vinooj on 2007-10-07
Thanks for you reply. It really helped.

---

