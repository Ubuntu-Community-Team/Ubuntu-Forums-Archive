---
title: "Run 'Live Linux' on external SSD rather than USB stick?"
date: 2017-03-31
forum: Installation &amp; Upgrades
---

### Post by greengalaxy on 2017-03-31
There are many people who running Linux 'Live' rather than full install.   
'Choosing between Live USB and Full USB Installation' [https://ubuntuforums.org/showthread.php?t=2130234](https://ubuntuforums.org/showthread.php?t=2130234) 
for some of and pros and cons.  

In my case as for many others, it's because I can't get Linux to install on my NUC. 
But a USB Live version is slower than an SSD drive.  So my question, can use I use an external SSD drive, to run the live version with 'persistance'.?   I'll need to buy another  SSD drive and enclosuer, so I'm wondering, has anyone tried this?   Wouldn't it work?        

There are MANY multiboot thumb drive creators, that have persistance. I tried 'YUMI', 'LinuxLive USB Creator', and Rufus.  But they are meant for USB thumbdrives [pen drives] only.   Could any of these be made to do the same on an external SSD? Recommendations?

---

### Post by ubfan1 on 2017-03-31
Sure, there is not much difference between USB boot devices (although some external disk enclosures don't work for booting).  The SSD will be much faster than flash.  You can use mkusb I believe to set it up with persistence.  If you are going for a multiboot setup, (many ISOs to boot), and you can live with a 4G persistence size, you might make a FAT partition big enough to hold several casper-rw files in different directories and use the persistence-path=/X to select which one to use for any particular boot.

---

### Post by greengalaxy on 2017-04-01
Does the 'Live Linux' have to be on a FAT or FAT32 partition?  Or I could make it an ext3? (but I'll be partitioning from Windows, using the EaseUS partitioner.   It can do ext3, but not ext4. )
And then I'd like to partition the rest of the drive for other uses, backing up windows stuff, on NTFS partitions.  This is ok?

---

### Post by Bucky Ball on 2017-04-01
You would be better to post a thread to try and get help with why you can't install rather than going this route. A live session on an SSD with persistence??? May as well just install it because this is an ad-hoc workaround that avoids the actual problem: why can't you install Ubuntu on the SSD the regular way?

Ask that question in a new thread and you'll probably get plenty of help. That appears to be your actual issue.

---

### Post by sudodus on 2017-04-01
Yes, it works well to install a persistent live system in an SSD drive. The SSD drive can be plugged in as an internal drive, and it can be put into an external box and connected via USB and eSATA. I use such systems, where the persistent live system is created with mkusb. The advantage with mkusb is that it creates a ***partition*** for persistence, so the whole drive can be used.

See these links

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by greengalaxy on 2017-04-01
Thanks.  I will study those links!  I already tried several apps like YUMI or Unetbootin, on USBsticks, but they limit the persistence to 4gb.  And I can't open nor see into the casper-rw file to view/manipulate its contents.  
But with mksub I could create a large 20+GB partition and use all of it as a 'casper-rw' partition?  And I could open and manipulate its contents from any file manager, as one can with installed versions?

---

### Post by sudodus on 2017-04-01
Yes, if you select a GUID partition table, GPT, you can have a huge casper-rw partition, several TB. If you select the old style MSDOS partition table the maximum partition size is 2 TB, also enough in most cases. Some middle-aged HP computers refuse to boot via USB, if there is a GPT, so if you intend to run your persistent live system in such computers, you had better select an MSDOS partition table (this is one of the options, in mkusb).

And yes, you can manipulate the casper-rw partition itself, the file system and the content (files and directories) with standard tools.

---

### Post by yancek on 2017-04-01
The reason you are limited to a 4GB casper-rw is that software such as YUMI and unetbootin use FAT32 filesystems to create the bootable usb.  It's a limitation of the FAT32 filesystem.  Using a Linux filesystem lets you create any size you want and mkusb works very well for that.

---

### Post by C.S.Cameron on 2017-04-01
One way to put a persistent install on hard drive is to make the persistent install to flash drive and then clone this to the hard drive using dd. This can be done with the installers you mention, I think mkusb can install directly to SSD.

In this case it looks like you are planning on using the SSD as a permanent solution, a Full install might be a little more stable than a Persistent install and boots a little faster.

---

