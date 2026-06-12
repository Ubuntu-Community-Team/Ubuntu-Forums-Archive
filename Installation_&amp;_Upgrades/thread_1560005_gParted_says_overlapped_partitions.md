---
title: "gParted says overlapped partitions"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by sdhanush1 on 2010-08-24
Hi

I Have The Ubuntu 10.4 cd and tried to install it on my pc with xp

but in the live cd gparted says my hard disk as unallocated space and overlapped partions

please help me wat to do :(

and i dont want to lose data on any of my hard disk

---

### Post by sdhanush1 on 2010-08-24
output of sudo sfdisk -d
& of sudo fdisk -lu

```
ubuntu@ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 23856527, size= 48452038, Id= 7, bootable
/dev/sda2 : start= 84887463, size= 71135817, Id= 7
/dev/sda3 : start=    16126, size= 84871334, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=    16189, size= 22523006, Id= 7
/dev/sda6 : start= 22539258, size=  1317267, Id= 7
/dev/sda7 : start= 72308628, size= 10490382, Id=83
/dev/sda8 : start= 82799073, size=  2088387, Id=82
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb93db93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    23856527    72308564    24226019    7  HPFS/NTFS
/dev/sda2        84887463   156023279    35567908+   7  HPFS/NTFS
/dev/sda3           16126    84887459    42435667    5  Extended
/dev/sda5           16189    22539194    11261503    7  HPFS/NTFS
/dev/sda6        22539258    23856524      658633+   7  HPFS/NTFS
/dev/sda7        72308628    82799009     5245191   83  Linux
/dev/sda8        82799073    84887459     1044193+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by srs5694 on 2010-08-24
That is one weird layout! The problem boils down to /dev/sda1, which is defined as a primary partition in the middle of the extended partition. If /dev/sda1 is *NOT* your Windows boot partition, then fixing the problem should be fairly straightforward, but it requires using text-mode tools that newbies are likely to find intimidating. Basically, you need to edit the output of "sfdisk -d" to change /dev/sda1 into a logical partition -- /dev/sda9 is easy, or you could sort the logical partition numbers to match disk order. You'll then pass the results back, as in "sfdisk < parts.txt", if you store the data in parts.txt. This process is similar to the one I describe on my [Missing Partitions in GParted](http://nessus.rodsbooks.com/missing-parts/index.html) Web page, but it's simpler, since you don't need to change the extended partition's size.

Your /dev/sda1 has its boot flag set, though, which suggests it *is* your Windows boot partition. Solving this problem will be a bit trickier, but the basic outline is the same: Save the sfdisk output to a file, edit it, and use sfdisk to change it on the disk. In this case, though, you'll need to convert /dev/sda5 and /dev/sda6 into primary partitions (give them the numbers /dev/sda2 and /dev/sda4), convert /dev/sda2 into a logical partition (give it the number /dev/sda5), renumber /dev/sda7 and /dev/sda8 to /dev/sda6 and /dev/sda7, and adjust the start point and size of the extended partition to match these changes. This is a tricky set of changes to implement without making a mistake.

An alternative, albeit one I'm slightly reluctant to suggest, is to use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) utility to make the changes. GPT fdisk is designed to edit GPT disks, not MBR disks such as you've got, but it can convert from MBR to GPT and from GPT to MBR. It's not very fussy about errors like you've got when reading MBR, so it will *probably* read the partition table and convert it to GPT (internally) just fine. You can use it like fdisk in many ways, so you can check that it's read the partitions by typing "p"; all but the extended partition should show up. You'd then type "r" to go to the recovery & transformation menu and use the "g" option to convert back to MBR form. You'll see a summary display, which will enable you to change the primary/logical status of each partition, set its active (boot) flag, change its type code, and so on. When you're done, it'll save your changes. It may then be necessary to re-install your boot loader. Since the program does the math of figuring out start and end points, you won't make a mistake on that score; however, GPT fdisk wasn't designed for this task, so it's conceivable that it will do something unexpected.

However you fix this, I strongly recommend you back up your partition table first. The output you've posted (particularly the sfdisk output) can serve this purpose.

---

### Post by sdhanush1 on 2010-08-24
> **srs5694 said:**
> That is one weird layout! The problem boils down to /dev/sda1, which is defined as a primary partition in the middle of the extended partition. If /dev/sda1 is *NOT* your Windows boot partition, then fixing the problem should be fairly straightforward, but it requires using text-mode tools that newbies are likely to find intimidating. Basically, you need to edit the output of "sfdisk -d" to change /dev/sda1 into a logical partition -- /dev/sda9 is easy, or you could sort the logical partition numbers to match disk order. You'll then pass the results back, as in "sfdisk < parts.txt", if you store the data in parts.txt. This process is similar to the one I describe on my [Missing Partitions in GParted](http://nessus.rodsbooks.com/missing-parts/index.html) Web page, but it's simpler, since you don't need to change the extended partition's size.

Your /dev/sda1 has its boot flag set, though, which suggests it *is* your Windows boot partition. Solving this problem will be a bit trickier, but the basic outline is the same: Save the sfdisk output to a file, edit it, and use sfdisk to change it on the disk. In this case, though, you'll need to convert /dev/sda5 and /dev/sda6 into primary partitions (give them the numbers /dev/sda2 and /dev/sda4), convert /dev/sda2 into a logical partition (give it the number /dev/sda5), renumber /dev/sda7 and /dev/sda8 to /dev/sda6 and /dev/sda7, and adjust the start point and size of the extended partition to match these changes. This is a tricky set of changes to implement without making a mistake.

An alternative, albeit one I'm slightly reluctant to suggest, is to use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) utility to make the changes. GPT fdisk is designed to edit GPT disks, not MBR disks such as you've got, but it can convert from MBR to GPT and from GPT to MBR. It's not very fussy about errors like you've got when reading MBR, so it will *probably* read the partition table and convert it to GPT (internally) just fine. You can use it like fdisk in many ways, so you can check that it's read the partitions by typing "p"; all but the extended partition should show up. You'd then type "r" to go to the recovery & transformation menu and use the "g" option to convert back to MBR form. You'll see a summary display, which will enable you to change the primary/logical status of each partition, set its active (boot) flag, change its type code, and so on. When you're done, it'll save your changes. It may then be necessary to re-install your boot loader. Since the program does the math of figuring out start and end points, you won't make a mistake on that score; however, GPT fdisk wasn't designed for this task, so it's conceivable that it will do something unexpected.

However you fix this, I strongly recommend you back up your partition table first. The output you've posted (particularly the sfdisk output) can serve this purpose.

actually my windows is on a extended drive,but the boot files are on the first primary partition 

can i just remove the overlapping in a simple method without losing my data?

and i am complete newbie to linux

---

### Post by srs5694 on 2010-08-24
> can i just remove the overlapping in a simple method without losing my data?

The short answer is: no, or at least not that I know of.

The long answer is: The problem isn't even remotely Linux-specific. In the Master Boot Record (MBR) partitioning system that you're using, there are three types of partitions: primary, extended, and logical. You can define up to four primary partitions. Because it became clear many years ago that four was too small a number for this function, a hack was developed: One primary partition could serve as a placeholder for additional partitions. This placeholder primary partition became known as an extended partition, and the partitions it contains are known as logical partitions. Because of this setup, *all of your logical partitions must be contiguous.* This restriction refers to the partition start and end points, not the partition numbers. If you examine your partition layout, you'll see that /dev/sda1, a primary partition, lies in the middle of your extended partition, between the logical partitions /dev/sda6 and /dev/sda7. This is simply illegal in the MBR scheme. It can be fixed either by turning /dev/sda1 into a logical partition (which will render Windows unbootable, if I understand your setup correctly) or by converting /dev/sda5 and /dev/sda6 into primary partitions. The trouble is that most partitioning tools don't make such transformations easy. In this case, a further complication is that some tools, including the Ubuntu installer, will refuse to work with the disk because it's damaged (which it most emphatically *is*.)

That said, it's conceivable that there's a disk partitioner or disk repair utility that will fix your disk in a semi-automatic way. If such a utility exists, I don't know what it is. The best I know of on that score is GPT fdisk; I described how to use it to fix your disk in my previous post. Note that *any* attempt to repair this problem is potentially risky; with corrupt data structures, even an otherwise reliable program might do something bad. With a backup, such as the sfdisk output you posted, you should be able to recover from problems.

---

