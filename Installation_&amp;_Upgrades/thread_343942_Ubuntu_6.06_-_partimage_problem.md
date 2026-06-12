---
title: "Ubuntu 6.06 - partimage problem"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by llelkes on 2007-01-22
Hi!

I have a problem with partimage. Its a rescuecd with a Gentoo linux.
I'd like to increse my paririton for Ubuntu.

Old parttab:

part1 NTFS 10GB - Win
part2 ext3  5 GB - Ubuntu
part3 fat32 10 GB

partimage
  - make a backup of ubuntu

fdisk 
  - delete part2, part3
  - create new part 2 15GB 
  - cerate and format for ext3 15GB

partimage
  - restore ubuntu

ewerithing worked fine :) but after booting to ubuntu     
df -h
  - ubuntu partition size is the old size 5 GB

if i check fdisk the size of the partition is correct :D 
if i check thrue ubuntu df -h for /dev/hda2 then 5 GB :confused: 

 Any ideas?
(i made a several backups and restores with that partimage for Fedora and WinXP and no problem)

Thanks,
Laci

---

### Post by llelkes on 2007-02-07
problem solved - i need to resize the filesystem:

fsck /dev/hda8  - chect filesystem for errors

tune2fs -O^has_journal /dev/hda8  - turn off journal - covert ext3 to ext2

resize2fs /dev/hda8 - wotout 2. param take the maximal part. size 

tune2fs -j /dev/hda8 - turn on journal - convert ext2 to ext3

fsck /dev/hda8  - chect filesystem for errors

---

### Post by mjiba on 2007-03-08
> **llelkes said:**
> problem solved - i need to resize the filesystem:

fsck /dev/hda8  - chect filesystem for errors

tune2fs -O^has_journal /dev/hda8  - turn off journal - covert ext3 to ext2

resize2fs /dev/hda8 - wotout 2. param take the maximal part. size 

tune2fs -j /dev/hda8 - turn on journal - convert ext2 to ext3

fsck /dev/hda8  - chect filesystem for errors

can anyone explain these steps for a neewb?  I am having he same problem but have no idea how to resize my filesystem.

---

### Post by Herman on 2007-03-08
Hello mjiba, 
I would consider those steps to be a little bit advanced for a new users to be bothered with. 
Basically llelkes had Ubuntu in a 5 GB partition, and made a backup of the entire operating system in the partition with Partimage. When llelkes restored the backup, it was restored into a larger partition of 15 GB, but the filesystem was still only 5.0 GB, only filling 1/3 of the partition. 
To resize the filesystem, llelkes first checked the filesystem for errors, and then llelkes turned of the ext3 journalling to make it into an ext2 filesystem instead. Then  resized the filesystem, and turned journalling back on again. The only difference between ext2 and ext3 is that ext3 features journalling. Finally, llelkes rechecked the filesystem once more, just to make sure.
It is nice to see people using Linux commands to do things. We can do everything with Linux commands if we know how. To find out more about the commands we can look them up in the manual. What I mean by that is, we can type 'man  fsck ', 'man tune2fs' and 'man resize2fs', for an explanation of what those commands  and their options will do.
 
These days it is simpler and faster if you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") to just right-click on the partition (filesystem) and click 'check', and [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") will do all that for us in a minute or two. That's the easiest way to do it.

Regards, Herman :)

---

### Post by Lucifiel on 2007-05-05
> **Herman said:**
> Hello mjiba, 
I would consider those steps to be a little bit advanced for a new users to be bothered with. 
Basically llelkes had Ubuntu in a 5 GB partition, and made a backup of the entire operating system in the partition with Partimage. When llelkes restored the backup, it was restored into a larger partition of 15 GB, but the filesystem was still only 5.0 GB, only filling 1/3 of the partition. 
To resize the filesystem, llelkes first checked the filesystem for errors, and then llelkes turned of the ext3 journalling to make it into an ext2 filesystem instead. Then  resized the filesystem, and turned journalling back on again. The only difference between ext2 and ext3 is that ext3 features journalling. Finally, llelkes rechecked the filesystem once more, just to make sure.
It is nice to see people using Linux commands to do things. We can do everything with Linux commands if we know how. To find out more about the commands we can look them up in the manual. What I mean by that is, we can type 'man  fsck ', 'man tune2fs' and 'man resize2fs', for an explanation of what those commands  and their options will do.
 
