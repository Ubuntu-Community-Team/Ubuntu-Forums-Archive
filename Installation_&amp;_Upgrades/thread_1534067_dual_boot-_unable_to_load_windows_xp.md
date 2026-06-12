---
title: "dual boot- unable to load windows xp"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by mkshaji on 2010-07-19
Hi,
Iam new to linux, I installed ubuntu 10.04, aftert that i cluld not able to start windows xp,Please find the details about my hard disk
Please help me,
Thanks in advance
Regards
shaji


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a66c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Extended
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a911a90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       12111    56323890    f  W95 Ext'd (LBA)
/dev/sdb3   *       12112       19457    59006745    7  HPFS/NTFS
/dev/sdb5            5100       12111    56323858+   7  HPFS/NTFS
shaji@test:~$

---

### Post by celldweller1591 on 2010-07-19
Sp is not loading may be coz ur Ntldr is missing (bootmanager of xp). But i cant be sure, just goto Ubuntu terminal and type : "sudo update-grub" and restart the system and see if xp entry comes to it ? If it does, its fine. But if not, then recover ur ntldr using Xp cd. 
Put xp cd in the drive and boot from it. Open the recovery console when first screen loads up by pressing "R". then type 
    **bootcfg /rebuild **/*to rebuild your boot config*/
**    fdisk /mbr    **/*wait for it to comlete*/ 
 and restart the system. See if that works !

---

### Post by oldfred on 2010-07-19
So we know what is where run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

