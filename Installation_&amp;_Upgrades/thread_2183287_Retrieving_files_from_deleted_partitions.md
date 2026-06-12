---
title: "Retrieving files from deleted partitions"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Dustin_Whisenhunt on 2013-10-24
When I went to install 13.10 I chose the option to remove windows and replace with Ubuntu. I had two partitions when I chose this. One with files I wanted to keep and the other being the windows 7 partition. When I chose to remove windows I assumed it would be placed on my C drive and not my other one. But what actually ended up happening was all my partitions merged into one deleting everything. Now I only have Ubuntu on my drive. I need help retrieving my files please!

---

### Post by amjjawad on 2013-10-24
Hello and Welcome :)

> **Dustin_Whisenhunt said:**
> When I went to install 13.10 I chose the option to remove windows and replace with Ubuntu.

You have chosen that yourself. The system did not choose it for you :)


> I had two partitions when I chose this. One with files I wanted to keep and the other being the windows 7 partition. When I chose to remove windows I assumed it would be placed on my C drive and not my other one. But what actually ended up happening was all my partitions merged into one deleting everything. Now I only have Ubuntu on my drive. 

Any Operating System in the world will wait for you to enter any command that to be executed and run by that system. The system does not know you have assumed. It knows only what you are giving to it. You should have simply backed up your files before doing anything :)

> I need help retrieving my files please!
If your HDD is wiped now, I am not too sure how exactly you are going to get your files back that you didn't backup before the installation and assumed the system will back them for you.

---

### Post by Melodie on 2013-10-24
> **Dustin_Whisenhunt said:**
> I need help retrieving my files please!

As amjjawad said you really should have done a copy of your personal data on another media before starting! Never forget that even if you don't mistake while partitioning you could be victim of a power supply shutdown or any trouble related to electricity and or electronics.

There is a way for you to revert back to what it was: when a new partitioning is done, a new partition table is created, which is added on top of the former one, such as tracing paper. 

The program having for name "testdisk" can help you revert back to the former table partition. This is a command line tool, and not really easy to deal with, but if you don't partition again, if you follow a good tutorial and you are very precise following it well you can succeed.

Info about testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You have it available in many rescue CD's. One I would suggest is Parted Magic:
[https://partedmagic.com/](https://partedmagic.com/)

You have a choice among a bunch here:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

You can watch and read about how to use it here and here:
[http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)

[http://www.maketecheasier.com/recover-data-and-partitions-for-free-with-testdisk/](http://www.maketecheasier.com/recover-data-and-partitions-for-free-with-testdisk/)

Please keep in mind that "c:" does not exist in the linux world : we use "/dev/sda" for the first hard drive, "/dev/sdb" for the second hard drive and so on... same for usb sticks, it can be /dev/sdb, or /dev/sdc if there are two hard drives.

The partitions of a hard drive will be /dev/sda1 then /dev/sda2, and if there is an extended partition it will be /dev/sda2 and the first logical partition will be /dev/sda5.

---

