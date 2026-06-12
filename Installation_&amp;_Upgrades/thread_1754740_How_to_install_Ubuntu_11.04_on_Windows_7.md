---
title: "How to install Ubuntu 11.04 on Windows 7"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by da007man on 2011-05-10
Hi, I just downloaded and put on a USB key ubuntu 11.04. However when I did the installation process, it told me that it would erase my Windows 7 OS. But, I want to keep windows 7 and install Ubuntu 11.04 with it. How do I do that? I went in the partition section and did not know what to do. Please help! :)

---

### Post by Rubi1200 on 2011-05-10
Hi and welcome to the forums :)

When you start the USB choose to try and not install Ubuntu. When you get to the desktop open a terminal with Ctrl+Alt+T and copy this command:

```
sudo parted -l
```
Press Enter for the command to run. When you see the output you can copy/paste from the terminal into a new post here so we can get an idea of your setup.

Thanks.

---

### Post by da007man on 2011-05-10
Model: ATA ST9320325AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  316MB  315MB   primary  ntfs         boot
 2      316MB   302GB  302GB   primary  ntfs
 3      302GB   318GB  16.1GB  primary  ntfs
 4      318GB   320GB  2142MB  primary  fat32        lba


Model: USB Flash Disk (scsi)
Disk /dev/sdb: 2005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      262kB  2005MB  2005MB  primary  fat16        boot

---

### Post by Quackers on 2011-05-10
Your hard drive appears to be filled with partitions :-)
It doesn't matter that there may be free space within one or more of them. There is nowhere for Ubuntu to install to :-) Ubuntu cannot use a NTFS partition.
But the main problem is that you have 4 primary partitions. This is the maximum number of primary partitions on any single disc which is formatted in the mbr partition system.
Therefore you can't just make some free space by shrinking a partition.
To install another operating system to that disc you will need to delete one of the primary partitions (be careful which one!!!). Then you can create some free space by shrinking a partition and then you can create an extended partition (which is a different kind of primary partition) to occupy that new free space. 
Then within that extended partition you can have as many logical partitions as you like, inside which you can install other operating systems.

The installer is stopping you from creating a 5th partition - which would be bad!

---

### Post by da007man on 2011-05-10
Uh....yeah I think I'll bring my computer in so that someone can do it for me :P Or is it easy to do?

---

### Post by da007man on 2011-05-10
I'll formulate the question differently... How do you do it properly and safely? Because I want to intall and use Ubuntu REAL BAD :)

---

### Post by Rubi1200 on 2011-05-10
The first thing to do is backup all important data before making any major changes to the system.

Then, if you don't already have one, create a Windows recovery disk that you can use in the event something goes wrong:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Do some reading before you jump in and start partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Finally, read about dual-booting and look at some guides:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by da007man on 2011-05-10
Thanks :) I'll read it and do what I can. How can you install ubuntu on an external drive?

---

### Post by Quackers on 2011-05-10
The order would be something like this imo.
Decide which partition you can do without.
Backup what you may need from within that partition.
Make a Windows repair disc (if you don't have a Windows installation disc). A recovery dvd is NOT the same thing!
Delete the partition from within Windows (Disk Management console)
Depending on which partition you delete and whether it gives you enough space for Ubuntu or not.

a) Not enough space  -  defragment the C: partition in Windows.
   Shrink the C: partition with Windows Disk Management Console.
   Reboot twice to make sure Windows is still happy.
   Boot from the Ubuntu live cd/usb and choose the "install alongside" option

b) Enough space for Ubuntu after deleting the partition  -  boot from the  
   Ubuntu live cd/usb and choose the "install alongside" option

If you get stuck anywhere, ask again :-)

ADDED  You could install to an external drive (unless that too already has 4 primary partitions - which is unlikely).

---

### Post by Rubi1200 on 2011-05-10
In the second guide I linked to in the section on dual-booting there is also a tutorial on how to install to a second drive.

There is another option available if you are not ready to deal with deleting and creating partitions just yet and that is to install Ubuntu using Wubi. Basically, this creates a virtual file inside Windows that allows you to try Ubuntu without all the fuss of partitioning.

Here is the guide for that:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by da007man on 2011-05-10
Thanks :)

---

