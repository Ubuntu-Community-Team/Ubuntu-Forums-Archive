---
title: "Can't find any partition for Ubuntu"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by mickelsen on 2010-03-10
I have a blank, 250 GB hard disk and I want to use the whole thing to install Ubuntu on my new shop computer. I have the LiveCD with ver. 8.04.0 and Emc2, which boots just fine. When the installation gets to part about setting up the partitions, the partition table is blank. I reformatted the entire disk using my Windows XP installation disk, but the Ubuntu installation program still can't find it. I'm baffled. Can anyone give me a clue as to what might be wrong? Is there a Linux utility that I could use to format or setup the disk for Linux installation? Any help will be greatly appreciated.
Mark

---

### Post by n0dix on 2010-03-10
The utility can be Gparted. Additionally it's strange that LiveCD don't recognize Windows partition. Try with a recent LiveCD version.

---

### Post by mickelsen on 2010-03-10
Gparted doesn't find anything to work on, either.  This is really strange!  The XP installation disk sees the partition just fine.
Do you know what the most recent LiveCD version is?

---

### Post by n0dix on 2010-03-10
Stable version is 9.10

---

### Post by mickelsen on 2010-03-11
Okay. The 9.10 Gparted can see the hard disk. It has one partition at /dev/sda1 and one block of unallocated space sized about 7.84 mb. Windows always leaves a block like that. I don't know for sure, but I think that may just be lost at this point.
 
I'm hoping that I can partition the disk using the 9.10 Gparted and then go back to 8.04 and it will be able to see the disk then. I would like some guidance as to how to partition the disk. I would think that I should make a "/" file system and a swap area. Once I decide how big the swap space should be, then everything else should go into "/". I THINK I can wait until later to allocate part of "/" to "/home".
 
(Please, everybody, feel free to jump in and tell me how wrong I am, if I am.)
 
Could somebody tell me if this is a good approach, and how much swap space I should have? And can I do what I'm talking about with Gparted?
 
Thank you very much for the help.
Mark

---

### Post by mickelsen on 2010-03-11
I see that Gparted can create partitions of several different types; msdos, aix, etc. What is the best type of partition to use for Ubuntu?

---

### Post by mikewhatever on 2010-03-11
The partition for Linux should be in a Linux format, ext4, if you want to use 9.10 (Karmic), ext3. if you want to use 8.04. 
The size of swap depends on the amount of RAM, which you didn't specify. If I had to guess, 1GB should be optimal.
Since you know you'll want a home partition, there is no reason not to create it now.

---

### Post by mickelsen on 2010-03-11
Okay. So now I have a disk that is 232.88 GiB of unallocated space. The only operation it will allow me to do is create a new partition table. I can select a new partition table type from the following: msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun, or loop, and it warns me that it will immediately erase all data on the entire disk (not that I care in this case). Which one should I chose?

---

### Post by mikewhatever on 2010-03-11
What are you using to create partition?

---

### Post by mickelsen on 2010-03-11
I am using the Gparted that is available on the Ubuntu 9.10 LiveCD.

---

### Post by n0dix on 2010-03-11
But, you can do the same when you going to install Ubuntu.

---

### Post by Arand on 2010-03-11
msdos is the most commonly used partition table and presumably what you would want to use if it it comes down to rewriting the partition table.

Just in case, you need to select (click) the empty space in gparted to create a new partition, otherwise all options apart from partition table creation will be unavailable.

- Arand

---

### Post by leorolla on 2010-03-11
To be sure, what do you see after

```
sudo fdisk -l
```

?

---

### Post by mickelsen on 2010-03-11
Well, I'm confused! I've used the 9.10 Gparted to create an ext3 file system using all the space on the disk. It says that it is at /dev/sda1. I haven't tried to create a swap space or "/" or "/home" partitions because I'm unsure how to do it. I want to install Ubuntu ver. 8.04.0 with Emc2 preinstalled on the LiveCD since Emc2 needs to be tightly coupled with Ubuntu when it's installed. But when I go back to the 8.04.0 LiveCD and try to install it, it can't see any file system on the disk, and it can't create one. I can't see any way to get to a command line to run fdisk. I realize that I'm just a newbie and that I'm probably missing something very easy and basic, but please point it out to me because I AM missing it.
Thanks,
Mark

---

### Post by Arand on 2010-03-11
The terminal can be started from menu *applications>accessories>terminal

But that 8.04 is unable to detect any partitions seems to point at other problems, fdisk might come up blank as well, but do try it...
- Arand

---

### Post by mickelsen on 2010-03-11
Okay, I've had it.  There's something wrong with that drive!  I have another one.  It's only 160 GB but it will have to do.  I'm trying it now.  The 8.04 Gparted can see  it right off, so that's encouraging.  I'll report back and let you know, especially if I need help with swap space, etc.
Thanks for your help up to now.
Mark

---

### Post by mickelsen on 2010-03-11
I changed the drive out and suddenly everything went smoothly.  I installed ver. 8.04 on my system with no problem.
Now I've got to learn some basics.  I want to download some programs such as VirtualBox, but I don't know how to create a new folder to put them in.  I bring up the file browser and click on my user directory, /home/mark, click on the file command, but the "create folder" command is shadowed out.  I want to create a "downloads" folder to put various downloads in, but I don't know how.  Can someone tell me how to do this, and where to find some basic documentation to look up how to do stuff so I'm not always whining to you guys with each little thing?  I know you'll find this hard to believe but I'm actually fairly computer literate.  Right now I just don't know where to look for even the basics for Linux and Ubuntu.
Thanks again for the help.
Mark

