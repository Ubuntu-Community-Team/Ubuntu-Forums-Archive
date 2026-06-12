---
title: "Dual boot and GRUB - unknown file system??"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by furghella on 2006-08-24
I have installed Windows XP and Ubuntu, each on a separate hard drive. 

Grub is installed as well and does seem to work: on start-up I can select either Ubuntu or Windows. HOWEVER, when I select Windows I get an error message, I guess grom grub, that looks as follows:

Booting Windows XP
root (hd1, 0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

For your information, here is what I get from "fdisk":

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24228   194611378+  83  Linux
/dev/sda2           24229       24321      747022+   5  Extended
/dev/sda5           24229       24321      746991   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10010    80405293+   7  HPFS/NTFS


If I enter the BIOS and start from the Windows disk everything works fine, so I guess I need to give grub additional information, but what?

---

