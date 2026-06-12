---
title: "Grub2 Error 21 on RAID 1 after installation"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by svenol on 2010-05-06
Hey all.

I'd like to set up a RAID 1 with two SATA HDs (2x Western Digital 1TB "WD10EARS").
On that raid I'd like to install several operating systems and there are no other HDs, so I have to install the bootmanager to that raid.
My raid controller is a Jmicron JMB36X (BIOS v1.03) plugged in a PCIe slot.
```
$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000066bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7180    57673318+   7  HPFS/NTFS
/dev/sda2            7181       14360    57673350    7  HPFS/NTFS
/dev/sda3           14361       19843    44042197+   5  Extended
/dev/sda5           14361       19582    41945683+  83  Linux
/dev/sda6           19583       19843     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000066bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7180    57673318+   7  HPFS/NTFS
/dev/sdb2            7181       14360    57673350    7  HPFS/NTFS
/dev/sdb3           14361       19843    44042197+   5  Extended
/dev/sdb5           14361       19582    41945683+  83  Linux
/dev/sdb6           19583       19843     2096451   82  Linux swap / Solaris
```I installed Ubuntu 9.10 (32bit) from a Live-USB stick on the Linux partition. Everything looked fine until reboot:
```
GRUB Loading stage1.5
GRUB loading, please wait...
Error 21
```What is going wrong here?

I tried to reinstall grub from the live usb stick with
```
grub-install --root-directory=/mnt /dev/mapper/jmicron_Sven5 --modules=raid
```but this was the answer:
```
grub-probe: error: no mapping exists for `jmicron_Sven5'
grub-probe: error: no mapping exists for `jmicron_Sven5'
grub-setup: error: no mapping exists for `jmicron_Sven5'
```Supergrubdisk recognizes the previously installed Ubuntu and boots it successfully.

Can anyone help me?
Thanks a lot in advance!

Sven

---

### Post by ronparent on 2010-05-06
Just a suggestion. You may have to post to the server forum for your post to be answered by a knowledgebly reader.

---

### Post by svenol on 2010-05-06
Ok, thanks.
I posted it in the server forum. What about this very thread? Can anyone delete it?

---

