---
title: "Screwed up partitioning - have a /DOS partition but it's a folder!"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by mark2741 on 2008-11-07
I have a 300gb internal hard drive. I went into the manual setting of the partition manager that is available using the Live CD, and I deleted all the partitions and then created 4 new partitions:

100gb NTFS - for Windows XP
60gb EXT3 - for Ubuntu OS
8gb SWAP (I have 4gb of RAM and I read to use double that as the swap)
111gb FAT32 "Shared"

The "Shared" partition I setup so that it could be a partition that I would store all my data/personal settings/music/etc that I wish to share with the Windows OS and Ubuntu.

After doing the formatting, I quit the Live CD installer and then rebooted with the Windows XP setup CD and did a clean XP install into the NTFS partition, then after that was done rebooted and did a clean install of 8.04 64-bit and then immediate upgrade to 8.10 64-bit. Everything is great except one problem:

When I created the "Shared" partition, I didn't fully understand the whole 'mount point' thing, and the only options that the partition manager allowed were to mount it as "/DOS" or "/WINDOWS". I chose the "/DOS" option. Now, it is a folder and not an actual mountable drive. That would be fine if I was just going to use it for Ubuntu, but I want to have it as a mountable drive that I can access in both Windows XP and Ubuntu (as well as my wife's wirelessly connected laptop running Ubuntu).

How do I get rid of the /DOS folder (which is a whopping 111gb!) and make it a mountable drive instead?

Background: 

Due to having all kinds of issues with Ubuntu 8.10 (and some with 8.04), and finding that after just 9 months of using Windows Vista as my primary O/S it was quickly suffering that "Windows Rot" where it just gets slower and slower, I decided to upgrade all my hardware and then do a clean formatting and partitioning of my drive and do a nice dual-boot setup with XP and Ubuntu 8.10. Everything is running superfast and great now, with my current setup being:

AMD Athlon x2 5600+
4GB DDR2 RAM
Nvidia 8600GT 512MB

Thanks,

mark

---

### Post by smurthy on 2008-11-08
Hi, I am a total newbie to Linux, and will be watching this thread to see if I can learn something. I have a similar problem that I don't seem to understand at all.

I have XP on a 80GB drive in three NTFS partitions (24,16,20 GB) and recently added a 200GB 2nd drive where I made 4 NTFS partitions (40,80, 20,60 GB) - then decided that I would install Fedora 9 on on the 60GB as an ext partion - that worked well and I was able to boot XP / Fedora separately by switching boot priority in BIOS without messing around with boot loaders etc.

Fedora was too difficult for me to understand - I didn't know how to mount my XP NTFS partitions etc, and after running the live CD, I decided to install Ubuntu 8.04 under Windows - in the 80GB partition in my 2nd hard drive. Everything works fine now - I can boot XP/Ubuntu from my 1st hard drive, and Fedora from my 2nd hard drive - except:

1) Ubuntu 8.04 seems to occupy 15GB on the 80GB partition- everything I had read said I would only need 5GB.

2) Ubuntu seems unable to access the 200 GB drive accept report it as a 40GB /media/disk that has 180 GB free space.

3) Its own 'partition' is shown as /host with free 65GB.

I don't understand what is happening here!! 

Fortunately Fedora can now see everything, and XP can see everything except the extended 60 GB that Fedora occupies. My Ubuntu seems to have lost out.

I plan to uninstall Ubuntu and try another install of 8.04 but using WUBI this time - perhaps this might help? Real nervous right now!!

murthy

---

### Post by louieb on 2008-11-08
hello mark2741,
That the way the Unix/Linux file system works. Everything is a file or a folder. The folder the partition is mounted on is called it **mount point**. 

Unlike windows where you access  a partition by a drive letter. You access a partition in Linux through its mount point.  

If you would like to see what partitions are mounted where. open applications>accessories>terminal and key ```
mount
```

Sounds like every thing is working as it should. 

hi smurthy: 
You would be best served by staring a new thread.  Sounds like your setup is quit different from mark's.    He has a traditional Ubuntu in its own partition setup. Sound like you install using wubi. it could get real confusing fast

---

