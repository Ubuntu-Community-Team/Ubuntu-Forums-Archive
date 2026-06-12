---
title: "Resizing NTFS - claiming I only have 8Mb free, when I have about 40Gb!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Drakelet on 2008-04-28
I'm trying to resize my HDD so I can install Hardy, but am having problems.

I currently have Windows XP, taking up about 40Gb on an 80Gb NTFS HDD.  I want to resize it into 10Gb for /home, 10Gb for / and the rest for Windows.

When I try, in both Hardy built-in or in GParted from System Rescue CD, it claims I only have 8Mb of free space.  So, I can't resize.

Any ideas why?  This is bloody annoying.

---

### Post by housam on 2008-04-28
Before doing anything defrag your HDD 2-3 times and backup your data. then use the [[COLOR="Red"]_new version of Gparted_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") tool ( download and burn to a CD then boot from it ) to resize the windows partition and create the partitions you need.

---

### Post by Moop on 2008-04-28
Make sure the partition is unmounted before you try resizing. The 8mb of free space is unpartitioned space windows uses for boot files or something like that. Gparted is looking in the wrong place.

---

### Post by Drakelet on 2008-04-28
EDIT: Gonna take it to another thread.  Question answered, close if you want.

Well, I defragged 5 times and chkdik'd, and it's worked.  Now I have a new problem - getting online with my dial up Intel 536EP.  It just won't seem to work.

I've put in all the details under serial modem.  I've tried all the modem ports, but none seem to work.
Do I need to install it extra?  I've looked up the Intel536EP help page, but it didn't seem to help much - I want to install it through the Network thing (only way I can really).

EDIT: I forgot to say, it's 64bit Hardy.  I think I read 64bit doesn't work with the 536EP.  If so, ****!

Any thoughts?  Ask questions if you need to. :D

---

### Post by housam on 2008-04-29
Scan your modem using the [[COLOR="Red"]_ScanModem_[/COLOR]]("http://132.68.73.235/linmodems/index.html#scanmodem") tool which will give you information about your modem and the required driver needed to activate it.

---

### Post by housam on 2008-04-29
You can also check [[COLOR="Red"]_this thread _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=210405&highlight=install+modem+driver"). It is about activating the modem Intel 537EP

---

### Post by Drakelet on 2008-04-29
Oh OK, thanks you two.  Will try those now.  Although I have the 536, not 537.

---

