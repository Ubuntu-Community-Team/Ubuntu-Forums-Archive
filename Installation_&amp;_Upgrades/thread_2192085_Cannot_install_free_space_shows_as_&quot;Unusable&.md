---
title: "Cannot install: free space shows as &quot;Unusable&quot;"
date: 2013-12-05
forum: Installation &amp; Upgrades
---

### Post by ericg2 on 2013-12-05
Hi, I'm trying to install 13.10 as a dual OS with Win 7.  In following some advice, I shrank my 'a' partition to create another partition that I wanted to install ubuntu onto.  But I had problems during the install, namely that the aforementioned free space is shown as unusable.  

Here is a crappy screenshot: [http://imgur.com/PG04NpU](http://imgur.com/PG04NpU)

I've researched this a little and believe this is happening because only 4 partitions are allowed and my computer already had 4 before I created another one.

Oh, and I ran a boot info summary that can be found here: [http://paste.ubuntu.com/6527600/](http://paste.ubuntu.com/6527600/)

Question is, what now?  Thanks for your help.

---

### Post by ericg2 on 2013-12-05
Alright, good people.  I've got to get to bed, but I'll check this thread first thing in the morning.  Again, thanks for your help.

---

### Post by fantab on 2013-12-06
```
parted -l:

Model: ATA INTEL SSDSC2BF18 (scsi)
Disk /dev/sda: 180GB
Sector size (logical/physical): 512B/512B
Partition Table: **msdos**

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1574MB  1573MB  primary  ntfs         boot
2      1574MB  81.1GB  79.5GB  primary  ntfs
3      158GB   173GB   14.7GB  primary  ntfs
4      173GB   180GB   7516MB  primary


fdisk -l:

Disk /dev/sda: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders, total 351651888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24c323d7

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sda2         3074048   158410751    77668352    7  HPFS/NTFS/exFAT
/dev/sda3       308297728   336969727    14336000    7  HPFS/NTFS/exFAT
/dev/sda4       336969728   351649791     7340032   84  OS/2 hidden C: drive

```

Yes, 'msdos/MBR' partition table has PRIMARY Partitions limited to ONLY 4. If you need more partitions then you will have to DELETE a partition and make a new EXTENDED Partition as your fourth partition.
An 'Extended Partition' is a Primary Partition which acts as a container for LOGICAL Partitions. Inside an Extended Parittion we can have more than 100 Logical Partitions.

You have to decide which Partition are you open to delete or post a screenshot of your HDD and its partitions from Windows, and we can guide you further.

---

### Post by ericg2 on 2013-12-06
Okay, here is the partitions screen from Windows.  The block of 'Unallocated' is what I created by shrinking the Windows7_OS partition.

[URL="http://imgur.com/wFpEtJs"]http://imgur.com/wFpEtJs
[/URL]

---

### Post by fantab on 2013-12-06
The 7Gb partition in the Screenshot is 'Hibernation Partition'.
The 1.46Gb partition, labelled SYSTEM DRV, is probably a drivers storage.

I'd say copying all the contents of the 1.46Gb Partition to an external device and then DELETING it will be a good idea. (But find out and confirm that it has what we think it has, drivers.) 
You can merge the 'unallocated space' of 1.46Gb with Windows C.
Do this from Windows only. And later restart Windows a couple of times.
Disable Hibernation in Windows. It can cause issues with dual-booting.

Then Boot with Ubuntu DVD/USB, and Install Ubuntu, the installer will partition the rest for you and install

To manage it manually, 'Try Ubuntu without installing", open GParted and you can convert the 'unallocated space' of 71.47Gb as EXTENDED Partition. You will still see 'unallocated space'. In this space create:
20Gb LOGICAL Ext4 / Ubuntu
48Gb Logical Ext4 /home
2Gb Logical SWAP
1.47Gb Logical NTFS SYSTEM DRV (copy the contents of deleted partition here).

---

### Post by Mark Phelps on 2013-12-06
There's every possibility that the Win7 boot loader folder and files are contained in the 7GB partition. If that is the case, deleting it will render Win7 unbootable!

You can "fix" this problem by doing the following:
1) Download and install EasyBCD from NeoSmart Techologies
2) Use the BCD Backup Repair feature, and the Change boot drive option to migrate the Win7 loader folder and files to your OS partition.

After that, you no longer need the 7GB partition for booting purposes.

However, if you want to remove that, reclaim the space, and merge that 7GB with something else, you need to do the partitioning activities either from Win7 Disk Management utility, or make a CD from the Minitool Partition Wizard Boot CD download, boot from that, and use that.

Also, it would be a good idea to use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will provide the means to repair/restore the Win7 boot loader -- should something happen to it.

---

