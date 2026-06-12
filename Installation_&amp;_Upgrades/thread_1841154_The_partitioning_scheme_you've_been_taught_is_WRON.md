---
title: "The partitioning scheme you've been taught is WRONG"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by jwcalifo on 2011-09-08
Sorry for the dramatic title, but its true. I completely disagree with the idea of segmenting a single hard drive into multiple partitions. When using a single disk, separating system binaries and program binaries PHYSICALLY, using partitions, from things like data files like video files is a mistake.
 
For example, say that you have /usr on one partition near the beginning of the disk and /home on another partition near the end of the same physical disk. You double-click on a video file, located in /home/$username/Video, and the file opens in your video editing program, located in /usr/bin/[programname]. The disk has to move first to the beginning of the disk to load program binary data, then all the way to other end of the disk, perhaps on a different platter, to access the video file data. It might have to do this back and forth action several times before the file is fully loaded in the editor. This delay is called reduced performance.
 
Now, if you have two controllers, then it makes perfect sense to split these things up.
 
:grin:

---

### Post by agillator on 2011-09-08
To each his own. To begin with, drives are so fast today I'm not sure the time of moving really amounts to that much. Second, there are a number of reasons to use multiple partitions. For example, splitting the directory tree over several partitions can help a great deal and save hours if you update/upgrade your system periodically. So it really boils down to your priorities and your experiences. In my mind, no 'system' of partitioning is right or wrong, just matter of what works for you.

---

### Post by tgalati4 on 2011-09-08
If you are doing video editing, then you have lots of RAM.  Plus, if you know something about RAMdisks, then you will set one up for your editing sessions anyway.  I use firefox with a RAMdisk and it's much faster than writing the cache to disk.

If you do your video editing frequently and directly to disk, then you will thrash your disk regardless of the partitioning scheme.

---

### Post by fdrake on 2011-09-08
> **jwcalifo said:**
> Sorry for the dramatic title, but its true. I completely disagree with the idea of segmenting a single hard drive into multiple partitions. When using a single disk, separating system binaries and program binaries PHYSICALLY, using partitions, from things like data files like video files is a mistake.
 
For example, say that you have /usr on one partition near the beginning of the disk and /home on another partition near the end of the same physical disk. You double-click on a video file, located in /home/$username/Video, and the file opens in your video editing program, located in /usr/bin/[programname]. The disk has to move first to the beginning of the disk to load program binary data, then all the way to other end of the disk, perhaps on a different platter, to access the video file data. It might have to do this back and forth action several times before the file is fully loaded in the editor. This delay is called reduced performance.
 
Now, if you have two controllers, then it makes perfect sense to split these things up.
 
:grin:

this would happen even if you have 1 unique LARGE partition .... DATA IN THE HHD AREN'T WRITTEN 1 NEXT TO EACH OTHER. they are spread out in the remaining space.

---

### Post by jwcalifo on 2011-09-08
Yes, but moving over one cluster is much different from moving over one platter.

---

### Post by fdrake on 2011-09-08
> **jwcalifo said:**
> Yes, but moving over one cluster is much different from moving over one platter.

agreed , and that's when the swap partition plays an important role in the game.

in the end like everything is to find your right balance between security/recovery and speed/performance. which one is more important to you?

---

### Post by ottosykora on 2011-09-08
@jwcalifo

sorry, but saying it is wrong to partition is in itself wrong.

There are many good reasons for having data partition and system partition separate, as well as having separate partitions for other variables.

You are probably thinking, that if all is in one partition on a disk, then all is close together and so the mechanical seek will be shorter. Many people think that, as they have been watching defrag under DOS so often.
Under DOS based file systems, well the data is written starting from beginning of the partition. When anything is changed, then it has to be written to new location and the file allocation table has to be updated! There are two copies of it, so both have to be updated. So where ever the file is located, the head has to move to the particular information in the file allocation table and then to the sector the part of that file is located. So it will move all over the partition anyway back and for.
If all stored in one big partition, the movement even here will be probably bigger then between two adjacent partitions ;-)

In linux systems, the files are deliberately written over large area, leaving big gaps between the used parts. This is particularly so with ext2 and ext3. This is done so there is enough 'spare' space between the files to accommodate any changes without the need to move anything or defrag.

And furthermore, today we are not really able to tell where physically the data on the hard drive are stored exactly. The controllers inside the drive are so smart, that placement of any data can take place almost anywhere as big space reserves are kept on the physical surface of the drive to compensate for lost or damaged parts and all this dynamically moved around.


So yes, your theory would be correct if stated in 1987 to some extend, but is definitely not valid in 2011.

---

