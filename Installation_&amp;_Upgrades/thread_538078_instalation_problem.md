---
title: "instalation problem"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Raymondpaul on 2007-08-29
when i try to install it say loading linux kernal 100% then after a couple minutes it says error reading boot 
disk does anyone know what is wrong with it?

---

### Post by Pumalite on 2007-08-29
Post specs. What are you using: Live CD? Alternate?

---

### Post by Raymondpaul on 2007-08-29
live cd 

AMD Athlon 64 processer 1 gig of memory 300 gig hardriver

---

### Post by kellemes on 2007-08-29
Maybe a bad burn?

---

### Post by Raymondpaul on 2007-08-29
idk i tried i to different disk and same error

---

### Post by Raymondpaul on 2007-08-29
the computer im trying to install on isnt connected to the interent would that cause any problems?

---

### Post by Pumalite on 2007-08-29
Do md5sum on iso, burn at 4x. What about graphics?.

---

### Post by Raymondpaul on 2007-08-29
um i dont realy rember but i know its an nvidia graphis card

---

### Post by Pumalite on 2007-08-29
It is important to you as well as us (to help you) to know exactly what card you have. Check your Manual or your boxes and try to find out. It's convenient to be connected to the Internet, but in most cases you can complete an installation without Internet. In some special cases, the installer keeps trying to find the connection to Internet.

---

### Post by Raymondpaul on 2007-08-29
i have nvidia gforce fx 5500 graphics card

---

### Post by Pumalite on 2007-08-29
Well, that cannot give you the error that you reported. Have you tried downloading a new iso, doing md5sum, burning at 4x?

---

### Post by TechYesLogic on 2007-08-29
I plan to install Ubuntu.
I have a 160GB and 40GB HDDs. (160GB-WinXP and 40GB-Win98)
I have 10GB unallocated space(meant for installing ubuntu).

I've read the official Ubuntu book and got some idea of installing.
Will this 10GB unallocated space be shown in the partition manager?

And also, in windows, FAT32 partitions are not able to access NTFS systems.
Again, if i install ubuntu on a FAT32 partition, will it be able access NTFS partitions?
OR
Installing on 'ext3' will allow me to access both FAT32 and NTFS or NTFS ONly....???

I know its a lengthy query, but, please somebody help me...

---

### Post by merlinus on 2007-08-29
First of all, it would have been better to start a new thread rather than jump into this one with a different situation.

Nevertheless...

fat32 and ntfs are for windows.  You cannot (thankfully!) install ubuntu on to those.  It uses ext3 or other linux filesystems only.

During installation, the partitions will be formatted accordingly.

There are drivers that you can install so ubuntu can write to NTFS.  It can write to fat32 without these.

You can also install drivers so windows can read and write to ext3.

-merlin

---

### Post by Pumalite on 2007-08-29
You are highjacking this thread, but I'll tell you a couple of things. First: 10 GB is pretty slim pickings for an Ubuntu installation. You cannot install Ubuntu in a Fat32. Third: you cannot install in an unallocated space; use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to make a partition. Installer will format as appropriate.

---

