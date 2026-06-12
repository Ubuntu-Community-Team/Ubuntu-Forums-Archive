---
title: "Partitioning for dual booting."
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by Morten_Fjellheim on 2015-01-26
So, i have tried ubuntu and i like it.  I think its dificult using emulators like wine, playonlinux etc so while i elarn about them i wana use windows besides ubuntu. I have tried to use gparted to make a partition to install windows on, i havent had much sucess in it though:( 
I was wondering if anyone could link a guide that explains how to make a partition i can install windows on. I want to split the hard drive in two almost equal parts, one for ubuntu and one for windows. The best way is probably to make a logical partition on the main harddisk, its just that i dont know how:(

---

### Post by Bashing-om on 2015-01-26
Morten_Fjellheim; Hello;


A great and comprehensive guide:
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Using that as our common reference, if you have further questions or concerns; please ask !

It is our desire to see you up and running 'buntu ->

[INDENT][INDENT][INDENT]help is what we do
[/INDENT][/INDENT][/INDENT]

---

### Post by Morten_Fjellheim on 2015-01-26
> **Bashing-om said:**
> Morten_Fjellheim; Hello;


A great and comprehensive guide:
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Using that as our common reference, if you have further questions or concerns; please ask !

It is our desire to see you up and running 'buntu ->[INDENT][INDENT][INDENT]help is what we do
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for that guide, its 14.10 i am running however so i am not sure if i can use it. Now, the problem described above by myself has been partially solved, i used the windows install program to split the hard drive in two. I now have two drives with almost the same size. But now i am back witht he same problem i had when i first tried to install for dual booting.
Even though i just have formated the hardrive meant for ubntu, and given it ext 4 filesystem i get an errormessage when i press install. The message says there is nor rootfile system applied on root! I am not sure if i should reopen the old thread or continue using this one. This thread is diferent from the old one due to the fact that this time i have been sucessfull in creating one partition for windows and another for ubuntu. So i think i will continue using this.

---

### Post by Bashing-om on 2015-01-26
Morten_Fjellheim; Sure;

We try and walk you through it.
Presently, are you able to boot up Windows ? 
Did you defrag Windows prior to resizing ? 
Did you run Windows file system check after completing the partitioning ? 

OK, we expect that Windows is installed on the 1st partition(s), and ubuntu is to be/or is installed on latter partitions.
It would at this time help a bunch to see what the partitioning layout is currently:
From the liveDVD in "try ubuntu" mode post back the outputs - Between Code Tags, please - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
We then see what is, and what is to be done.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Morten_Fjellheim on 2015-01-26
Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdcf9592c


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2  *       206848 483329893 483123046 230,4G  b W95 FAT32
/dev/sda3       483330048 968402943 485072896 231,3G  7 HPFS/NTFS/exFAT
/dev/sda4       968402944 976773119   8370176     4G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 7,5 GiB, 8017412096 bytes, 15659008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1          24 15659007 15658984  7,5G  c W95 FAT32 (LBA)


Disk /dev/sdd: 3,6 GiB, 3876225024 bytes, 7570752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18


Device     Boot Start     End Sectors  Size Id Type
/dev/sdd1        8064 7570751 7562688  3,6G  b W95 FAT32


Disk /dev/sde: 7,5 GiB, 8036285952 bytes, 15695871 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0d910b21


Device     Boot Start      End  Sectors  Size Id Type
/dev/sde1        4096 15683583 15679488  7,5G  b W95 FAT32


Disk /dev/sdf: 7,2 GiB, 7743995904 bytes, 15124992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd8780098


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdf1        8064 15124991 15116928  7,2G  c W95 FAT32 (LBA)


Disk /dev/sdg: 7,5 GiB, 8017412096 bytes, 15659008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdg1  *       24 15659007 15658984  7,5G  b W95 FAT32




I hope this is what you were asking me to do. As for your questions, yes io am able to boot windows. I did not defrag windows and i did not run windows file system check after partitioning.
When it cones to where i installed windows that was not on the first partition, it was on the second because at the time i already had ubuntu installed on the pc. After i installed windows i formated the first partition (the ubuntu partition) and set it to ext 4 cause i was told another time that ext 4 was the filesystem that should be aplied to a ubuntu partition.

---

### Post by Morten_Fjellheim on 2015-01-26
Oh sorry, my bad.......dev sda1 is the windows loader.
                                   dev sda 2 is the ubuntu partition
                                   dev sda 3 is the partition windows is installed on

Some information, i have no mount on the ubuntu partition (dev sda 2) should i_

---

### Post by Morten_Fjellheim on 2015-01-26
After eading the guide you linked i have done some changes to the partitioning, therefore i am now attempting an install. I will mark the thread resolved for now but will open it again if it didnt work.

---

### Post by Morten_Fjellheim on 2015-01-26
I have sucessfully installed both system on my pc and i can also open both. I will not need further asistance.

---

### Post by Bashing-om on 2015-01-26
Morten_Fjellheim; Great !

You do good work ->
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

