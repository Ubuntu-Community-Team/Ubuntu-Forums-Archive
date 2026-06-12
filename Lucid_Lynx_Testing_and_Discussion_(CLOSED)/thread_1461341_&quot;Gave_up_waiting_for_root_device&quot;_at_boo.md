---
title: "&quot;Gave up waiting for root device&quot; at boot"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by elegant55 on 2010-04-24
Hi I am running lucid with latest update.
This problem is similar as described in 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/325856](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/325856)

The boot freezes before the splash shows up. The message will shows up if I hit enter at keyboard or power button of the computer.

It doesn't happen at very boot just from time to time.

I dual boot Lucid with Win7.

Here is my fstab 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4572129f-9090-4e42-85bb-f683f8672ad6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=b21d6e8b-5284-43dd-bfe7-dbc490f8b3ec /home           ext4    defaults        0       2
# /space was on /dev/sda5 during installation
UUID=b7a431b0-d5e7-4cf0-a24c-abe5bcd69a1b /space          ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=dbf5dbd5-20f0-4d8d-a393-bf8210cb631a none            swap    sw              0       0

and fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25510   204902400    7  HPFS/NTFS
/dev/sda2           25510       63754   307200000    7  HPFS/NTFS
/dev/sda3           63755      121602   464657820+   f  W95 Ext'd (LBA)
/dev/sda5           63755       83335   157284351   83  Linux
/dev/sda6          120558      121602     8387584   82  Linux swap / Solaris
/dev/sda7           83336       88806    43945776   83  Linux
/dev/sda8           88807      120557   255038464   83  Linux

Is it a known bug or anyone has seen same problem?

---

