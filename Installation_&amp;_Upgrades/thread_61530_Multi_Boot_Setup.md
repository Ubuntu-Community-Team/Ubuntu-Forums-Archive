---
title: "Multi Boot Setup"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by menawollas on 2005-09-01
I am just about to install Ubuntu on my first hard drive, which is currently partitioned as follows.

Part
1    Primary                   30Mb    FAT (dos)
2    Primary(active)      10Gb    NTFS (winXP)
3    Logical                    20Gb    FAT32 (data)
4    Logical                    20Gb    NTFS (data)
5    Logical                    40Gb    NTFS (data)
6    Logical                    20Gb    empty (for ubuntu)
7    Logcal                     1Gb      empty (for ubuntu swap)

As indicated, I intend to install ubuntu on partitions 6/7, however what happens when I get to the LILO / Grub stage ???

My understanding is that a PC will boot from the active primary partition. Therefore does the boot manager need to be installed in partition 1? Will it effect anything on the XP partition ??

Or does it do something with the MBR, and not touch anything else? If so, if I want to delete it, how do I restore the MBR ??

Also, what are the relative advantages of LILO v Grub.

Or should I just use XOSL?

thanks

---

### Post by Lord Illidan on 2005-09-01
Grub will ask you if you want to install MBR on the primary partition, select yes, and dual-booting will be set up automatically. You can then choose between XP and Ubuntu at boot time..

No, it will not effect anything on XP's partition...

---

### Post by menawollas on 2005-09-01
Which Primary Partition ?

XP is the active one.

---

