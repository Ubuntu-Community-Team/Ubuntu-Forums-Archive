---
title: "problem installing ubuntu 12.04"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by dharmesh.patel on 2013-11-06
Hi I'm new here and i was trying to install ubuntu, this is also my first experience with Linux. i downloaded the iso from the ubuntu site and I used unetbootin to put the iso on a usb flash drive (my computer doesn't have a disk drive). so when i restart my computer with the usb in it loads to the grub and when i try to install ubuntu it lets me set the initial options then restarts to the grub menu. there's an option to check for error and it comes back with 1 error. i also tried "universal usb installer" and "usb-creator" and they had the same issue but they also found two errors.

---

### Post by fantab on 2013-11-06
Is there space for Ubuntu on the hard drive? When you boot with the USB, 'Try Ubuntu without installing"- open Terminal [ctrl+alt+t] , run the following commands and post its output here:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by dharmesh.patel on 2013-11-06
this is what comes up:

ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd0e8063b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   922757119   461173760    7  HPFS/NTFS/exFAT
/dev/sda3       922757120   976560127    26901504    7  HPFS/NTFS/exFAT
/dev/sda4       976560128   976771071      105472    c  W95 FAT32 (LBA)


Disk /dev/sdb: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013713 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     4013712     2006825    c  W95 FAT32 (LBA)




ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   472GB  472GB   primary  ntfs
 3      472GB   500GB  27.5GB  primary  ntfs
 4      500GB   500GB  108MB   primary  fat32        lba




Model: SanDisk U3 Cruzer Micro (scsi)
Disk /dev/sdb: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2055MB  2055MB  primary  fat32        boot, lba

---

### Post by fantab on 2013-11-06
You don't have space to install Ubuntu/Linux. So what do you want to do, Dual-Boot Windows and Ubuntu or Erase Windows and install Ubuntu? "How to" depends on your answer/choice?

Also tell us about your computer, RAM, Graphics etc.
What version of windows do you have, Win7 or Win8?

---

### Post by dharmesh.patel on 2013-11-06
I want to duel-boot windows and Ubuntu
i have an: 
HP ENVY 6 Notebook PC
AMD A6-4455M APU with Radeon(tm) HD Graphics, 2100 Mhz, 2 cores, 2 logical processors
Windows 7 Home Premium

---

### Post by fantab on 2013-11-06
```
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
**Partition Table: msdos**


Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   472GB  472GB   primary  ntfs
 3      472GB   500GB  27.5GB  primary  ntfs
 4      500GB   500GB  108MB   primary  fat32        lba
```

Alright. Your HDD has a 'msdos' partition table, which has a ONLY 4 PRIMARY Partition Limit. You already have 4 Primary Partitions. So, what do we do?
1. Delete one of the Primary Partition
2. Create an EXTENDED Partiton in its place. [Extended Partition is a Primary Partition which acts as a container for LOGICAL Partitions. Inside an Extended Partition we can create 100 Logical Partitions or more].

Creating an Extended Partition is simple. But first we need to decide which Partition to Delete. A Screen-Shot of your Partitions from Windows will help us. Please post the Screen-Shot of your HDD from Windows, showing all the drives.

Also, it is recommended that you make a [Windows Repair Disc]("http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html") before we commence any further. This not same as vendor recovery.

Post that screen-shot.

---

### Post by dharmesh.patel on 2013-11-06
here it is. and if i dont have a disk drive or external disk drive what are my options for a windows repair disk.

---

### Post by fantab on 2013-11-06
Don't you have a CD/DVD or you don't have CD/DVD drive? I think you can use a USB pen/thumb drive too, but not sure how to go about it. We need a Repair Disk, because if thngs go south your can recover your windows.

