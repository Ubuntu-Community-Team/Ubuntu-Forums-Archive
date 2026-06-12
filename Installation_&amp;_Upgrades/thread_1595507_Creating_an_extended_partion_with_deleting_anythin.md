---
title: "Creating an extended partion with deleting anything?"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by connel on 2010-10-13
Hi, I have just purchased a HP netbook. I wish to install UNE on it but it already has 4 primary partitions. Is there any way I can put these in an extended partition without deleting them? Thanks

---

### Post by VMC on 2010-10-13
> **connel said:**
> Hi, I have just purchased a HP netbook. I wish to install UNE on it but it already has 4 primary partitions. Is there any way I can put these in an extended partition without deleting them? Thanks

Not without backing one of them up first. Your allowed only 4 primary partitions including extended.

You could copy all the file from one partition to another or to an outside source (usb).

Give us the output of your partitions now so we can see what you have. From a terminal type the following:

```
sudo fdisk -l
```

---

### Post by connel on 2010-10-13
Here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e35ee32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       12774   102400000    7  HPFS/NTFS
/dev/sda3           28834       30389    12486656    7  HPFS/NTFS
/dev/sda4           30389       30402      105656    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1010 MB, 1010826752 bytes
32 heads, 61 sectors/track, 1011 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ab00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1011      986705+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

There is a small partition called HP_Tools that is only 100MB and I have backed it up. I noticed it had a "flag" of LBA. Is it safe to delete this and recreate it inside an extended partition?

---

### Post by srs5694 on 2010-10-13
One of those NTFS partitions (probably /dev/sda3) most likely contains an on-disk equivalent of your Windows installation DVDs. There should be a Windows utility that came with the system that will enable you to create physical DVDs (which are better than an on-disk system in case of a disk hardware failure anyhow). I recommend you run it (twice, for safety). Thereafter, you should be able to safely remove the partition in question, resize and remove partitions as necessary, create a new extended partition, and install Linux in logical partitions inside the extended partition.

---

### Post by connel on 2010-10-13
There is an application in my windows install that allows me to burn my recovery partition but my netbook doesn't have a dvd drive. Do you know if it is possible to get a virtual dvd drive that burns stuff to an image? If not I'll back it up on my usb hdd :)

---

### Post by srs5694 on 2010-10-13
Since the netbook doesn't have a DVD drive, DVD backups won't do you a lot of good in an emergency. Thus, I'll revise my advice and suggest that you back up the small FAT partition, delete it, adjust your partitions including making a new version of that partition as a logical partition, and then restore the FAT partition to its new logical version. It's also possible you don't want whatever's on there (probably some minor utilities provided by the computer's manufacturer), in which case you can just ditch it entirely.

Alternatively, perhaps there's a way you can create a USB flash drive with the contents of the "installation" partition. Maybe you could ask about that on a Windows forum, if nobody here has suggestions.

---

### Post by connel on 2010-10-14
Ok, think I'll just delete the small FAT partition and restore in a logical partition.

Thanks for your help, really appreciate it :D

---

