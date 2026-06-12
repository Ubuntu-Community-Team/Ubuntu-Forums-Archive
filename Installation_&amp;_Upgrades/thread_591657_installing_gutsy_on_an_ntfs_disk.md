---
title: "installing gutsy on an ntfs disk"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by iceonthehudson on 2007-10-25
I had Feisty running fine on a system with two hard drives, one of which (80G ext3) had the Ubuntu installation, and the other of which (250G ntfs) had all the data (music, movies, docs, etc).  

After a few weeks I tried to install XP as a dual boot, and after that my computer started shutting down or restarting randomly, no matter which OS I was booted into.  Since I cleaned the inside with a handheld vacuum and it made no difference, I figured it was probably the smaller hard drive that was acting up, since its pretty old.  

My plan is to disconnect the 80G drive and install Gutsy onto the 250G.  Is there any way I can do that without losing all the data on the disk during the installation?

---

### Post by snickers295 on 2007-10-25
do a defrag on the ntfs system twice.
make sure that there are no virus on the partition.
then download and partition with [gparted]("http://gparted.sourceforge.net/livecd.php") livecd.

---

### Post by iceonthehudson on 2007-10-26
the problem is, i no longer have an xp installation, although i do have an xp cd, so how can i defrag the volume?  can i do it from the gutsy live cd or the xp cd?

---

### Post by aidanr on 2007-10-26
You'll want to [resize]("http://gparted.sourceforge.net/larry/resize/resizing.htm") the ntfs partition with gparted and free up space for gutsy. I don't think defragging is necessary. 

> Note that Parted does not require a file system to be "defragged" (Parted can safely move data around if necessary). It's a waste of time defragging. Don't bother! [source]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25")

Of course it would be best to back up first if at all possible.

---

### Post by iceonthehudson on 2007-10-27
ok, i ran gparted, but while it was applying the changes i got "ERROR: Extended Record Needed (1032>1024) Not yet supported."  

Googling around a bit, I found some people saying to defrag the volume, others saying upgrade the BIOS.  Since I don't have an XP installation anymore, I don't know how I can defrag the disk, since it's ntfs.  

I also don't know how to upgrade the bios, since I don't know the make and model of my motherboard, and don't know how to upgrade a bios anyway. 

Which is a better option, or if I should do both, how?

---

