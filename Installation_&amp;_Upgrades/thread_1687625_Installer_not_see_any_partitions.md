---
title: "Installer not see any partitions"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by MVG-V70 on 2011-02-14
I try to install Ubuntu 10.10 on HP notebook G62 (Intel-i3, 64-bit)
It have a 320GB hdd with my laptop which now consists of:

1) SYSTEM volume
2) (C: ) volume with windows 7
3) RECOVERY (D: ) volume
4) HP_TOOLS volume

1 to 4 are originally there.

And now I shrink (C: ) by 50GB to get a unallocated space in which I decide to install ubuntu:
First I try to shrink by Windows7 tools, but installer did not see unallocated space (but shows list of my volumes).
Then I install Acronis disk director and made 50GB unallocated space by Acronis.
**After this Ubuntu installer does not see any volumes on my HDD** :(
Windows7 boots nad works normally.

I try to restore ALL from image by HP TOOLS but without result - installer doesn't see any volumes.
I try boot from CD, remove *dmraid* and all *raid* package and try run istaller - no result.

---

### Post by Kirboosy on 2011-02-14
Maybe you need to boot GParted and try tweaking the drive from there. I'm not familiar with Acronis but it sounds like its messing you up.

Have you had ubuntu installed before on this laptop?

---

### Post by Mark Phelps on 2011-02-14
If you did not remove any partitions, then you can not install to another one because 4 primary partitions is the maximum.

If you are running Windows 7 and your FORCE the installer to create another partition, you are going to hose up your Win7 install because it will then convert your partitions to Dynamic Disks -- something you do NOT want to do.

---

### Post by MVG-V70 on 2011-02-14
> **Caboose885 said:**
> Maybe you need to boot GParted and try tweaking the drive from there. 
I try boot Ubuntu from CD and run GParted: it also not see any volumes.
> **Caboose885 said:**
> Have you had ubuntu installed before on this laptop?
This is a new laptop with preinstalled Windows7

---

### Post by Kirboosy on 2011-02-14
The only problem with that is I'm not sure which partition he should remove. If he had an extended partition he would be fine but I'm pretty sure there is no way to convert without formatting the partition.

---

### Post by MVG-V70 on 2011-02-14
> **Mark Phelps said:**
> If you did not remove any partitions, then you can not install to another one because 4 primary partitions is the maximum.
My problem that after Acronis ubuntu-installer could not see ANY partitions.

---

### Post by oldfred on 2011-02-14
You have to delete one partition to be able to create the extended partition to hold all the logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Kirboosy on 2011-02-14
He can't even see the partitions to delete them. Thats a major stopping point and I'm not sure how to fix it.


Maybe try [gParted Live]("http://gparted.sourceforge.net/"). I know Ubuntu comes with gParted but maybe the live CD will have new features that the Ubuntu one doesn't have

---

### Post by Quackers on 2011-02-14
The partition could be deleted from within Windows disk management utility.
Other people in your position have deleted the HP TOOLS partition, then resized the C: partition then created an extended partiton in that free space (but not with the Windows Disk Management utility).

---

### Post by MVG-V70 on 2011-02-17
Here is my screenshots

---

### Post by oldfred on 2011-02-17
Sometimes it is just NTFS needing chkdsk and other times it is this:

[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)
Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

Post this so we can see if it is an overlapping partition issue.

```
sudo fdisk -lu
```

---

### Post by MVG-V70 on 2011-02-19
> **oldfred said:**
> [http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
This is good advice! Thank You
I think this is my case. I will try it...

---

### Post by MVG-V70 on 2011-02-19
```
/dev/sda1 : start=     2048, size=   407552, Id= 7, bootable
/dev/sda2 : start=   409600, size=471705600, Id= 7
/dev/sda3 : start=594995200, size= 29949365, Id= 7
/dev/sda4 : start=624928768, size=   211632, Id= c
```

---

### Post by MVG-V70 on 2011-02-19
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7f66b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   472115199   235852800    7  HPFS/NTFS
/dev/sda3       594995200   624944564    14974682+   7  HPFS/NTFS
/dev/sda4       624928768   625140399      105816    c  W95 FAT32 (LBA)

```

---

### Post by oldfred on 2011-02-20
You do have overlapping partitions. sda3 end is larger than sda4's start.
624944564 > 624928768

See post #11.

---

