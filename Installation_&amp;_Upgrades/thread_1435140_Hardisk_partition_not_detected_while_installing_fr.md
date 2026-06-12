---
title: "Hardisk partition not detected while installing fresh ubuntu after installing windows"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by papuaq on 2010-03-21
I am using Ubuntu for more then 2 years with no problem. Installed almost every release of Ubuntu from 7.04 to 9.04 with every consecutive release. Recently I got some problem with window Vista. I re-installed it. After installing Windows Vista, i tried to recover the grub of Ubuntu 9.04. But didn't succeed. (dont explored much the reason, although I have done it several times) I decided to install Ubuntu 9.10 through USB disk. The installer is not able to detect my hard disk partition. I explored lots of thread, but didn't found any useful link. After a lot of try, I decided to delete the existing Ubuntu partition.
One thing I found is the start and end sectors of the partition were overlapping. I tried to fix it with testdisk utility. Now every thing is messed up. Following is the output of fdisk -lu

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+   6  FAT16
/dev/sda2   *    21133312    80675811    29771250    7  HPFS/NTFS
/dev/sda3        80678493   119732444    19526976    c  W95 FAT32 (LBA)
/dev/sda4       119732445   312592769    96430162+   f  W95 Ext'd (LBA)
/dev/sda5       119732508   173341347    26804420   83  Linux
/dev/sda6       173341413   212395364    19526976   83  Linux
/dev/sda7       224108544   307335167    41613312    7  HPFS/NTFS
/dev/sda8       307337216   312578047     2620416    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4022 MB, 4022337536 bytes
12 heads, 4 sectors/track, 163669 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1096     7856127     3927516    b  W95 FAT32




While using the gparted from live CD of Ubuntu 9.10, Its not showing up the partitions.

---

### Post by vanadium on 2010-03-21
You have an unused gap between 160649 and 21133312. However, because you already have three primary partitions and one extended partition, there is no way that that space can be used again under the current partitioning.

It might be possible to solve this by moving partitions, then expanding the extended partition. However, it might be quicker, cleaner and more fool proof to just restarted from scratch, i.e. wipe the entire disk, have Windows installed on the desired size, and have then Ubuntu use the remaining space.

---

### Post by papuaq on 2010-03-21
Thanks for the hellp Vanadium. I am also thinking for the same.

---

### Post by raymondh on 2010-03-21
Just curious ....

- can you share the actual error message, if any?
- are you running any RAID functionality?  In  your liveCD and in live session, access a terminal and type

```
sudo apt-get remove dmraid
```

exit terminal and proceed to install.  See what happens.

I have seen installs that would not go through because of the partition limit.  However, selecting 'manual' usually overcomes that.

If you do decide to re-do everything ..... and assuming you install windows first, remember to defrag (at least 2x) before installing Ubuntu. Also note that you may run into the 'immovable files' that windows does put all over the HD.  Usually by turning off system restore or page filing will allow you shrink windows better.  Just rememeber turn them back on after.

As always, have a working/tested back-up of your files.

Raymond

---

### Post by papuaq on 2010-03-22
Hi Raymondh,
for 
> - can you share the actual error message, if any?

There is no error message. Actually Partition editior showing the whole Harddisk as a single partition. Even gparted(not sure if its used by the installer) is not showing any partition nor error. 

for > - are you running any RAID functionality? In your liveCD and in live session, access a terminal and type

I am not using any RAID functionality. Infact, I have already tried installation after removing dmraid. but no luck.  

I will keep in mind points mentioned by you while re-installing the whole system. Hopefully will be doing this in coming weekend. 
Till then, any other suggestion is welcomed. 

thanks once again.

---

