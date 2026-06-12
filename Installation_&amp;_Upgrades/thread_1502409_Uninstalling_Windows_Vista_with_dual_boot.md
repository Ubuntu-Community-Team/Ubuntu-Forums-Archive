---
title: "Uninstalling Windows Vista with dual boot"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by chip35pdx on 2010-06-05
Hi, I'm currently running Ubuntu 9.04 and Windows Vista in a dual boot system. I would like to completely erase Windows without damaging Ubuntu. I rarely use Windows and would like to clear up hard drive space. If anyone has a good way to do this please let me know. Thanks

---

### Post by kansasnoob on 2010-06-05
We should get a better look at your specific partitioning arrangement so post the output of this command:

```
sudo fdisk-l
```

---

### Post by chip35pdx on 2010-06-05
Thanks for the reply but unfortunately I'm getting an error that says the command is not found. Is there another way to retrieve the partitioning info?

---

### Post by darkod on 2010-06-05
I think there is slight spelling error:

sudo fdisk -l (small L)

---

### Post by kansasnoob on 2010-06-05
Oops, typo, I left out a <space> between fdisk and -l:

```
sudo fdisk -l
```

---

### Post by pizza-is-good on 2010-06-05
All you have to do is format the windows partition. You will loose all data on it. Once that is done, you will have an 'extra' HDD to store data in.

I think that is what everyone wants to help you with once you post the output of fdisk.

Now if you want to merge your windows space into your ubuntu partition, that will be very complicated, and you'd probably loose some of the data. I've never done it, so I won't tell you how, because I don't know a reliable way to do it.

---

### Post by chip35pdx on 2010-06-05
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69cdc6ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32664   262370272+   7  HPFS/NTFS
/dev/sda2           37649       38914    10158080    7  HPFS/NTFS
/dev/sda3           32665       37648    40033980    5  Extended
/dev/sda5           32665       37438    38347123+  83  Linux
/dev/sda6           37439       37648     1686793+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x044e6587

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       27424   220283248+   7  HPFS/NTFS
/dev/sdb2   *       27425       38440    88486020   83  Linux
/dev/sdb3           38441       38913     3799372+   5  Extended
/dev/sdb5           38441       38913     3799341   82  Linux swap / Solaris
chip@chip-desktop:~$

---

### Post by lordppm on 2010-06-05
System => Administration => Disk Utility

---

### Post by chip35pdx on 2010-06-05
Looks like I don't have a disk utility program. Would you suggest Gparted?

---

### Post by pizza-is-good on 2010-06-05
> **chip35pdx said:**
> Looks like I don't have a disk utility program. Would you suggest Gparted?

GParted will work wonders. I rarely use the disk utility. Go with GParted.

---

### Post by kansasnoob on 2010-06-05
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69cdc6ad

Device Boot Start End Blocks Id System
/dev/sda1 * 1 32664 262370272+ 7 HPFS/NTFS
/dev/sda2 37649 38914 10158080 7 HPFS/NTFS
/dev/sda3 32665 37648 40033980 5 Extended
/dev/sda5 32665 37438 38347123+ 83 Linux
/dev/sda6 37439 37648 1686793+ 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x044e6587

Device Boot Start End Blocks Id System
/dev/sdb1 1 27424 220283248+ 7 HPFS/NTFS
/dev/sdb2 * 27425 38440 88486020 83 Linux
/dev/sdb3 38441 38913 3799372+ 5 Extended
/dev/sdb5 38441 38913 3799341 82 Linux swap / Solaris

So, two Linux OS's? Do both run? What are they?

It looks like Win Vista is on sda1, but what's on sda2?

I assume the NTFS on sdb1 is just data?

That's why I asked for that output, we (and you) need to consider everything :)

As far as just removing sda1 and sda2 (if you determine that's what you want to do) that would leave no primary partition at the beginning of the disc and I've always believed that it's best to begin with at least one primary.

---

### Post by chip35pdx on 2010-06-05
Here's an attachment of my hard drive structure in GParted.

---

### Post by louieb on 2010-06-05
Glad kansasnoob asked for the fdisk listing -  you have 2 320GB hard drives - the Gparted screen shot only shows sda - click the drop-down box in upper right - select sdb to see the other one. 

Anyway looks like your booting to Ubuntu installed in partition sda5  - as long as you don't delete or move sda3, sda5 or sda6 (about 38GB total) - looks like The Ubuntu install will be safe and the computer will continue to boot to Ubuntu Linux.  

:confused: now you will just have to figure out if theres anything you want to keep  - and what your going to do with the extra 600GB + of disk space.

---

