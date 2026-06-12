---
title: "Partition problems"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by taker101 on 2011-09-01
I have windows 7, i need to create a new partition to install ubuntu, yet run windows 7 alongside it. I have free space on the allocate drive space however it is deemed unusable.

---

### Post by agillator on 2011-09-02
Back up your windows partition. Go ahead and start the ubuntu installation. One of the things the installer will ask you is where you want to install the system and you have several options: in addition to other systems, using the entire disk, etc. Answer appropriately - I assume alongside existing systems using free space. One of the options is also to manually set up partitioning. If you choose that option it will allow you to set the partition you want to use, the size, etc. When done, it will create the partition, format it, and install the system. Of course, you will want to back up your Windows partition first anytime you are doing something like this. And did I mention BACK UP YOUR WINDOWS PARTITION! Good luck, have fun.

---

### Post by Hakunka-Matata on 2011-09-02
taker101,  Welcome to the forums

Your Windows& Disk:

[LIST]
[*]How many primary partitions?
[*]All Basic Partitions or some Dynamic?
[*]of which Type,
[LIST]
[*]Win 7
[*]7 HPFS/NTFS -
[*]83 Linux -
[*]82 Linux swap / Solaris - etc.
[/LIST]
[*]How much Unallocated space available?
[/LIST]

---

### Post by taker101 on 2011-09-02
When I try to install Ubuntu the only two options given to me are: 1) Replace Windows 7 with Ubuntu
2) Something Else

I have 4 partitions all of which are basic and primary. And I have 100 GB unallocated. Current OS is windows 7.

Btw thank you for responding so for.

---

### Post by Hakunka-Matata on 2011-09-02
> **taker101 said:**
> When I try to install Ubuntu the only two options given to me are: 1) Replace Windows 7 with Ubuntu
2) Something Else

I have 4 partitions all of which are basic and primary. And I have 100 GB unallocated. Current OS is windows 7.

Btw thank you for responding so for.

post output of ```
sudo fdisk -lu
```

If all four primary partitions already exist (that's the maximum primaries allowed on MBR discs) you'll have to do some partition work first.
If you can post a picture of gparted depiction of the drive, that would be good, and/or a picture of windows disk management showing current layout of drive.

---

### Post by taker101 on 2011-09-03
heres is a pic of the disk management

---

### Post by YesWeCan on 2011-09-03
> **taker101 said:**
> heres is a pic of the disk management
Hi there. All 4 of your primary partitions are being used. To install Ubuntu at least one needs to be vacant. So you will have to delete one. HP_Tools may be the best one to make a backup of and then delete. Don't delete the System partition.

---

### Post by nipunshakya on 2011-09-03
> **taker101 said:**
> 

I have 4 partitions all of which are basic and primary. And I have 100 GB unallocated. Current OS is windows 7.



First off all, you cannot install Ubuntu in a machine that has four primary partitions my friend. You need to either reduce the partitions into two or need to change either of the unwanted partitions to logical drive....i had the similar problem with my machine too, but i managed it, installed wubi for test drive of ubuntu and now am planning to install ubuntu in a fresh partition....

for managing your partitions, download minitool partition wizard here: -

[http://http://www.partitionwizard.com/download.html]("http://http//www.partitionwizard.com/download.html")

its free and easy to use.....

you can give a shot to wubi too, installing ubuntu as an application too....but your machine your choice my fren....if u wanna have fresh partition, use the tool.

here's a link that could be helpful with your installation process too...read nicely and grab a good idea if u need....

[http://http://members.iinet.net/~herman546/index.html]("http://http//members.iinet.net/%7Eherman546/index.html")



Regards, NeptuneTech

---

### Post by oldfred on 2011-09-03
Some more links on the 4 partition issue.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)


Do this first just in case.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by taker101 on 2011-09-04
I downloaded successfully downloaded ubuntu using the wubi download. Thank you for taking the time to help me.

---

### Post by nipunshakya on 2011-09-04
> **taker101 said:**
> I downloaded successfully downloaded ubuntu using the wubi download. Thank you for taking the time to help me.

The pleasure was all mine....goodluck with your machine's rebirth....enjoy....:P

Regards,NeptuneTech

---

