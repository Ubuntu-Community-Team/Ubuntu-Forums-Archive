---
title: "Dual boot from Scratch XP &amp; Ubuntu?"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by crocco on 2005-08-15
I want to do a complete reinstallation of XP and Ubuntu.  Everything I have read to date addresses setting up a dual boot on an existing XP maching, resizing the disk durning installation of Unbuntu.  

I am wondering, if I am starting from scratch, and don't care about saving my current XP install, is there a better way to do this?  

Can I reformat and partition my HD first, put XP on one partion and Unbuntu on the other without the resize step?  

I would like to have a clean/fresh install of both on my PC.  

Any help would be great!  Thanks

---

### Post by PeP on 2005-08-15
yes you can format first, install then without resizing anything.

Just a tip: install XP first .

If you plan to do this with a big HD plan to make many partitions:
1. NTFS for XP
2. FAT to have a fs usable by both
3. one for / (root partition)
4. one for /home (users settings and documents when it is separate it is easier to reinstall  or to switch to another distrib
5. one for swap (virtual ram very small partition)

---

### Post by crocco on 2005-08-16
Many thanks...and 3 more questions:

1. Can I perform all of the partitioning with the XP CD?  
2. Can you make Partition size recommendations for a 80 Gig hard drive 
   (or percentages/minimum sizes for small/sharing partitions)?
    (am looking to use XP for gaming only)
3. Am I understanding you correctly? Are you suggesting 5 seperate partions with a FAT partition to allow them to share files between?  (seems like a very cool concept). 

Very helpful! Thanks!!

---

### Post by varunus on 2005-08-16
Ubuntu's installer can resize partitions, so if XP's is being mean, just let it have the whole drive.

ubuntu can create FAT32 partitions inside its installer during the partitioner, just choose "manual partitioning."
Here's a guide with pictures:
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by DancingSun on 2005-08-16
[QUOTE=crocco]Many thanks...and 3 more questions:

1. Can I perform all of the partitioning with the XP CD?  
2. Can you make Partition size recommendations for a 80 Gig hard drive 
   (or percentages/minimum sizes for small/sharing partitions)?
    (am looking to use XP for gaming only)
3. Am I understanding you correctly? Are you suggesting 5 seperate partions with a FAT partition to allow them to share files between?  (seems like a very cool concept). 

Very helpful! Thanks!![/QUOTE]
[list=1]
[*]Nope.  The XP CD can only create NTFS and FAT32 partitions.  You'll need to specify a size for the XP partition and leave some empty space for Ubuntu.

[*]The sharing partition's size should depend on your usage.  If you need to edit very large files (eg., video files) from both OSes, then you should make that partition fairly large.

The "/" partition is where the core Ubuntu files will be installed.  "/home" partition will contain your user files, like Windows' "User Documents and Settings" folder.  Currently I have "/" as 5 GB, and the rest of the Linux partition as "/home" (I install all my Linux games under "/home/username/games"), on a 80GB Linux partition.  The advantage of having a separate partition for "/home" is that you can reinstall, or change distribution, without having the files in your "/home" partition getting destroyed.  I do not have a "swap" partition, because I have 1 GB of RAM, otherwise, make your "swap" parition around 1.5X-2X the amount of your RAM.

[*]Personally, I do not use a FAT32 partition for sharing.  Ubuntu by default can READ from NTFS partitions, and WinXP can READ from Linux partitions with some 3rd party software (there are free ones).  But if you're just using XP for gaming purpose, like me, then you probably won't have much of a need to use a FAT32 partition.  What the FAT32 enable, is WRITE operation from both OSes.  This means, if you have a Open Office document in the FAT32 partition, for example, you'll be able to edit and save the changes from both OSes.  Also, FAT32 partitions are more prone to lost clusters, which translates to data loss.  Remember those old Win95 - Win98 days?
[/list]

---

### Post by crocco on 2005-08-16
So, I could:

1. Write a word file to the NTFS in XP
2. Read the same word file from open office, then do a "Save as" to my linux partition under a new file name (Or vice versa)?  

Awesome advice!!! Now I am excited!!

---

### Post by DancingSun on 2005-08-16
[QUOTE=crocco]So, I could:

1. Write a word file to the NTFS in XP
2. Read the same word file from open office, then do a "Save as" to my linux partition under a new file name (Or vice versa)?  

Awesome advice!!! Now I am excited!![/QUOTE]
Precisely!  Hmm...I thought I gave an example, I guess that was in another thread :)

This is actually what I did as well.  I have some word documents, like my resume, saved in my NTFS partition, and when I installed Ubuntu, I wanted to edit those files in Ubuntu, so I mounted the NTFS partition (instructions can be found on [www.ubuntuguide.org](www.ubuntuguide.org)) in Ubuntu, copied the "My Documents" folder to my "/home" directory, added write permission (they were marked read-only since everything in the NTFS partition is marked as read-only).  Opened the docs with Open Office, and start typing away.

---

### Post by Hairy_Palms on 2005-08-16
yep you can do just that, and you can also do it the other way round with third party software, i installed the same way you want to, and i have 4 partitions which are
Ubuntu
Suse
swap
WinXP
i personally dont like the seperate home partition, as its what i used to have in mandrake and it used to unmount itself which kinda annoyed me, but i give each OS a single partition to dominate now. 

i personally use explore2fs to get files from linux in windows
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

