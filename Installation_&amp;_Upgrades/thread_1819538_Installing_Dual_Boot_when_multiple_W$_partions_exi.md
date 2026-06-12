---
title: "Installing Dual Boot when multiple W$ partions exist"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by juliancam on 2011-08-06
The title says it all really. I am still a comparative novice with Ubuntu. I have an Acer laptop that has Windows Vista on it's hard drive with an original setup of a hidden recovery partion, C partion for windows and D partion for data.  The drive is 250GB with C being 111GB (about half used) and D being 108GB (about 20GB used). I need to keep Vista but would like to install Ubuntu alongside as I prefer it. I have read up on installing a dual boot system but it all seems to assume windows is on one partion. Before making a start, I wanted to check how naive I am being in hoping that it is just a case of shrinking the D partion to make space and follow the onscreen instructions. I would really like to shrink both C and D partions but suspect that would create more problems than I care to face. I have a backup of all my data but would prefer not to have it all go pear shaped and have to reinstall Vista as my only Vista discs are the backup discs I had to make when I first got the computer.

Julian

---

### Post by oldfred on 2011-08-06
How many partitions have you actually used. MBR(msdos) only allows 4 primary partitions and Windows system seem to like to use all four. You can convert one primary to an extended partition can create as many logical partitions as you need for Ubuntu & a shared NTFS (D:) drive. Since you have a D: you may have to back it up and delete it, then recreate it as a new logical partition.

Post this from the Ubuntu liveCD and we can give more detailed suggestions.

```
sudo fdisk -lu
```Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.

---

### Post by juliancam on 2011-08-06
Thanks Oldfred. I have the original recovery dvds that I made and I have never had much success with repair cds - I always seem to cause more damage whilst trying to repair :(. 
Here is the fdisk report for the drive. I don't know enough to interpret it but I am hoping that the devs/sda might mean one primary and four logical partitions. SDB is the USB stick I am booting from. One further thought I had is that since there is so little on my data partition (and unlikely to grow significantly), maybe I could swap it onto C (reassigning the links for my user folders of course) and just use D for the Ubuntu installation. But I am not sure what complications that might cause to windows or Ubuntu.

Julian


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc6fd324a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20467712   254701567   117116928    6  FAT16
/dev/sda3       254701568   481595391   113446912    7  HPFS/NTFS
/dev/sda4       481595392   488394751     3399680   12  Compaq diagnostics

Disk /dev/sdb: 4075 MB, 4075290624 bytes
126 heads, 62 sectors/track, 1018 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7952615     3976277    c  W95 FAT32 (LBA)

---

### Post by oldfred on 2011-08-06
I do not see your d: drive. But you seem to have two Compaq diagnostics partitions? You also are showing FAT16 for your boot partition (c: drive?). XP installed in FAT32 (older versions) or NTFS and Vista/7 required NTFS, so what version of windows are you booting?

If you are sure D: drive only has your data, then you can back it up or copy it to c: if you have room. Windows needs lots of free space in a NTFS partition (30%) to work well. Then you can convert that partition to an extended partition can create a new logical partitions - NTFS for data, / (root), /home (if you want) and swap.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

IF system is so old as to boot from FAT16, do you have hardware specs for full Ubuntu or should you be considering one of the lighter weight versions? Also very old (over 6 or 7 years old) system can only boot from the first 137GB, so if you upgraded to a newer larger hard drive and install to the end of the drive may not boot.

---

### Post by juliancam on 2011-08-06
My laptop is an Acer Aspire 5920G so it's no spring chicken but not yet an old age pensioner. CPU is a low end Core2Duo and it has 3GB  ram and an NVidia 8600 mobile gfx card, so system specs are not a problem. Disk Utility shows SDA2 as Partition Type:FAT16 (0x06), Partition Flag: Bootable; Type:NTFS , Label: ACER and SDA3 as Partition type: HPFS/NTFS (0x07), Partition Flag: - , Type: NTFS, Label: DATA. This is how it came from Acer when I bought it. Why the heck SDA2 is FAT16 is anyone's guess but it came with Windows Vista and runs it quite happily. Equally why there is a 10GB recovery partition AND a 3.5GB recovery partition at the ends of the drive is a mystery known only to Acer. If I dump D in to C, it would leave 34 GB free or pretty much exactly 30% free space in C - a bit too tight for my comfort. It looks like either a long job using the recovery DVDs to start from scratch to create new partitions for Vista and Ubuntu or shrinking SDA3 to put Ubuntu in a new partition but I have 2 questions on this. Bearing in mind your comment about MBR(msdos) limitations, how do I tell if the existing partitions are primary or logical and will Ubuntu have problems installing between 2 existing partitions?

Edit: I have answered my first question SDA1 and SDA4 are not reporting as primary partions whilst SDA2 and SDA3 are primary partions so I should be able to create a new one for Ubuntu.

Julian

---

### Post by oldfred on 2011-08-06
Primary partitions are sda1 thru sda4. Any one of sda1 thru sda4 can be converted to the extended partition and then logical partitions start at sda5 and go up to just about any number. 

I have seen errors in partition table vs. partitions or partition table entry does not match actual format of partition. This often leads to errors as tools trying to read partitions see conflict. Have you tried opening drive with gparted from liveCD and does it show any errors (red or yellow icons next to partition).

Ubuntu installs just fine in logical partitions. Windows has to have its first install (boot flag) in a primary as that is the one it boots from. In fact users have deleted an old XP in the primary partition and wondered why a win& does not then work that was in sda5 (logical). Windows literally moves boot files from second installs into the first install.

---

### Post by juliancam on 2011-08-06
Oops sorry about that ( it's getting later in the evening  - UK is 5 or is it 6 hours ahead of Chicago) .I misread Vista's disk manager information. Back in Ubuntu Gparted reports all file systems as NTFS and all green next to the partitions but I am having trouble figuring out how to change SDA3 to an extended partition ( and in how to spell partition :) ). Methinks it is time for me to start again tomorrow before I mess up something important (us oldies can't burn the candle at both ends like we used to).

Julian

---

### Post by oldfred on 2011-08-06
Please do not use windows to create new partitions. It has a nasty habit of converting your partitions from basic to dynamic which does not work with anything including some windows utilities. Dynamic is windows version of LVM or logical volume management.

Use gparted to modify partitions. You can delete & create partitions easily with gparted.

---

### Post by juliancam on 2011-08-07
Ok. I think I have it now. Don't use windows for partitioning. If 4 primary partitions exist, you cannot change one to extended it must be backed up, deleted and then recreated as an extended partition. In my case, since I have a new backup  of system and data partitions, I think I will forego the dubious pleasure of the 2 hidden recovery partitions and thus leave room for me to create one more primary for Ubuntu.

Julian

---

