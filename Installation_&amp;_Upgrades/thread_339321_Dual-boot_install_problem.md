---
title: "Dual-boot install problem"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by clothrh on 2007-01-15
Hello, I've been using Ubuntu Edgy on my older machine, as the exclusive OS.  I've liked it so much I've decided to use Ubuntu on my newer machine, but I need to dual-boot with windows to keep my zune going and occasional stuff from the university.  I installed the first copy of ubuntu automatically, so this is my first manual install. I have two 160GB hard drives in the new machine, with one already formatted to FAT32, holding shared media for windows and ubuntu.  The master hard drive had 2 partitions under XP, with 40GB for system and the other 115GB or so for data. I'm installing from the Edgy Live CD, and in Step 4 I turned the data partition into 3 new partitions, Now the hard drive has 4 partions, and in Step 5 I'm trying to set them up as follows:

hda1 40GB ntfs for XP
hda2 2GB ext3 for swap
hda3 15GB ext3 for /
hda4 55GB FAT32 for /home

The window for step 5 has a warning at the bottom, saying "No root file system"

I thought the / on hda3 was supposed to create the root file system?  Any help will be greatly appreciated.

---

### Post by mat_geek on 2007-01-15
From the [Bug Report]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130")

> I confirm that this workaround works. Go back in the install interface, log as root in a terminal window, delete the partition with fdisk, recreate it (still in fdisk... at least that's what I did), and proceed with the installer reusing existing partitions.

But from the rest of the bug report it seems it may be more complex.


From the updated [Release Notes]("http://www.ubuntu.com/download/releasenotes/610")

> The advanced partitioning mode of the installer on the desktop CD has trouble reusing an existing root file system, and will incorrectly claim "No root file system". Since you must reformat the root file system for use by the installer in any case, you can easily work around this problem by deleting and re-creating the partition in question in the advanced partitioner. [https://launchpad.net/bugs/67130](https://launchpad.net/bugs/67130)

---

### Post by mat_geek on 2007-01-27
Tuirns out t was simpler than that.

Just delete the partitions you want to use. Restart the installer and you should get an option to use the largest contiguous free space. It will then create two partitions, root and swap.

That Is what I did for my install, last week. I tried every thing else and that worked.

---

### Post by clothrh on 2007-01-31
I finally got it to work, but I'm not sure exactly what I did differently.  I managed to get the live CD to do the manual partitioning and installation, so I didn't have to try anything too fancy.

---

