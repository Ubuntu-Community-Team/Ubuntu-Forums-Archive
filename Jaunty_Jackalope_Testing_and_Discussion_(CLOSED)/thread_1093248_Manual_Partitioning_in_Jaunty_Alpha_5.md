---
title: "Manual Partitioning in Jaunty Alpha 5"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ukkuku3d on 2009-03-11
Hi all,
yesterday I've tried to install the Alpha 5 of Jaunty, but I was stopped very early... at the moment of partitioning the HD:

I have currently 3 used partitions (swap, "/" with Intrepid and "/home") and an free partition, all formated with ext3.
So my plan is to install Jaunty at the free partition and reformat it during installation with ext4. From that moment on I should be able to boot Jaunty or Intrepid if it is needed and use the same user-data on the old ext3 /home partition.

But what the Jaunty installation do is something different. It offers only to install on /dev/sda as one partition, even if I select "manual partitioning" it still don't show the exisitng partitions and offers to create a new partition table by destroying all exisiting partititons. 
From within the running Jaunty live system I even cannot look to my harddisk, even not with GParted (which is currently not installable) or parted (Which shows an error on "print all" command).

What can be wrong here, my Intrepid is basically running fine???

Thanks a lot
  Achim

---

### Post by thtrgremlin on 2009-03-11
From the intrepid install and from the Jaunty Live CD, can you give the output of ```
sudo fdisk -l
```

They should be the same. Also, did you get the alpha 5 release, or the alpha 5 daily? You can run ```
sudo apt-get update && sudo apt-get dist-upgrade
``` before installing. If there was a bug with gparted, I would bet it has since been resolved.

Can you mount the partitions in the live session?

If you are still encountering the bug after updating the CD, file a bug report: [https://launchpad.net/ubuntu/jaunty/+source/gparted](https://launchpad.net/ubuntu/jaunty/+source/gparted)

If you havn't gotten it installed, there are other ways of getting jaunty installed, if you would like some help using what you have.

---

### Post by Neo_The_User on 2009-03-11
Please tell / ask one of the Ubuntu forum staff and or admins to move this to Jaunty discussion.

---

### Post by ukkuku3d on 2009-03-12
I don't see any difference of the both fdisk:

In Jauntey Alpha 5:
```

Disk /dev/sda: 36.7 GB, 36791903232 bytes
240 heads, 63 sectors/track, 4752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc84ac84a

   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1            1450        5168    28115640    5  Extended
/dev/sda2   *         154         846     5239080   83  Linux
/dev/sda3             847        1449     4558680   83  Linux
/dev/sda4               1         153     1156648+  82  Linux swap / Solaris
 /dev/sda5            1451        5168    28108080   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2063 MB, 2063302656 bytes
2 heads, 32 sectors/track, 62967 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
 Disk identifier: 0x0001ace3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       62967     2014912    6  FAT16

```

In Intrepid:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc84ac84a

  Device Boot Start End Blocks Id System
/dev/sda1 1450 5168 28115640 5 Extended
/dev/sda2 * 154 846 5239080 83 Linux
/dev/sda3 847 1449 4558680 83 Linux
/dev/sda4 1 153 1156648+ 82 Linux swap / Solaris
/dev/sda5 1451 5168 28108080 83 Linux

Partition table entries are not in disk order

```

I tried the Alpha 5 release,not the daily

I tried the update and dist-upgrade, but it failed with "out of memory" error message - I guess on the RAM-disk.
So still no chance to install gparted or use parted.

I was successful in mounting the devices in Jauntey, both a manual with the "mount" command and an automatic from inside dolphin worked perfect. Afterwords I'm able  to access my harddisk from within dolphin.
But even in mounted state, there is wrong behaviour during the installation. Now from within the "prepare partitions" dialoge I see nothing, even not the /dev/sda anymore. And a try to add a new partition or partiotion-table from within this dialoge also don't respond.

So I guess there is really a bug somewhere, but I can't understand how all the others install and test it. This problem hinders any installation (in the way I know).
  Achim

---

### Post by ukkuku3d on 2009-03-14
It simply works with the brand new Jaunty Alpha 6
  thanks to all guys working on that

---

