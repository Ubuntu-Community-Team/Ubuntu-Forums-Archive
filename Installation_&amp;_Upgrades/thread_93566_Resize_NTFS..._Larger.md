---
title: "Resize NTFS... Larger?"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by akniss on 2005-11-22
Okay... I screwed up and was wondering if anyone had done/seen this before.  I have been playing around with Breezy for a while, and decided to set up my new Dell laptop with a dual boot (Breezy/XP).  I first upgraded my XP Home (preinstalled) to XP Pro, everything worked well.  I then used the Breezy installation CD to resize the NTFS partition down to 16 GB.  I created a swap partition of 1 GB, a partition for Breezy (ext3) of 12 GB.  I was planning on using the rest of the disk for file storage (FAT32) for both OS's.  I forgot one important detail when setting this up... FAT32 partitions can only be 32GB in size.  Which means now I've got almost 16GB of free space that I can't use (what a waste?)  So my question is: can I wipe out all partitions except the 16GB NTFS where XP Pro resides, and use the Breezy install partitioning to INCREASE the NTFS partition size?  Here is what I would like to do:

Total: 80 GB (70GB is useable)
XP OS NTFS: from 16 GB to 20 GB
Ubuntu ext3: from 12 GB to 20 GB
Swap: stay at 1 GB
FileStore FAT32: stay at 32 GB (or whatever is left)

---

### Post by magicfab on 2005-11-22
I don't see any reason why you wouldn't be able to do that. Usual precuations apply:
- Defragment 
- Check for errors
- Backup

I've done dozens of resizing of NTFS partitions (really), although not to increase size.

---

### Post by akniss on 2005-11-22
The good news is there really isn't anything to backup... I only want to prevent losing my XP install for the Dell installed drivers, programs, etc.  Worst case scenario I could wipe clean and do a fresh install of XP Pro, but finding all the drivers for the laptop is an absolute pain in the @$$.  (Whoever said windows 'just works' has never installed XP clean without the preloaded mfr drivers!!!)

---

### Post by akniss on 2005-11-22
One other question:
I've read that using FAT32 as primary storage location is not a good idea since it is not a journaled file system.  Is there any other way to share *all* my files between linux and windows?  I have never had any luck keeping track of different versions of documents, moving them from one storage location to another.  I just want one place to store all my files, so they are accessable to both OSs.  Any thoughts on why I should/shoudn't ust FAT32 for this reason?  I will say that I've got an external hard drive that I can format to NTFS or ext3 (or any other for that matter) to use as a regular backup location.

---

### Post by Emerzen on 2005-11-22
Sort of indirect questions to some of your concerns as a fellow Dell owner:

-Dell maintains all the necessary drivers and software for your box on their website...log in and put type in your "service code" then go to downloads.  I've reinstalled Windows several times and go to the website for all needs (also get the latest drivers).

-Fat32 is not journalled, you are correct...so greater chance of data loss if your PC crashes...also, there is a 4Gb maximun to any one file...if you are not writing multimedia to this area, it's usually not a problem though.  There are tools to allow Linux to write to NTFS...search "write NTFS" here and that should be fruitful.  I've also heard of Windows software that allows you to read/write to ext3...I would google this one or checkout [www.tucows.com](www.tucows.com)

---

### Post by crispingatiesa on 2005-11-22
[QUOTE=akniss]Okay... I screwed up and was wondering if anyone had done/seen this before.  I have been playing around with Breezy for a while, and decided to set up my new Dell laptop with a dual boot (Breezy/XP).  I first upgraded my XP Home (preinstalled) to XP Pro, everything worked well.  I then used the Breezy installation CD to resize the NTFS partition down to 16 GB.  I created a swap partition of 1 GB, a partition for Breezy (ext3) of 12 GB.  I was planning on using the rest of the disk for file storage (FAT32) for both OS's.  I forgot one important detail when setting this up... FAT32 partitions can only be 32GB in size.  Which means now I've got almost 16GB of free space that I can't use (what a waste?)  So my question is: can I wipe out all partitions except the 16GB NTFS where XP Pro resides, and use the Breezy install partitioning to INCREASE the NTFS partition size?  Here is what I would like to do:

Total: 80 GB (70GB is useable)
XP OS NTFS: from 16 GB to 20 GB
Ubuntu ext3: from 12 GB to 20 GB
Swap: stay at 1 GB
FileStore FAT32: stay at 32 GB (or whatever is left)[/QUOTE]

I did something similar the other day but was to shrink the ntfs partition, I used qparted booting from a Konix CD, this way you wont have to wipe any drive.

Luck.

---

### Post by yesplease on 2005-11-22
I am not familiar with writing to NTFS, because I am afraid windows wont understand it (not sure though). However, you can read ext3 from windows with explore2fs (1.07) and read ntfs from ubuntu. This covers many ways of file echange, except for, for instance automatic synchronization.

There is a curious problem with fat32 [http://www.ubuntuforums.org/showthread.php?t=89992](http://www.ubuntuforums.org/showthread.php?t=89992) . I dont know if it applies to you, but a workaround is to format the fat32 partition after install of XP and ubuntu.

---

### Post by akniss on 2005-11-22
I decided to go ahead and use FAT32 as my data storage system.  I will just have to plan on backing up weekly to an ext3 or ntfs partition on my external harddrive.  Resizing the NTFS to a larger size worked like a charm.  No problems whatsoever.  In case anyone's wondering, this is what I did with my 80G drive:

hda1 - fat 47MB (no idea what this is, part of the default XP install)
hda2 - ntfs 23.29 GB (Windows XP Installation)
hda5 - ext3 22.28 GB (Ubuntu Installation)
hda6 - swap 1 GB
hda3 - fat32 27.94 GB (File Storage, accessible from both OSs) 

Thanks for everyone's suggestions.

---

### Post by brentroos on 2005-11-30
*

---

### Post by akniss on 2005-11-30
[QUOTE=brentroos]Why don't you just make an additional 16GB partition? How is this wasteful? Just allocate the space accordingly.[/QUOTE]

I'm only allowed 4 primary partitions....  Neither XP nor Ubuntu would let me create one more partition.

---

