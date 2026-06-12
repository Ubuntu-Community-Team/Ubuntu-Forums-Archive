---
title: "Difficulty Installing (No partitions listed)"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by Tweaker420 on 2014-12-11
Greetings. I am trying to install Ubuntu 14.04 beside Windows 7. I have installed Ubuntu on this computer before. Everything goes fine until I get to Install Type. There is nothing at all listed here, and if i click any button other than back or continue i get errors. The real problem is not being able to select a partition for install. I have tried two different DVD's as well as USB install and i arise at the same problem each time, no listed partitions. I did some googling and I do not have any RAID issues or other strange problems. Attached is a screenshot. Any help would be appreciated, I have been on windows 7 for far too long and finally i do not have to use the windows only propriatary hardware i once needed, so I am free to use Ubuntu once again.

---

### Post by ajgreeny on 2014-12-11
Can you open gparted in the live ubuntu system that you used for installing and show us what that finds on the machine's hard disk.

---

### Post by grahammechanical on 2014-12-11
Is Windows 7 still on that machine? Have you done something that has effectively "blanked" the hard disk? In which case the "Use the Entire disk" option would be more appropriate than the "Something Else" option. Details on the existing partitions would also be helpful. What do Windows utilities show as on the disk?

Regards.

---

### Post by Tweaker420 on 2014-12-11
> **ajgreeny said:**
> Can you open gparted in the live ubuntu system that you used for installing and show us what that finds on the machine's hard disk.

Here is a screenshot. Thanks!

---

### Post by Tweaker420 on 2014-12-11
> **grahammechanical said:**
> Is Windows 7 still on that machine? Have you done something that has effectively "blanked" the hard disk? In which case the "Use the Entire disk" option would be more appropriate than the "Something Else" option. Details on the existing partitions would also be helpful. What do Windows utilities show as on the disk?

Regards.

No the disk is definately not blank. In fact I have made an ext4 partition even to put Linux on. GParted screenshot above. I do not even get to the part where i can select "use entire disk" or "something else" I believe this is the part I am stuck at. I am using the ISO downloaded from Ubuntu. Have tried downloading it more than once and used a different download of it but the same file. I assume the direct from Ubuntu download would be a good copy of it rather than torrent. A screenshot was uploaded of GParted showing my partitions, if you still want the one from Windows i can do that too.

---

### Post by oldfred on 2014-12-11
Choose the Something Else install option and click on sda6 and then the change button. Format ext4, choose it as root. You have some unallocated which you can click on plus button and make swap.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by Tweaker420 on 2014-12-11
> **oldfred said:**
> Choose the Something Else install option and click on sda6 and then the change button. Format ext4, choose it as root. You have some unallocated which you can click on plus button and make swap.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)



I get no option to choose "something else" or even "entire disk", also, there are no partitions listed in the installer despite GParted clearly showing they exist. I have also made an ext4 partition for which i wish Ubuntu to be installed upon. My previous posts attachments show what i mean. I will check these links tho and see if any of them suggest a resolution.

---

### Post by Tweaker420 on 2014-12-11
Unfortunately, none of those links offer a resolution oldfred. Thank You~

---

### Post by grahammechanical on 2014-12-11
> [COLOR=#000000]I do not even get to the part where i can select "use entire disk" or "something else" I believe this is the part I am stuck at.[/COLOR]

I have no choice but to believe you but it is most certainly strange. In every install that I have done the method is to let the live session load and we get a screen that offers Try Unbuntu without installing and Install Ubuntu. If we select Install Ubuntu then we get a screen asking us to confirm that there is enough disk space, and the machine has an internet connection and asking if we want to install updates at the same time and also if we want to have third party software installed. Then next screen offers

1) Install Ubuntu alongside - that is other operating systems
2) Erase disk and Install Ubuntu
3) Encrypt the new Ubuntu installation for security
4) Use LVM with the new Ubuntu Installation
5) Something Else - Create, resize partitions yourself or choose multiple partitions for Ubuntu.

It is only after choosing Something Else that we get that partitioner screen. 

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Regards.

---

### Post by oldfred on 2014-12-11
What does this show. Gparted does not seem to show any errors or warnings.
sudo fdisk -lu
sudo parted -l

---

### Post by Tweaker420 on 2014-12-12
> **oldfred said:**
> What does this show. Gparted does not seem to show any errors or warnings.
sudo fdisk -lu
sudo parted -l

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x87a48055

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   314793674   157293413+   7  HPFS/NTFS/exFAT
/dev/sda3      1929326168  1953122526    11898179+   7  HPFS/NTFS/exFAT
/dev/sda4       314793681  1929310109   807258214+   5  Extended
/dev/sda5       314793744  1804675071   744940664    7  HPFS/NTFS/exFAT
/dev/sda6      1804677120  1929308159    62315520   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001024af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15663103     7830528    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EADS-65M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   161GB   161GB   primary   ntfs
 4      161GB   988GB   827GB   extended
 5      161GB   924GB   763GB   logical   ntfs
 6      924GB   988GB   63.8GB  logical   ext4
 3      988GB   1000GB  12.2GB  primary   ntfs


