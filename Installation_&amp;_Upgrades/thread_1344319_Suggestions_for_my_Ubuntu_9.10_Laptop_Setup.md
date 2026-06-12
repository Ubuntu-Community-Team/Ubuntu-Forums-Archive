---
title: "Suggestions for my Ubuntu 9.10 Laptop Setup"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by maxtheitpro on 2009-12-02
I'm now using Ubuntu 9.10 on my Toshiba L305-S5944 laptop which is a Dual Core 2.16Ghz, 2Gb RAM and 250 MB Hard Drive.
Originally I had tried to install Windoze and allocated 30 Gb for XP but the install crapped out on me (XP can't see SATA) so I was saved by the Ubuntu Live CD.

Basically, I'm HAPPY as hell with my current setup (9.10 running perfectly, VirtualBox with an XP guest). However, I have about 16 GB of data on a 200 GB NTFS partition. According to the Disk Utility in System-->Administration, I have the following disk layout, which I want to CHANGE: 
* 250 GB Hard DIsk
       >> 20 GB Linux Filesystem (Linux Ext3)
       >>  DATA (198 GB, NTFS)
       >> 32 GB Extended (contains logical partitions)
                   >>> 2.0 GB Swap Space
                   >>> 30 GB Filesystem (FAT32)

QUESTIONS:
1) Assuming I back up my DATA partition to an external USB 2.0 drive, HOW can I backup and/or reinstall Ubuntu 9.10 "without" losing all the programs I just installed (VirtualBox with XP as Guest, etc.)???? What should I backup so that I can just recopy (if I have to reinstall Ubuntu)?

2) Assuming that I were able to reformat the entire hard drive in order to prepare it for Ubuntu 9.10 (I'd like to use Ext4), please suggest a disk setup that will utilize the entire 250 GB hard drive.
ie. How many partitions should I create? How big should my swap partition be? How big should my /home / and other partitions be?? What's the best disk layout to maximize performance (separate /home partition, etc.?)

a) I would like to run Fruity Loops Studio or Virtual DJ some day in the future on XP. I don't know how well this runs in VirtualBox though. Maybe I should keep 5GB or so for a future XP install to dual boot into these 2 apps? Does Linux have anything similar BTW? Oh, I WON'T ever be installing Windows 7. I just might want a teenie little space for XP though.

b) Note: I'd like most of my hard disk space for DATA (MP3s, documents, videos, etc.) purposes

I'm thinking of this setup:
* 200 DATA partition
* 50 GB for Linux, Swap, etc.

Is this correct? I'm sort of stuck in the Windows mentality of separating my DATA drive from the C: drive just in case I have to reformat. Do I need to do this with Linux? Should I just make /home 200 GB??

Last Word:
To conclude, once I move my data over to the external USB drive, what else do I need to copy over from the Ubuntu side so that I don't have too much reinstalling work to do? Do I need to download Karmic Koala? I upgraded from Jackalope. This is my dilemma. Is there a step-by-step way to image my Ubuntu install so that I can restore it on an ext4 partition? Tell me what backup program to install. I already have Simple Backup, Simple Restore, Deja Dup Backup Utility, and Back In Time from the Software Centre.

Looking forward to your replies.

---

### Post by maxtheitpro on 2009-12-03
Oh well, I'll just do a fresh reinstall after I play around with some other distros!! :-) Curious to try out the latest releases of Mint, Mandriva and PCLinuxOS

---

