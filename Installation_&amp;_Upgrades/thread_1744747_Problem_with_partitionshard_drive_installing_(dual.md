---
title: "Problem with partitions/hard drive installing (dual boot) ubuntu 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by The-Master on 2011-04-30
Hi.  

My problem is that I can't seem to install ubuntu with my current hard drive partitioning.  Is there any way I can sort this?  This is what it looks like in the allocated drive space window currently:

[img]http://s2.postimage.org/ririvoxhi/Screenshot_Install.png[/img]

My hard drives are partitioned like this:
[LIST]
[*]Windows 7 - 242GB
[*]D Drive (where I install programs for windows) - 137GB
[*]I also have a partition I made which was going to be for Ubuntu which is roughly 100GB.
[*]The 15GB partition is a recovery partition
[*]I'm not sure exactly what the other ones are (boot and things I think)
[/LIST]

It says that half my hard drive is unusable and doesn't know how much memory is used in my partitions.

I can't seem to mount the partitions when I boot into the live desktop from the disk.

When I try to install on any of my partitions I get this:

[img]http://s1.postimage.org/npbb7z23u/Screenshot_No_root_file_system.png[/img]

Sorry I have just spewed all of my problems out in quite an unordered fashion.  Hopefully you can make sense of it and can give me a hand.

Would be much appreciated!

Thanks.

PS. if it makes any difference I'm trying to install the 64 bit version.  My computer should be compatible since I have the 64 bit version of windows 7.

---

### Post by Quackers on 2011-04-30
If you select "try Ubuntu" from the live cd and load the desktop, you can then fire up gparted from the System > Admin menu. Please post a screenshot of what gparted shows.

---

### Post by The-Master on 2011-04-30
Thanks for the quick response.  Here is what gparted shows:

[img]http://s4.postimage.org/3y4w5zg3l/Screenshot_dev_sda_GParted.png[/img]

---

### Post by Quackers on 2011-04-30
You already have 4 primary partitions. 4 Primary partitions is the maximum allowed on an mbr partitioned disk. If you try to make another partition Windows will change its partitions to "dynamic disks". This is BAD!
Also the first 3 NTFS partitions have an exclamation mark in a red circle next to them. Right-click on each one and select "information" and see what gparted says about that.
Judging by what you have named sda4 I suspect that you intend to install Ubuntu there. That won't work as Ubuntu will not install to a NTFS partition. You would need to delete that partition and create an extended partition in its place. This extended partition can then hold as many logical partitions as you wish to create.

---

### Post by oldfred on 2011-04-30
STOP!!! Do not write anything to disk.

You do not show either 242GB or 137GB windows partitions. It looks like in creating sda4 you somehow erased you main windows partitions.

Linux does not use NTFS partitions and you should make sda4 an extended partition so you can add many logical partitions inside it. But most standard windows installs now use all 4 primary partitions, making users leap thru hoops to install. Most make recovery DVDs and erase that or backup the vendor utilities and erase that one.

If your windows partitions are really missing you may be able to recover some or all of the data with testdisk. It may or may not recover to a point of being bootable.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by KingLewy on 2011-04-30
I too have 4 primary partitions and cannot install Ubuntu. I've installed Ubuntu god knows how many times (either enlightening friends and family to its wonders, or simply installing multiple times on my own computers for **** ups) and I have never come across this. I've screen dumped what GParted showed me below. Would it be correct of me to back up HP_TOOLS to cd or external HDD, delete the partition and replace it with an EXT4 partition to install Ubuntu on (after resizing, obviously)? Thanks.

Well, I can't get the image to upload :s It shows:- 

sda1 - ntfs SYSTEM 199 MiB (boot flag)
sda2 ntfs 449 GiB (Windows 7)
sda3 ntfs RECOVERY 16 GiB
sda4 fat32 HP_TOOLS 103 MiB lba (flag)

---

### Post by oldfred on 2011-04-30
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by The-Master on 2011-05-01
Thanks for all that information.  It is all very useful.  The current problem I have is that with my 4 partitions set up I proceeded to split one in windows so I could install ubuntu.  I didn't know of the 4 primary partition limit when I did this.  So now my windows disk manager looks like this:

[img]http://s2.postimage.org/ysm579pcv/Untitled.jpg[/img]

That looks to me like I only have 1 primary partition and the rest are virtual ones or simple volumes.

But this doesn't make much sense to me because gparted seems to show that I have 4 partitions (shown above).  It also says there are errors which I have uploaded below.

Can anyone get their head round this?  Do you think there would be any way to sort it without wiping everything from my disk.

Sorry about the essay length posts!

---

### Post by oldfred on 2011-05-01
Gparted must now see dynamic SFS partitions. It did not used to. The offical windows procedure is to back everything up, erase disk and create new partitions.

Always best to use windows tools for windows and Linux tools for Linux. Create new partitions with gparted.

Be sure to have good backups. And if nothing is in the new partition delete it first.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

### Post by KingLewy on 2011-05-01
Thanks a bundle. I'm getting some really good advice here. I followed the procedure posted by srs5694 in the linked post up to Step 5. I've backed up my recovery partition (4 dvds, thanks HP) and deleted it and resized my Windows 7 partition. In the Windows Disk Management tool I can see the unallocated space freed up from the Windows 7 partition, but not from the Recovery partition :s Don't know why this is, but I'm asuming there's nothing potentially "dangerous". I may attempt to install Natty tonight, I may wait until tomorrow. Either way, I'll post how it goes.

Thanks for all your help, it's been invaluable!

---

### Post by KingLewy on 2011-05-07
Ubuntu 11.04 is ace. Thanks for all your help :)

---

