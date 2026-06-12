---
title: "Dual boot partitioning"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by wahoobob on 2011-06-01
Just downloaded 11.04 and went to install on a windows 7 as a dual boot.  I didn't see any option to make a new partition for ubuntu as I seem to remember in earlier editions.  Am I missing something?  I want to leave 7 intact and give linux about 60 gigs to work in.  I would like to use a separate home partition,  but that is not a deal breaker if I can't.  Is there a simple install sequence I can use.  I am fairly non-technical.

---

### Post by garvinrick4 on 2011-06-01
Boot into install cd and choose Try Ubuntu and then select "gparted" package and you can
make partitions there for your / and your /home with '/' being your root file system. Needs
no more than 10 gig for / and as big as you want for /home everthing to be formatted in
ext4 while making partitions. Can make a /swap partition also about 2x's your installed RAM.

Most installation guides say to defrag windows before resizing that partition to make room
for Linux.

Resize and leave what space you want and then right click on space and make it and extended partition and then make your partitions for linux inside the extended partition with logical partitions. Can only have 4 primary partitions Windows is primary and extended is primary and then extended can house all the logical partitions you want. So extended just a house for logical partitions is all.

Right click on any partition to select what you want to do and have to hit the apply arrow to
put in effect. Be very carefull it is a partitioning tool 'gparted' that is.

**I will see if I have any links: I have no idea how old these are or what kind of gparted
sites just some I had in my tomboy notes in Ubuntu.

Gparted sites
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

[https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions)

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

### And your signature of being over 63 and naked at anytime kinda makes a person want to barf.##

---

### Post by oldfred on 2011-06-01
Most Windows 7 computers seem to use all 4 primary partitions. You will have to delete one to then follow garvinrick4's instructions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.

HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by wahoobob on 2011-06-02
Got home and tried both from the ubuntu disc and an older gparted disc and neither would let me change the size of the windows partition.  I would try to move the slider and nothing happens.  Tried changing the nubers, and nothing would change.  I don't think I have the partition mounted and there is only 2 gb showing free at the end of the drive and the rest is one primary partition... I opened the free area and said it could be formatted as partition also, but I just didn't complete that and left it as is for now.  I've never had this happen.  Any ideas?

---

### Post by oldfred on 2011-06-02
If it is Windows 7, you should use its MMC to shrink the windows paritions. That is generally a bit safer.

Post this from liveCD:

```
sudo fdisk -lu
```

---

### Post by wahoobob on 2011-06-03
Thanks, I'll try that.

---

### Post by bak&#305;r on 2011-06-06
Hi,

Not directly related to your currrent discussion, but currently using Wubi, I am planning to install Ubuntu 11.04 with partitioning. As my windows also "wants" to be reformatted, should I perform the partitioning during win xp setup or with live CD? or does it make a difference?

Thanks

---

### Post by oldfred on 2011-06-06
@bak&#305;r
Welcome to forums. 

It is best to start a new thread with your topic as the title. You will get more/better answers.

XP does not have partitioning built in. You can just use gparted. Be sure to backup everything you want to save. Note that wubi is just a file inside the NTFS partition, so backup any Ubuntu information also.
The XP installer will see totally blank drives or a NTFS partition with the boot flag to install to. I would partition in advance, or at least set up the NTFS partition to install XP to rather than install to full drive & have to defrag, chkdsk & shrink the NTFS partition.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by bak&#305;r on 2011-06-06
Thanks a lot for the advice.

---

### Post by physio_amer on 2011-06-07
[FONT=Comic Sans MS][SIZE=4]If you are new to linux then its better to use WUBI to install ubuntu from windows. it just stays on a ntfs drive which can be secondary or primary partition (read other than c:/). coz, in future if you face any problem with ubuntu then you can easily uninstall it using WUBI. I am using windows 7 and installed sabily 10.10 using WISABI (its ubuntu modified for muslims). [/SIZE][/FONT]
:KS

---

