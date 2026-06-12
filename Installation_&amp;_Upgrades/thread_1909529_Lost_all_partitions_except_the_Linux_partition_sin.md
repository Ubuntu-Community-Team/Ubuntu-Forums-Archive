---
title: "Lost all partitions except the Linux partition since updating"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by Temerity on 2012-01-15
Dear all,

I have had many problems following installation of updates this morning, I believe all the cosmetic problems have been solved by more recent updates. However, and critically, I cannot now access the other 2 partitions, or indeed any other remote drives from the Linux partition in the Places menu or by clicking on the desktop icon. (I have acquired however, access to Documents, Music Videos, which I do not want). The other two partitions are both run under Windows (which cannot see the Linux partition). I need to transfer files between. 

Can you help me restore access? When I click on the Computer icon which previously allowed access to everything I receive an alert with the message:

Could not display "computer:///"
The file is of an unknown type

many thanks

Mark

---

### Post by darkod on 2012-01-15
In terminal, execute:
sudo fdisk -l (small L)

and post the results.

---

### Post by Temerity on 2012-01-16
> **darkod said:**
> In terminal, execute:
sudo fdisk -l (small L)

and post the results.
It returns

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      369494      184716   de  Dell Utility
/dev/sda2          370688    31827967    15728640    7  HPFS/NTFS/exFAT
/dev/sda3   *    31827968   421256429   194714231    7  HPFS/NTFS/exFAT
/dev/sda4       421256430   488392064    33567817+   f  W95 Ext'd (LBA)
/dev/sda5       421256493   482480144    30611826   83  Linux
/dev/sda6       482480208   488392064     2955928+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2d9712e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   488394751   244196352    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976751999   488375968+   c  W95 FAT32 (LBA)

I am interested to mount sda4 sdb1 and sdc1 on boot - as is the current configuration: there is a further external drive which Ubuntu should fund (as well as generally, be responsive to USB keys etc) but doesn't. However I am not  connected to that drive right now.

thank you for your help

Mark

---

### Post by Mark Phelps on 2012-01-16
You can't mount /sda4 as that is an Extended partition and is just a container for other partitions.  /sda5 should already be mounted when you're in Ubuntu.

As to mounting the two NTFS partitions, you should see them listed under the "home" icon in the launch panel on the left.

If they will not mount when you click the appropriate icon, they could have filesystem problems.  Also, if you're running Ubuntu 11.10, you likely have ntfsprogs installed by default.  If so, remove that and install ntfs-3g in its place.  Once you do that, you will likely be able to mount the two NTFS partitions (after rebooting).

---

### Post by Temerity on 2012-01-17
Didn't work I'm afraid. I should perhaps say again that what has happened is I have lost the capability to automatically mount any and all drives, including external drives USB sticks etc.. since the last updates were applied. 

Mark

---

