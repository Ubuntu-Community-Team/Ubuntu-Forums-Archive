---
title: "Best Dual Boot Partition Setup"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by falcon1 on 2008-11-03
Hey everyone - here is my situation: I would like to dual boot WinXP along with Ubuntu 8.10. I am wondering what the best practice for dual boot setup is. I have a few questions:

How many partitions should be setup? I know at least 2: one for XP and one for Ubuntu, but then there is the question of a separate partition for linux-swap(does it have to be separate?).

Also, I would like a separate partition for all my data (music, pics, etc.) - if I made another NTFS partition for data, would Ubuntu be able to read and write to/from it? Is this secure? For example, if I were to download some virus to the data partition that didn't affect linux, but then I boot into windows, would windows then be infected? Is it best to just keep everything downloaded in linux within the linux partition? 

Finally, what would be the minimum recommended sizes for these partitions? Right now I have a 20gb one for windows and programs, then the data one.

Whew - guess that is quite a lot of questions, and i am sure there will be more. Thanks a lot!!

---

### Post by Mr_JMM on 2008-11-03
May not be the ideal but this is how I set mine up to make things easy:

1 partition for Windoze, NTFS as small as possible. Knew I wasn't going to add anything else to it. Make this a primary.

2. Due to limitations with number of Primary partitions, and to allow further additions, set the remainder of the disk as an extended partition. Split this partition into 3 logical partiions for /root, /home and swap.

/swap should be about 2GB (some say twice RAM but 16GB+ can be excessive!!).

/root, like the NTFS can be as small as possible. I think 4GB is the minimum. The rest is /home (/home will be where all your docs, music, files etc will reside). /root and /home should be ext3 formatted (NOT another NTFS).

What is the total size of your drive? Will be able to be more accurate. I know you said you have 20GB for Windoze.

---

### Post by falcon1 on 2008-11-03
Thanks for the reply! Right now, I only have 60Gb to work with, but I was also trying to just get kind of a general guideline that could be flexible so others could use it - plus I should be getting a new computer with a larger HD soon! :p 

As for your setup, it seems pretty good, but where would you store files that are created/downloaded in windows? Would those go in the /home? Would windows be able to write to an ext3 formatted partition? Also, what was the word on security/a file downloaded in linux then infecting the windows partition? Nothing to worry about?

Thanks again,

-jon

---

### Post by blackened on 2008-11-03
Since you've only got 60GB, I would suggest keeping the 20GB for XP, then doing like Mr_JMM suggests with the remaining 40GB. I allocate 10GB (currently using 4.3GB of that) for / (root), approximately RAMx2 for the swap parition (within reason, 2GB is more than enough), then the remaining free space for /home.

Windows can't read or write ext3 out of the box. Use the driver from [here]("http://www.fs-driver.org/") for that.

As to the security issue: if you download something unsavory from the web using linux and then run it in windows, then yes, it will likely effect your windows installation just as if you had downloaded it in windows. This would mainly apply to executables and scripts, but not to drive-by downloaders and the like as linux is generally immune to things like that.

If you download something in linux and never run it under windows, then it will not effect your windows installation.

---

### Post by falcon1 on 2008-11-04
Alright, just to make sure this is right, my setup should be something like this (for a 60GB HD):

```

20GB / - Primary, NTFS - Windows install + windows specific applications

4GB /root - Extended, ext3 - this is for the base linux install??

2GB /swap - extended, linux-swap - linux swap

34GB /home - extended, ext3 - all downloaded and personal files for both linux 
and windows (maybe just setup a folder of files downloaded in linux and scan 
them in windows with AV before opening).

```

If a larger hard drive was used, would I just want to increase /home and /root (is /root for installing linux applications?).

Hopefully I have this all right! Cheers,

-jon

---

### Post by blackened on 2008-11-05
There isn't really going to be a partition called "/root" it will just be "/" but is referred to as the "root partition". The "root folder" is a subfolder of "/" where the root user files are stored. Hopefully this is clear enough. You can read about linux directory structure in various places on the web as well as this forum.

If you plan on installing alot of global themes, icon packages, applications, etc., then I would suggest making the root partition bigger, but it's really up to your discretion. 


Suggested layout:

10GB - "/"

2 GB - swap partition

28GB - "/home"

> **falcon1 said:**
> Alright, just to make sure this is right, my setup should be something like this (for a 60GB HD):

```

20GB / - Primary, NTFS - Windows install + windows specific applications

4GB /root - Extended, ext3 - this is for the base linux install??

2GB /swap - extended, linux-swap - linux swap

34GB /home - extended, ext3 - all downloaded and personal files for both linux 
and windows (maybe just setup a folder of files downloaded in linux and scan 
them in windows with AV before opening).

```

If a larger hard drive was used, would I just want to increase /home and /root (is /root for installing linux applications?).

Hopefully I have this all right! Cheers,

-jon

If you were to use a larger drive, then you could leave the "/" partition alone and just enlarge the "/home" partition. Unless you're doing some pretty irregular stuff, then your "/" partition need not be more than ~10-15GB at the very most.

---

### Post by fewjr on 2008-11-05
falcon1, 
     Check this out. [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning). You can make a data share partition also (fat32). The rest of Herman's site is very informative.

Good luck,
fewjr

---

### Post by falcon1 on 2008-11-05
Thanks again guys - very informative! If I were to go the route of setting up a fat32 data share partition, how big would the /home partition need to be? Or does setting up a data share partition change the whole layout (no more /home partition, and just make / larger??)? Thanks again!!

-jon

---

### Post by blackened on 2008-11-05
> **falcon1 said:**
> Thanks again guys - very informative! If I were to go the route of setting up a fat32 data share partition, how big would the /home partition need to be? Or does setting up a data share partition change the whole layout (no more /home partition, and just make / larger??)? Thanks again!!

-jon

Honestly, with the quality of the current built-in ntfs driver I don't see much point of a fat32 partition, but if you do plan on going that route, then you could eliminate or keep the home partition (of significantly reduced size, around 5GB or so). It's really up to you. The only issue I can think of, which is a definite benefit, is that if you reinstall and *do* have a home partition, then your preferences for installed programs, icons, and themes (unless you installed them globally) could be retained if you did a clean install, where if you have no home partition they could not.

---

### Post by YaroMan86 on 2008-11-05
Here's how I do it. And I think it is the best way:

I have Windows and Ubuntu. I primarily use Ubuntu.

My first partition will be NTFS as formatted by Windows XP when it is installed. Oftentimes it's my first hard disk instead since Windows and Windows Software (A) Takes an obscene amount of space. (B) Seem to act unpredictably when Windows is not installed on what is determined to be C: I usually have to remove any external drives or media before I install Windows to be sure that Windows will be on C: after the install.

Linux is on my second hard disk, the SATA. It is:

A 20 GiB reiserfs partition for the Linux system. I like reiserfs because it seems fast to me. That and I won't have to worry about regular fscks.

A 5 GiB swap partition. I know... EXTREMELY generous. But I easily have the room and 5 GiB is a nice number to me.

The rest of the hard disk is ext3. /home. This is also shared with Windows via the EXCELLENT ext2 IFS driver. This allows me to do a number of things: 1. All my documents, no matter what OS it originates will all be in one central location. 2. My settings will be put in there as well so I can keep it all even oer reinstalls. No backups needed.

---

