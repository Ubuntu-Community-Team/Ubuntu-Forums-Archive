---
title: "Help with partitioning"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by rayhorn13 on 2007-06-02
**FYI: I am installing Linux for the very first time.**  I have been an avid Windows user for some time & actually handle most of the computer issues at work, so I may have some things pretty embedded into my thick skull & may need to be talked down to as far as the Linux Way of doing it.

I have downloaded the latest Ubuntu and have plenty of space for Linux partitions (see attachment), but I can't seem to find any specific "how to" items on EXCATLY how to create the partitions I need for Linux, what type of file system (?), a shared partition for WinXP & Linux access (?), etc.  Is there a tutorial out there that has step-by-step instructions for the very beginner in mind?  I definitely have to have a dual boot because my work applications (AutoCAD & Revit) must have Windows - or so I'm told.

Maybe I'm missing something in the ones that I've found, maybe I'm reading something wrong, maybe I'm too green for the tutorials I've found, maybe I'm too gunshy because I'm worried about screwing up the WinXP install with my work on it.  I'm not sure, but could someone please help me??

***_[SIZE="2"]THANK YOU VERY MUCH IN ADVANCE. [/SIZE]_***

---

### Post by wpshooter on 2007-06-02
My best advice to you would be to make sure that you have a good backup of any critical information BEFORE you attempt to install Ubuntu.

Beyond that, I personally do not recommend having more than 1 O/S on a machine at one time.

But good luck.

---

### Post by bulldog on 2007-06-02
More than one OS shouldn't be a problem.
The only thing I don't know what it is,is the first line in your screenshot,EISA configuration,it doesn't seem to be a regular partition,so I can't say if ubuntu will mess with it.
But if it is a normal partition,there should be no problem.
You can let the installer do the job or create some partition on forehand.
You need two partitions as a minimum,a / [root] partition and a swap partition.
Root can be from 5 - 10GB or bigger if you want,or you can create a separate /home.
And you need a swap partition of about 1GB.

---

### Post by x1a4 on 2007-06-02
Hi,

Boot to the Ubuntu CD and use 'GNOME Partition Manager' to create your partitions.  

**EDIT:** Oops, I haven't looked at your screen shot.  Your best bet is to install everything on one primary ext3 partition with (RAM x 1.5) for swap at the end.

Disregard everything below unless you get a second hard drive to install Ubuntu as it's typically better (but not required) to have one drive per OS.  Unless yu have SCSI RAID of course.

----------------------------------------------
I recommend you setup your file systems to something like this.  The below assumes that you have windows on hd0 and want to install Ubuntu on hd1

(hd1,0) 4GB extended partition with the following volumes: 
**2GB ext3** file system mounted on **/boot**
**2GB ext3** mounted on **/root**

(hd1,1) 20GB extended partition with the following volumes
**10GB ext3** mounted on **/var**
**10GB ext3** mounted on **/tmp**

(hd1,2) remaining space less (RAM x 1.5) extended partition with the following volumes: 
**/home**  --this way, should you switch operating systems you will have your files preserved
**/**
You might want to use the **ReiserFS** for these two.  

An alternative is to create a /docs (documents) file system (what I have) and the rest (including /home) on root (/), then just create a symlink to /docs in /home/$USER

You might also create a vfat volume here to share with windows but that's not necessary.  When I was dual-booting I installed the **ntfs-3g** file system and used it to mount my windows ntfs partitions.  ntfs-3g comes with both read and write support.  

Finally, 

(hd1,3) primary partition
**(RAM x 1.5)GB** for **linux-swap**


Additional notes: 

Depending on how you're using your computer you might want to create more specialized volumes as well.  After getting rid of windows I used the space on the now-formally windows drive to store backups, encryption keys, ISOs etc.

Keep in mind that you can only have 4 primary partitions.  One extended partition counts as one primary.  But it can have multiple volumes.

---

