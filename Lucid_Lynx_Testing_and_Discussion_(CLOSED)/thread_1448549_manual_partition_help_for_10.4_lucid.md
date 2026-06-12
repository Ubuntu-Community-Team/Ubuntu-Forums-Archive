---
title: "manual partition help for 10.4 lucid"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lori Boyd on 2010-04-06
Hey I need a little help from someone. 
I'm attempting to install 10.4 lucid from a livecd and i'm not familiar with partitions because i've never done it before. I want to dual boot windows 7 with the latest ubuntu because 9.10 will not work on my computer. I have a brand new hp pavillion dv4-2165dx laptop. Here's what i need to know:
 
1.) Is there a way to do an automatic partition on this version either through the full install or the demo install, if there is where/how do i do this?
 
2.) If there is no automatic partition, obviously i have to do a manual partition.Here's what i currently have
/dev/sda1 ntfs size208mb used69mb
/dev/sda2 ntfs size479641mb used49108mb
/dev/sda3 ntfs size20147mb used16889mb
/dev/sda4 fat32 size108mb used 33mb
Do i just change these numbers and file systems around or do i create a new partition table?
How much space to I use for each partition?
Any help would be appreciated because i really want ubuntu on my computer and this is the only way it will work on my computer.
[FONT=Segoe Print][SIZE=3][FONT=Segoe Print][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by oldfred on 2010-04-06
The 20-30 year old MBR partitioning scheme only allows 4 primary partitions and you have used all 4. I see windows boot, windows and two others usually recovery or related data.

You can convert one primary partition to an extended partition and add many additional partitions but have to have all the space adjacent and delete one of your existing partitions.

Without knowing how valuable your data is in any of the existing I think the best way is another hard drive. If you are sure you can delete and move data around after backing it all up then you may be able to create new partitions.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by srs5694 on 2010-04-06
I'm not intimately familiar with the Ubuntu installer (I've run it a few times, but I don't recall every detail), so I'll pass on answering your first question.

I am, however, very familiar with partitioning systems, so I'll say this about your second question: HP has done you a grave disservice. Most computers use the Master Boot Record (MBR) partitioning system, which is ancient and limited. In particular, you can have only four "primary" partitions. If you need more than four partitions, you can turn one of the primary partitions into an "extended" partition, which is a placeholder for an arbitrary number of "logical" partitions. Primary partitions are given the numbers 1-4 in Linux, so it's obvious that HP has, most inconsiderately, used *all* of your available partitions. You cannot add more partitions to your disk without deleting or otherwise altering at least one of your existing partitions. I'm not entirely sure what all of your partitions are, but my guesses are:


[list]
[*]/dev/sda1 -- This may be a Windows Recovery Environment (RE) partition, which is a sort of "helper" partition for Windows. I'm somewhat foggy on precisely what it does for Windows, but I'd be reluctant to delete it.
[*]/dev/sda2 -- This is almost certainly your main Windows installation (C: in Windows). You shouldn't delete it unless you plan to re-install from scratch, but you can shrink it to make room for Linux.
[*]/dev/sda3 -- My guess is that this partition holds the equivalent of your Windows installation DVD(s). Did your laptop come with physical media? If not, look for an application to create them and run it to create recovery DVDs. Then run it again to make a second copy. Once you've done this, I *think* it should be safe to delete this partition. (I did so with the equivalent partition on my Toshiba laptop.) While the program is making DVDs that HP is too cheap to provide to you, I recommend you write them a letter, with a cc: to Microsoft, telling them how cheap they are. The manufacturers will continue to be so cheap and inconsiderate as long as people don't complain.
[*]/dev/sda4 -- I have no idea about this one. Therefore I'd be reluctant to delete it unless/until I learn that it's safe to do so.
[/list]


So, if I were in your shoes and didn't learn more about these partitions, my plan would be:


[list=1]
[*]Make the recovery DVDs I've described
[*]Delete /dev/sda3
[*]Shrink /dev/sda2 (use Windows' native disk partitioning tool for this, if possible)
[*]Create a new extended partition (which will be called /dev/sda3)
[*]Create logical partitions for Linux. I recommend a 5-20GB root (/) partition, a swap partition that's a bit bigger than your RAM space, and whatever is left for /home. You might also consider shrinking the main Windows partition quite a bit and creating a new partition for sharing between Linux and Windows. This is safer than accessing the Windows system partition from Linux.
[*]Install Linux
[/list]


An alternative would be to completely wipe everything on the computer, re-install Windows in a less partition-hogging way, and then install Linux. This will obviously be easiest if you've got a retail Windows installation disc and spare license, but you might be able to use the recovery discs burned from your system to do the job. (I'm not sure how much flexibility such discs give in terms of partitioning, though; you might end up with a system that's set up exactly like it is now, with no choices to override the default settings.)

---

