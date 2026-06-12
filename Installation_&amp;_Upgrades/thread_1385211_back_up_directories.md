---
title: "back up directories"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by mattman85 on 2010-01-19
Is it possible to just tar /home, /opt, and a couple other directories, and then save them on some medium, so that when doing a fresh install, I could just extract the folders from the tar file and keep my information?

I don't plan on doing daily/weekly backups, but I want a copy of some folders so that I can keep as many of my settings as possible in case I need to do a fresh install.

I also don't have the ability to create another partition on my hard drive to be able to put /home on it.. but yes, I looked into that route, as well.

---

### Post by audiomick on 2010-01-19
> **mattman85 said:**
> Is it possible to just tar /home, /opt, and a couple other directories, and then save them on some medium, so that when doing a fresh install, I could just extract the folders from the tar file and keep my information?

will work with home, at least theoretically...;) I don't know what happens if you put old system folders into a newer installation, but if it is the same version re-installed, should work. One would have to be sure not to copy the broken bit back into the fresh installation...

> I also don't have the ability to create another partition on my hard drive to be able to put /home on it.. but yes, I looked into that route, as well.

Don't know how
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
or no room?

---

### Post by mattman85 on 2010-01-19
I know how to..  I just don't have room.  My laptop only has a 120GB IDE HDD, which, between XP, Ubuntu, and an NTFS partition that houses some cross-platform data, I'm stressed for space..  Plus there is a partition that gateway preconfigured for wiping the entire HDD..  GParted won't let me have more than 4 partitions :(

---

### Post by mattman85 on 2010-01-19
> **audiomick said:**
> I don't know what happens if you put old system folders into a newer installation, but if it is the same version re-installed, should work.

I'm actually planning on downgrading from 8.10 to 8.04, as I have constant problems with Firefox and sounds..  Firefox always resizes itself outside the constraints of my screen, and I have to press F11 twice to get it back to "full screen".  I always seem to lose sound, and after running through the [Comprehensive Sound Problems Solution Guide]("http://http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound"), it is only fixed for a short time..

---

### Post by audiomick on 2010-01-19
> **mattman85 said:**
> 
 GParted won't let me have more than 4 partitions :(

It is true that you can only have 4 primary partitions. The way around that is to make (less than) 3 primaries, and an extended. Within the extended you can then make more partitions. I am not sure how many, I think 64.
There is some reading here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
particularly the links to partitioning basic and creating extended partitions.

Whether it is an option for you or not depends mostly on how physically full your drive is, i.e. if you still have empty space in your existing partitions to play around with. Also, changing around your partitions on a working system is not to be entered into without careful consideration.

---

### Post by audiomick on 2010-01-19
> **mattman85 said:**
> I'm actually planning on downgrading from 8.10 to 8.04, 

Doing that means a re-install, which would allow you to start using extended partitions.

---

### Post by audiomick on 2010-01-19
Also, just found a useful post on the topic
[http://ubuntuforums.org/showpost.php?p=8690183&postcount=15](http://ubuntuforums.org/showpost.php?p=8690183&postcount=15)

---

### Post by mattman85 on 2010-01-19
> **audiomick said:**
> It is true that you can only have 4 primary partitions. The way around that is to make (less than) 3 primaries, and an extended. Within the extended you can then make more partitions. I am not sure how many, I think 64.
There is some reading here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
particularly the links to partitioning basic and creating extended partitions.

Whether it is an option for you or not depends mostly on how physically full your drive is, i.e. if you still have empty space in your existing partitions to play around with. Also, changing around your partitions on a working system is not to be entered into without careful consideration.

I know...  my NTFS DATA partition is a logical partition inside of an extended partition.  the issue is that I don't have space for anything other than the 3 primary and extended, which only had enough space for me to add the data partition.  I think there is about 15 or 20MB unallocated space on the disk.  I had to rework windows and ubuntu's allocation of free space just so I could get enough free space in one spot to be able to chunk it into an extended partition, and then create a logical partition..

the overall issue here is that my laptop is almost 5 years old :-(  I don't get paid enough at the school district as an IT specialist to be afford a new computer, when my wife and I have a baby boy due around May 24th (^.^)

anywho..  thanks for the help, everyone..  I guess I'll tinker with trying to compress /home at least, and then boot into a liveCD on my district macbook pro and see if uncompressing will let all of my stuff show up..  not too sure of how else to test it, really..

---

### Post by audiomick on 2010-01-19
What about an external drive? Costs a lot less than a new box, and might relax your space problems a bit.

---

