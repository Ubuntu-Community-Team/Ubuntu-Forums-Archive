---
title: "Lucid CD installation didn't overwrite past one"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by motorhead_1 on 2010-05-23
Hi, 
I used to have a 2 partitions disk (3 if we count the swap) with win XP and Karmic 9.10. Since I had problems upgrading from Karmic to Lucid I decided to install again Lucid from the cd leaving the XP partition unchanged. 
Now I think that new Lucid didn't install over the past Lucid (after upgrade) but it has created a new partition, am I right?

```
daitarn@daitarn-laptop:~$ sudo fdisk -l
[sudo] password for daitarn: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf6d9322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1890    15181393+   7  HPFS/NTFS
/dev/sda2            1891        5992    32943769+  83  Linux
/dev/sda3            5992        9729    30022241+   5  Extended
/dev/sda5            9548        9729     1461883+  82  Linux swap / Solaris
/dev/sda6            5992        9395    27335680   83  Linux
/dev/sda7            9395        9547     1222656   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
```Is there a way to unify all the Linux partitions??

---

### Post by darkod on 2010-05-23
You are right. For your own protection linux doesn't assume that you want it to overwrite another OS, unless you specifically tell it to.
Since you didn't use manual partitioning to point it to install on the existing root partition, it created a new installation.

You can't unify them as far as I know.

But since the new install is still new, and if you don't have important data to get out of your failed Karmic upgrade, just boot into live mode, open Gparted and delete all linux partitions going back to front, all except /dev/sda1 which is your XP partition.

Then just start the installer and tell it to use Use Largest Available Free space option. That will install it into the empty space you created with deleting the partitions.

Or use manual partitioning option to set the partition sizes exactly as you want.

---

### Post by motorhead_1 on 2010-05-23
Thanks! job done.

```
[U]
daitarn@daitarn-laptop:~$ sudo fdisk -l
[sudo] password for daitarn: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf6d9322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1890    15181393+   7  HPFS/NTFS
/dev/sda2            1891        9730    62968833    5  Extended
/dev/sda5            1891        9548    61506560   83  Linux
/dev/sda6            9548        9730     1461248   82  Linux swap / Solaris
daitarn@daitarn-laptop:~$ [/U]
```I guess it's now the way it should be, though I don't know what is that 'extented' partition.

---

