---
title: "Partition and format strategy for dual booting"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by raymond3 on 2007-03-14
I'm building a PC that will be used mainly as a Linux desktop but I will also boot into Windows XP for Photoshop and color matched printing work (I'm a pro photographer).

I have two 500 gb SATA drives and two 200 gb ide drives.  I want all data to be readable and writtable by both operating systems.  Does windows handle ext3 better than Ubuntu handles NTFS?

Right now I am planning on setting up 2 100 gb partitions on one of the SATA drives to install Windows and Ubuntu in.  The rest of that drive and the other 500 gb drive is available for data or ???

The IDE drives currently have data on them and are NTFS but they can be backed up and changed to something else if it's better.

Photoshop works best when its "scratch drive" is set to a drive other than the windows install so I will need another NTFD partition somewhere off of the first SATA drive.

I guess I just need some pointers on getting this setup for the best performance and reliability.

Thanks!!!

Ray

---

### Post by raja on 2007-03-14
I dont know about windows and ext3, but have been using ntfs-3g to write in NTFS partitions with Ubuntu and it seems to be pretty stable now.

---

### Post by raymond3 on 2007-03-14
Do you know if I would be able to share the mounted NTFS partition with SAMBA over my network?  For example, I'm booted into Ubuntu, have the 500 GB NTFS drive mounted and am sharing a folder of MP3 files to other computers on the network.

---

### Post by Enki on 2007-03-14
I've had mixed results with write access to NTFS from linux. Haven't tried the EXT2 driver for
 Windows, but I'm worried it might mess up permissions and generally don't like the idea of malicious code under Windows having access to my Linux data. Read access either way shouldn't be a problem, if you don't mind copying your files around. Ubuntu comes with NTFS read capabilities, for the other way around, there's [Linux Reader]("http://www.diskinternals.com/linux-reader/"). If your files don't exceed 4GB, a shared FAT32 partition would be the best option.

Based on experience with a similar setup, and supposing you want maximum performance for Photoshop, I'd go for something like this:

first harddisk:
40GB NTFS Windows (plenty of room for OS + programs)
300GB FAT32 (PSD files)
30GB EXT3 Ubuntu / (more than you need, but since you have 1000GB...)
100GB EXT3 Ubuntu /home (for everything but your .PSDs)

second harddisk:
2GB FAT16 for Windows swap (if you need more, go for FAT32)
10GB NTFS/FAT32 PS scratch
2GB Linux swap
rest: EXT3 temporary backup/or leave unused until you really need it

---

### Post by Rotaj on 2007-03-16
I am looking to do something similar with my home system. The question that comes to mind is how do you do the FAT32 format. Is that done from XP, Ubuntu or an older MS product?

---

### Post by Pumpkin Eater on 2007-03-21
Rotaj:

I used XP's partition manager to reformat an ext3 partition as fat32 for use as a common partition for XP and Ubuntu.  Don't do what I did!  It renumbered my partitions (sda2 became sda4 etc.) which meant that Ubuntu tried to use with Win partition as Swap space.  I don't know if any damage was done, but the result was that Windows would no longer boot.  

Use Gparted (off the Live CD) instead. 

I hope my reply is not too late!

---