Your Second Partition, 99MB HP Tools can be safely deleted. But before you Delete it copy all of its contents elsewhere.
1. Delete your 'HP Tools' Partition.
2. Create space for Ubuntu by SHRINKING your first partition, C: 430GB. [How to Shrink Partition]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")... 
3. After above two steps, you will have 'Unallocated space'. Leave it as it is. And Boot Ubuntu DVD/USB.
4. If you want to Backup your HDD this will be a good time. It will be useful if something needs to be restored, especially if you want to re-sell your laptop in factory condition. 
[http://www.macrium.com/](http://www.macrium.com/)
[http://kb.macrium.com/KnowledgebaseArticle50074.aspx](http://kb.macrium.com/KnowledgebaseArticle50074.aspx)
[http://kb.macrium.com/KnowledgebaseArticle50047.aspx](http://kb.macrium.com/KnowledgebaseArticle50047.aspx)

The above, 4th step is Optional.

5. Boot with Ubuntu DVD/USB and follow this for automated install:[ http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

Be Careful, you have to choose "**Install Ubuntu Alongside Windows 7**".... Thats it.

OR

You can choose 'Something Else' option to manually partition and install Ubuntu. I'd recommend this.

Boot with Ubunt DVD/USB and "try ubuntu without installing'. Open Gparted.

Seclect the 'unallocated space' [say you have 100GB], and "create new':
1. 100GB Extended Partition. See in dropdown menu and choose Extended partition. Apply changes. After applying changes you will notice that you still have 100GB 'unallocated space'.
2. 20GB LOGICAL Partition [Use As = Ext4] check Format. Apply changes.
3. 4GB Logical Partition [Use As = SWAP/Linux SWAP] Check Format. Apply Changes.
4. All the remaining GB [USe As = Ext4] Check Format. Apply Changes.
5. Close Gparted.
6. From Desktop, Install Ubuntu.
7. At the 'Installation Type' Dialog choose 'Something Else'. Again you will see gparted-like interface.
8. Select 25GB Partition, hit Change and select [Mountpoint = /] this is where you will install Ubuntu system files. change/continue
9  Select 'All the remaining GB, hit change and select [Mountpoint = /home] here you store all your personal data. Change/continue.

[**Read Here**]("http://members.iinet.net.au/~herman546/p23.html") to see the screen-shots. Its bit old, but relaveant.

Thats it.

Good Luck.

---

### Post by mastablasta on 2013-11-07
there is no need to delete any partition. use the free mini tool partition wizard to change the C volume into secondary (extended) partition.

defragment it two times and shrink it for some ubuntu space (leave the space it unformated) and then continue with install as described by fantab. you may need to choose something else. and i would like to add that if you need to go with something else you will only need 2 paritition for Ubuntu (/ and /swap).

how to create recovery disk? - it's in the manual. one of the HP tools in windows (don't know which one on your HP) will help you create it. mine is the tool to setup computer, update vide drivers and BIOS. it was there where i could create recovery disk (only one) and i had to do it to a USB stick - you just need a large enough USB hard drive or stick and the rest is done automaticly.

another option is to back the whole thing up (clone it bit by bit) to external USB drive using Redo backup or Clonezilla.

---

### Post by fantab on 2013-11-07
Windows7 from Logical Partiton works, but I don't trust Windows on a Logical Drive and I wouldn't recommend it... I've had problems with it on a friend's machine. 
However, I have never owned a HP machine, so the above post by mastablasta perhaps comes from experience with HP machines. Either ways you should be fine.

---

### Post by dharmesh.patel on 2013-11-07
ok so i looked at the options you guys have given me and i deleted the hp_tools partition, i chose to go against mastablasta[COLOR=#000000] method because as i first time linux user the something else method seems confusing. but i do have some questions, first how big should the new partition be, should it be as big as i want the linux partition and second do i format it or leave it unidentified.[/COLOR]

---

### Post by fantab on 2013-11-07
The manual/'Something Else' option gives you more control over your installation and its quite simpler than it sounds, anyway.

Yes, the Linux Partition can be as big as you want it to be and as much Shrinking Windows allows on C: partition.
Leave the space you've made available for Ubuntu as "unalllocated space", do NOT create any partition using Windows' tools. However you can either create partitions using Gparted or let the ubuntu installer take care of it for you.

**Backup All your Important DATA** before you proceed with installaiton. If you make a mistake with auto disk partitioner then the installer might wipe out the entire disk. A good BACKUP is very IMPORTANT.

---

### Post by mastablasta on 2013-11-08
lately HP_Tools actually has some good diagnostic, recovery and update utilities. so it is not really good to just remove them. however now that you've done it i believe they can still be reinstalled later on windows C partition should you need them.

Backup, backup, backup!

Proceed as you planned and good luck.

---

### Post by dharmesh.patel on 2013-11-08
ok so i installed ubuntu and it said complete and to restart but when i restarted it didnt load the grub menu it just went straight into windows

---

### Post by fantab on 2013-11-08
Try **[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")**. The '*Recommended Repair*' will fix it for you. Save the **Bootinfo-Summary** LINK which is generated by Boot-REpair and post it here if you still encounter any boot issues.

---

### Post by dharmesh.patel on 2013-11-08
alright everything is working fine now. thank you for all your help

---

### Post by fantab on 2013-11-08
Did you use boot-repair?

If you are content, mark the thread as 'Solved' using Thread Tools.

---