---

### Post by n0dix on 2010-03-11
For download packages the best is using Synaptics. 
Here's an interesting [link]("http://ubuntuguide.org/wiki/Ubuntu:Karmic").

---

### Post by presence1960 on 2010-03-11
> **mickelsen said:**
> Okay. So now I have a disk that is 232.88 GiB of unallocated space. The only operation it will allow me to do is create a new partition table. I can select a new partition table type from the following: msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun, or loop, and it warns me that it will immediately erase all data on the entire disk (not that I care in this case). Which one should I chose?

make the new partition table msdos and click the green check mark to apply. Now that you have a valid partition table create the partitions as mikewhatever advised you to do.

---

### Post by srs5694 on 2010-03-11
I realize it's late for the OP, but there's some serious confusion in this thread about some basics.

First, there are two independent sets of names being used: Partitioning scheme labels (msdos, gpt, aix, etc.) and filesystems (ext2, ext3, etc.). These are two *entirely independent* concepts. A partitioning scheme determines what data structures are used to define where each partition begins and ends, what type it is, etc. Currently, the Master Boot Record (MBR) system is the most common, but it goes by several other names; it's called "msdos" by GNU Parted and related utilities. MBR is on its last legs, though; there's a transition underway to the GUID Partition Table (GPT) system, which handles bigger disks, does away with some MBR flakiness, and is (theoretically) more robust against certain types of problems. For a Linux-only system, I slightly favor GPT, but if you want to multi-boot with Windows, MBR will cause fewer problems. (Selecting MBR for a Linux-only system is fine, but as I say, GPT has some advantages, such as redundant partition tables for increased reliability.)

The second set of names being tossed around refer to filesystems. These are data structures that reside *within* partitions to help the computer identify individual files and directories. I don't recall precisely what Ubuntu supports "out of the box," but common filesystems for Linux include ext2fs, ext3fs, ext4fs, ReiserFS, JFS, and XFS, with Btrfs being the up-and-coming filesystem that's still too new to be recommended but that may take its place as a major one in a few months. Ext2fs lacks a journal and so will be slow to recover after a power failure. This makes it unsuitable except on small volumes (say, a separate /boot partition). Any of the rest can be good choices, with ext3fs, ext4fs, and ReiserFS being generally favored for general use and ext4fs, JFS, and XFS being well-suited for very big volumes (multiple terabytes) and/or for handling very big files (roughly a gigabyte or more).

Linux installs itself to a main partition, which contains a filesystem. This is the "root directory" (also written as "/"). Other partitions, which also contain filesystems, may be "mounted" on root, whereupon they're accessed as directories of root (or of one of its directories). This can be done for /home, /usr, /usr/local, /var, or various other directories. Swap space also occupies a partition, but it's not mounted in this way. In Linux, each partition is referred to as a device file with a number following the main device filename. For instance, /dev/sda (a whole disk) may contain /dev/sda1, /dev/sda2, and /dev/sda3 (three partitions, each with a filesystem or swap space). Thus, when mickelsen wrote...

> I've used the 9.10 Gparted to create an ext3 file system using all the space on the disk. It says that it is at /dev/sda1. I haven't tried to create a swap space or "/" or "/home" partitions because I'm unsure how to do it.

...he was most probably confused about the nature of partitions and mount points. Once /dev/sda1 is created and occupies all the space on the disk, it becomes impossible to create additional partitions on the disk to hold other filesystems or to be mounted anywhere else. (Unless this is an LVM configuration, which is a whole 'nother kettle of fish!) Presumably /dev/sda1 would become root (/) and there'd be no other /home partition, unless it were to be created on another physical disk.

My suspicion is that mickelsen's first disk is fine, but he did something different with the installer that caused it to complete more smoothly after he replaced that disk with another one. There are options to do things with varying degrees of automation, for instance, and if an advanced option were selected the first time around, it'd be easy to mess things up if one didn't know what one was doing.

Finally, the term "format" is loaded with confusion. It can refer to a low-level format (something that's done at the factory and never again on hard disks, but that's common on floppy disks) or a high-level format ("creating a filesystem" is the preferred terminology in Linux). Some users use "format" to refer to creating partitions, but this just adds to the confusion.

---

### Post by mikewhatever on 2010-03-12
> **mickelsen said:**
> I changed the drive out and suddenly everything went smoothly.  I installed ver. 8.04 on my system with no problem.
Now I've got to learn some basics.  I want to download some programs such as VirtualBox, but I don't know how to create a new folder to put them in.  I bring up the file browser and click on my user directory, /home/mark, click on the file command, but the "create folder" command is shadowed out.  I want to create a "downloads" folder to put various downloads in, but I don't know how.  Can someone tell me how to do this, and where to find some basic documentation to look up how to do stuff so I'm not always whining to you guys with each little thing?  I know you'll find this hard to believe but I'm actually fairly computer literate.  Right now I just don't know where to look for even the basics for Linux and Ubuntu.
Thanks again for the help.
Mark

I don't think clicking on a folder will create more folders, not even in Windows. You have to either right click on the white space inside /home/mark, or select File->Create-Folder from the file browser menu. The important part is, you must be in /home/mark.

---

