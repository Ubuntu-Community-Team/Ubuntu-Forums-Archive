---
title: "overlapped hard disk partitions"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by nvadiga on 2011-01-21
Hi,

I read many threads regarding `gparted` not showing up hard disk partitions. Also read the advice not to change partition table according to solution to given to others. So posting my partition table here... 

```
sudo parted /dev/sda print
Error: Can't have overlapping partitions.
```

```

mint@mint ~ $ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b05fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625137344   312568641    5  Extended
/dev/sda2       152072192   152276991      102400    7  HPFS/NTFS
/dev/sda3       152276992   193032191    20377600    7  HPFS/NTFS
/dev/sda4   *   362860544   363065343      102400    7  HPFS/NTFS
/dev/sda5             126   143203409    71601642   83  Linux
/dev/sda6       143203473   152071289     4433908+  82  Linux swap / Solaris
/dev/sda7       193037103   362860154    84911526    b  W95 FAT32
/dev/sda8       363069063   445209344    41070141   83  Linux
/dev/sda9       445209408   488633039    21711816    b  W95 FAT32
/dev/sda10      488633103   510031619    10699258+  83  Linux
/dev/sda11      510031683   625137344    57552831    b  W95 FAT32

```

I guess entire disk is taken as extended partition and primary partition(/dev/sda4) lying within this. So this is may be similar to thread [http://ww.ubuntuforums.org/showthread.php?t=1560005]("http://ww.ubuntuforums.org/showthread.php?t=1560005"). Correct me if I am wrong and also advice me on how to proceed further.

---

### Post by coffeecat on 2011-01-21
> **nvadiga said:**
> I guess entire disk is taken as extended partition and primary partition(/dev/sda4) lying within this.

I'm sorry to say this, but the situation is far, far worse. You do not have just one primary partition "within" the extended partition (an impossibility), you have three: sda2, sda3 and sda4. Even worse still, if you look at the start and end sector figures in your fdisk output, your primary partitions are situated mingled amongst the logical partitions. They go [COLOR=Red]sda5[/COLOR] - [COLOR=Red]sda6[/COLOR] - [COLOR=Blue]sda2[/COLOR] - [COLOR=Blue]sda3 [/COLOR]- [COLOR=Red]sda7 [/COLOR]- [COLOR=Blue]sda4[/COLOR] - [COLOR=Red]sda8[/COLOR] - and so on. The primary partitions are blue and the logicals red. Which means that simply editing the partition table to move the extended partition boundary won't work. All the logicals in an extended have to be contiguous. In your case they are broken up.

You need forum member srs5694, who posted in the thread you linked, to say whether this is repairable without a complete reformat and re-installation.

How did this happen?

---

### Post by Quackers on 2011-01-21
Wow! I too would like to know how you got to this stage, please.

---

### Post by nvadiga on 2011-01-21
Really I too don't know how I ended up with this:) I keep changing OS first installed Mandriva, then switched to OpenSuse, now planning to go for Mint and finding solution to my problem at Ubuntu forums :D Lot of choices, lot of support... Feeling great about LINUX.

I was not aware of all these concepts(primary,extended and logical). I request srs5694 to detail about this and how to manage partition in a web page.

Any how I am ready to erase entire disk and create new partitions.

---

### Post by srs5694 on 2011-01-21
Coffeecat's analysis is correct. The good news is that, aside from the bizarre primary-within-an-extended condition, the partitions are consistent -- they don't overlap with one another. Thus, it's theoretically possible to recover all your data.

The bad news is that there's no gap between the end of /dev/sda2 (ending at 152,276,991) and /dev/sda3 (beginning at 152,276,992). This is bad news because logical partitions require at least one free (unallocated) sector before them, which means that /dev/sda3 can't become a logical partition. Given the location of this partition on the disk, as laid out by coffeecat, this means you're in a bind -- /dev/sda3 is the fourth partition on the disk, meaning that if you place the one extended partition you're allowed before it, it will hold at most three partitions, you'll have at most three primaries, and you'll therefore have to discard four partitions; and if you place the extended partition after /dev/sda3, it will be able to hold all six partitions that come after /dev/sda3, but you'll only be able to preserve at most three of the current four first partitions (5, 6, 2, and 3). In other words, there's no way to convert this partition table into a legal MBR setup without losing one partition.

I see several broad options for how to proceed:


[list]
[*]Decide which of the four first partitions (5, 6, 2, or 3) to omit and repair the partition table, keeping three of those as primaries and converting all the rest to logicals. Note that your current partition 4 is marked as bootable, but it will necessarily be a logical partition by this scheme, and therefore will not be bootable. Since /dev/sda6 is swap space, you can probably omit it without shedding any tears, but the space will be lost (short of moving/resizing partitions), and you'll be without swap space.
[*]Convert the disk to the GUID Partition Table (GPT) format with [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/) You can then preserve all your partitions; however, Windows can't boot from a GPT disk, so this is a reasonable option only if you want to use the disk for data or to boot Linux (but not to boot Windows).
[*]Convert the disk to GPT form but with a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to make up to three partitions accessible to Windows. Windows can boot from one of these three partitions, too. Unfortunately, hybrid MBRs are flaky and dangerous, and you've got six NTFS or FAT partitions, so I suspect this would be too limiting.
[*]Convert the disk temporarily to GPT and resize /dev/sda2's end point to make it just a bit smaller. This will enable you to convert back to MBR form, preserving all your partitions. You will be limited in which partitions will be bootable to Windows, though (the details depend on where you place your primaries, but they must consist of three partitions at the start and/or end of the disk).
[*]Convert the disk temporarily to GPT in order to back up, move, resize, and merge partitions into a more sensible configuration, then either convert back to MBR form or create a hybrid MBR.
[*]Back up some partitions, delete them, fix the problems with sfdisk or some other tool, create new replacement partitions, and restore your data.
[/list]


How best to proceed really depends to a great extent on how the disk is being used (which OSes access which partitions, and which partitions hold bootable Windows installations), which partitions hold important data vs. being easily deleted, and what sort of backup facilities you have. There's a good chance you'll have to re-install Windows when you're through fixing the problems.

Please post back with more details if you need more advice.

---

### Post by coffeecat on 2011-01-21
> **nvadiga said:**
> I was not aware of all these concepts(primary,extended and logical).

With the mbr/ms-dos type partition table, you are limited to four primary partitions only. To get around this limitation, one primary partition (one only) may be what's called an extended partition - in your case sda1. Think of an extended partition as a special type of primary partition whose only purpose is to be a container for a number of logical partitions. You can tell which is a logical partition from the output of fdisk - it is numbered 5 or higher. An extended partition cannot contain a primary - that is a contradiction - but might appear to do so if something has been mis-written to the partition table, which must be what has happened in your case.

Forum member srs5694 may join us* but in the meantime a couple of questions. What is on your three NTFS partitions? If you have Windows on one or more, can you still boot into Windows? And did you use the application testdisk at any time?

* **EDIT**: I see that he has - posting just a few seconds before I did.

---

### Post by nvadiga on 2011-01-22
Here is the details about my partitions. 
sda2(shown as 'system reserved'when mounted) was created by windows installer when I installed it first time (on sda3). Windows got corrupted somehow, so installed again assuming that it will use same sda2. But it created all new partition sda4. So now windows is on sda3(20GB) and sda2,sda4(100MB each) are 'System reserved' partitions. I guess I can delete sda2.

I have Opensuse on sda5 and Mandriva on sda10. When I boot the system, I am given with first bootloader screen from Mandriva and then from Suse. I can boot all three OS. Now I am planning to erase both Mandriva and Suse(format both sda5 and sda10), and install Mint on sda10. Please advice me how to go further.

---

### Post by nvadiga on 2011-01-22
Forgot to mention that I haven't used testdisk application.

---

### Post by srs5694 on 2011-01-22
I started to write a recovery procedure for you, but I realized that it's so long and full of things that can go wrong that it's not worth it. I recommend you do one of three things:


[list]
[*]Back up your user data, wipe the partition table completely, re-install Windows from scratch, install Ubuntu, and restore your user data.
[*]Back up all your user data and Windows installation, wipe the partition table completely, restore your backups, and install Ubuntu.
[*]Buy a new hard disk and use various backup/disk cloning tools to copy only the partitions you intend to keep to the new disk, create a new Ubuntu installation on the new disk, and swap the disks so that the new disk is your primary disk. You can then wipe the partition table on your current disk, create one or more new partitions, and use it for storing backups.
[/list]


Either method will be much more likely to succeed than any attempt at recovering your current configuration. I'd say the probability of your ending up having to re-install Windows and/or losing some of your user data in a recovery attempt is in the high double digits (maybe 80%). Thus, backing up before such an attempt would be critical, and from there you're halfway to one of the preceding solutions. Furthermore, a recovery attempt is likely to suck up inordinate amounts of your time (and probably mine, too, since I imagine I'd end up answering several more queries from you as things go wrong).

A Windows backup tool I've used successfully is [DriveImage XML.](http://www.runtime.org/driveimage-xml.htm) It can back up a Windows installation and restore it later to another location on the disk. I'm not sure if it can clone directly from one disk to another, though. [Clonezilla](http://clonezilla.org) is a tool that can clone many OSes' installations from one disk to another, although I'm not sure if it will preserve Windows' bootability if the boot partition's location changes.

For your final system, I recommend creating two primary partitions for Windows (for the System Reserved and C: partition), one or more logical FAT or NTFS partitions (containing whatever's on your current FAT partitions), and three or four logical partitions for Ubuntu (the root (/) partition, a swap partition, a /home partition, and optionally whatever's on /dev/sda8, if it's not a /home partition now). Create them in that order, to keep related partitions close to each other on the disk to minimize disk head movements.

---

### Post by nvadiga on 2011-01-26
Thanks srs5694 and coffecat for your quick reply, I took external hard disk from my friend and copied all my data and installed all OSs again with partitions as per your suggestion. Thanks again...

---

