---
title: "How to move files in FAT32 so can resize"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by mspohr on 2006-07-01
I have a WinXP system with a 20 Gig HD (FAT32) that is less than half full but files are spread all over the disk (as viewed in the Windows defragmenter).  Problem is that I want to move these files so I can free up 10 Gig for Ubuntu.  The auto install tells me that I can only make an 8 Meg partition.  
Running Gparted from Ubuntu 6.06 live CD also tells me that I can only resize to make an 8 Meg partition. Gparted also gives me a warning and tells me that I don't have all the tools installed and that I need to install the correct plugin for this file system (FAT32) but no clue on what that might be.  I did check in the package manager and I do have the dosfstools installed but I don't know if this is the "plugin". 

Is there a utility that will move these files so that I can get a reasonable size partition?

---

### Post by aysiu on 2006-07-01
Can't you just run Windows defragmenter on it--instead of using the defragmenter program to just *view* the partition?

---

### Post by nickpaton on 2006-07-01
To add to the previous reply, rather than using the XP defragmenter which doesn't work that well, try the 30 day evaluation version of Perfect Disk which can be found at:

[http://www.raxco.com/](http://www.raxco.com/)

If you are still using XP (:mad: LOL) you will find Perfect Disk does a superb defrag job on it.

---

### Post by mspohr on 2006-07-01
I have run the Windows defragmenter on this partition several times but it still leaves files spread all over the disk (and even leaves fragmented files).  Like most things Windows, it doesn't work very well.

I'll give the Raxco PerfectDisk software a try.  Thanks for the tip!
I have a very old version of PartitionMagic (v3) but it doesn't support WinXP so I'm afraid to use it.

---