Model: hp USB Flash Drive (scsi)
Disk /dev/sdb: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8020MB  8018MB  primary  fat32        boot, lba

---

### Post by Tweaker420 on 2014-12-12
> **grahammechanical said:**
> I have no choice but to believe you but it is most certainly strange. In every install that I have done the method is to let the live session load and we get a screen that offers Try Unbuntu without installing and Install Ubuntu. If we select Install Ubuntu then we get a screen asking us to confirm that there is enough disk space, and the machine has an internet connection and asking if we want to install updates at the same time and also if we want to have third party software installed. Then next screen offers

1) Install Ubuntu alongside - that is other operating systems
2) Erase disk and Install Ubuntu
3) Encrypt the new Ubuntu installation for security
4) Use LVM with the new Ubuntu Installation
5) Something Else - Create, resize partitions yourself or choose multiple partitions for Ubuntu.

It is only after choosing Something Else that we get that partitioner screen. 

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Regards.

Attached is a serries of screenshots showing my installation progression. The only other proof i could provide would be a video; but it will show esentially the exact same thing.

---

### Post by oldfred on 2014-12-12
Having the blank screen is not all that unusual. The installer partition tool is having an issue with partitions.
But usually one of the other partition tools will show some sort of error.

If NTFS needs chkdsk or ext4 needs fsck, but then gparted shows a red or yellow icon, you have no icons.
Also if drive was ever RAID, it may have meta-data that has to be removed.
If drive was ever gpt  it may have the backup gpt partition table and that has to be removed.
If an error in partition table where some entry overlaps or goes beyond end of drive.

But again other tools usually flag those errors so we know what to fix, you are not showing any other issue.

Is BIOS set drive to AHCI, not IDE, nor RAID?

We could go thru all the fixes in case one is not being shown by the partition tools, but I would not expect that to help. There must be some other issue?

---

### Post by Tweaker420 on 2014-12-12
> **oldfred said:**
> Having the blank screen is not all that unusual. The installer partition tool is having an issue with partitions.
But usually one of the other partition tools will show some sort of error.

If NTFS needs chkdsk or ext4 needs fsck, but then gparted shows a red or yellow icon, you have no icons.
Also if drive was ever RAID, it may have meta-data that has to be removed.
If drive was ever gpt  it may have the backup gpt partition table and that has to be removed.
If an error in partition table where some entry overlaps or goes beyond end of drive.

But again other tools usually flag those errors so we know what to fix, you are not showing any other issue.

Is BIOS set drive to AHCI, not IDE, nor RAID?

We could go thru all the fixes in case one is not being shown by the partition tools, but I would not expect that to help. There must be some other issue?



I had tried setting the drive option in my BIOS (which was set to RAID) to IDE as well as AHCI, which, unfortunately, produces the same results. Thank you for your time!

---

### Post by oldfred on 2014-12-12
If you had RAID on, perhaps there is meta-data on drive.

 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda

---

### Post by Tweaker420 on 2014-12-13
> **oldfred said:**
> If you had RAID on, perhaps there is meta-data on drive.

 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda

ubuntu@ubuntu:~$ blkid
/dev/sda1: LABEL="SYSTEM" UUID="24947A069479DAAE" TYPE="ntfs" PARTUUID="87a48055-01" 
/dev/sda2: LABEL="OS" UUID="DA9E7B029E7AD70B" TYPE="ntfs" PARTUUID="87a48055-02" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="3884B3AE84B36CCE" TYPE="ntfs" PARTUUID="87a48055-03" 
/dev/sda5: LABEL="Storage" UUID="7D289D035786FCDD" TYPE="ntfs" PARTUUID="87a48055-05" 
/dev/sda6: LABEL="Linux" UUID="2c0dfbc8-a491-46a0-83c8-fa5ed6c776de" TYPE="ext4" PARTUUID="87a48055-06" 
/dev/sdb1: LABEL="UBUNTU 14_1" UUID="062A-5A4D" TYPE="vfat" PARTUUID="000abe10-01" 
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda
Do you really want to erase "pdc" ondisk metadata on /dev/sda ? [y/n] :

Alright I answered yes, and now my partitions actully show up in the installer. I shall post another reply telling of my results and if i was successful. Thanks!

---

### Post by Tweaker420 on 2014-12-13
> **oldfred said:**
> Having the blank screen is not all that unusual. The installer partition tool is having an issue with partitions.
But usually one of the other partition tools will show some sort of error.

If NTFS needs chkdsk or ext4 needs fsck, but then gparted shows a red or yellow icon, you have no icons.
Also if drive was ever RAID, it may have meta-data that has to be removed.
If drive was ever gpt  it may have the backup gpt partition table and that has to be removed.
If an error in partition table where some entry overlaps or goes beyond end of drive.

But again other tools usually flag those errors so we know what to fix, you are not showing any other issue.

Is BIOS set drive to AHCI, not IDE, nor RAID?

We could go thru all the fixes in case one is not being shown by the partition tools, but I would not expect that to help. There must be some other issue?

Working great. Many thanks!

---