These days it is simpler and faster if you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") to just right-click on the partition (filesystem) and click 'check', and [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") will do all that for us in a minute or two. That's the easiest way to do it.

Regards, Herman :)

Really? Does this "check" feature come with Dapper Drake livecd? That's because I have a Feisty beta livecd and I can't seem to find Gparted.

---

### Post by Herman on 2007-05-05
Hello [Lucifiel,]("http://ubuntuforums.org/member.php?u=263294")                      
No, the version of GParted that Ubuntu uses is GParted 0.2.5, which is quite an elderly version of GParted, it doens't have so many features, unfortunately.

However, you can download your own [GParted -- LiveCD]("http://gparted.sourceforge.net/") for free, and they are only a small download, about 45 MB I think. The latest released version is 0.3.4-6. You should get one of those and burn it to a CD, it is very good.  A CD-RW is best so you can overwrite it again when a newer version comes out. The GParted developers work very hard and keep improving GParted, a newer version comes out every two or three weeks. 
With [GParted -- LiveCD]("http://gparted.sourceforge.net/") you can right-click on your partitions and click 'check', and they will be checked for you. The file system will be resized to fill the partition. Minor repairs will be carried out for you and you will be able to see a report of what your filesystem is like when it's finished. If there are more repairs that need to be done manually (from the command line), it will let you know.
The GParted in the LiveCD has full 'move support' for Linux filesystems too, so you can 'move' a Linux partition or resize it from the start of the partition. That's an important feature because normally you can't move the start point of a Linux partition (easily), (well you can copy it and paste it three times to hop it to where you want it, but that's another story).
GParted Live CD also has Partimage and TestDisk in it, and there are Clonezilla versions too, and they even have Grub in them as well now!
I highly recommend [GParted -- LiveCD]("http://gparted.sourceforge.net/"). Everyone should have one.

Regards, Herman  :)

---

### Post by Lucifiel on 2007-05-05
> **Herman said:**
> Hello [Lucifiel,]("http://ubuntuforums.org/member.php?u=263294")                      
No, the version of GParted that Ubuntu uses is GParted 0.2.5, which is quite an elderly version of GParted, it doens't have so many features, unfortunately.

However, you can download your own [GParted -- LiveCD]("http://gparted.sourceforge.net/") for free, and they are only a small download, about 45 MB I think. The latest released version is 0.3.4-6. You should get one of those and burn it to a CD, it is very good.  A CD-RW is best so you can overwrite it again when a newer version comes out. The GParted developers work very hard and keep improving GParted, a newer version comes out every two or three weeks. 
With [GParted -- LiveCD]("http://gparted.sourceforge.net/") you can right-click on your partitions and click 'check', and they will be checked for you. The file system will be resized to fill the partition. Minor repairs will be carried out for you and you will be able to see a report of what your filesystem is like when it's finished. If there are more repairs that need to be done manually (from the command line), it will let you know.
The GParted in the LiveCD has full 'move support' for Linux filesystems too, so you can 'move' a Linux partition or resize it from the start of the partition. That's an important feature because normally you can't move the start point of a Linux partition (easily), (well you can copy it and paste it three times to hop it to where you want it, but that's another story).
GParted Live CD also has Partimage and TestDisk in it, and there are Clonezilla versions too, and they even have Grub in them as well now!
I highly recommend [GParted -- LiveCD]("http://gparted.sourceforge.net/"). Everyone should have one.

Regards, Herman  :)

Whoa, okay... thank you for all the help and instructions!!!! 
I will download the Gparted Livecd and post back within 24 hours' time. :P

---

### Post by Lucifiel on 2007-05-05
Woot, so using the Gparted livecd worked. :)

The only error I got was some superblock future error, which Ubuntu then fixed. :)

---

### Post by Herman on 2007-05-05
Yay!  :guitar:
I knew it would!
You won't regret having a GParted LiveCD, chances are it'll come in handy for again sooner or later for some other jobs you might need. 
Glad it worked for you, thanks  for the feedback,
Regards, Herman :)

---

