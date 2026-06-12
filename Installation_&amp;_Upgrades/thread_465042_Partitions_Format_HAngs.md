---
title: "Partitions Format HAngs"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Norst on 2007-06-05
Install Ubuntu on a extra 500gb drive in my machine. 1st 3 drives are NTFS, last drive is the one I want Ubuntu on (Drives not partitions). Followed the install and selected "Guided Full drive" and point it to the 500GB blank drive. After the questions regarding name and password, it begins the partition format process. It shows 5% formating ext3 on the drive but just hangs there. I even had a nap and woke to the same display on the screen. I'm able to format the drive in windows and all that. And I removed all partitions form the drive before booting ubuntu, so I know its totally fresh for the install. Any ideas as to what or why this is happening?

Thank you for any help.

---

### Post by wpshooter on 2007-06-05
Sounds like you are using the ALTERNATE CD version to attempt the install.  Why are you not trying with the DESKTOP (live CD) version ?

Also, have you checked the integrity of the CD by running the verification function that is found on the initial boot screen menu ?

---

### Post by dabl on 2007-06-05
I personally like the GParted Live CD to check out, partition, and format a new hard drive.  You can download the ISO image from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

HTH  :)

---

### Post by Norst on 2007-06-05
I made a few diff cd's when 1st try'n it out. I could very well be using the alt CD. I'll find the desktop CD when I get home and make sure I use that. Not sure how you knew that could be the ALT CD but I'll go with that.

---

### Post by zdiddy on 2007-06-06
This is the exact same problem I have.  I currently have Windows XP installed and use three hard drives.  Two are ATA and the third was an SATA.  I installed another SATA 160gb hard drive and attempted to install both ubuntu and kubuntu 7.04 but both installs failed during the hd format at 5 %.  I have an Asus 939 SLI primium mother board with an Athlon X2 3800+.  I used the amd64 live cd, not the alternate one.  Any suggestions would help.

---

### Post by izyk on 2007-06-06
I have exactly the same problem. I have a shuttle SD32G, and it has two identical 320GB SATA hard drives. I boot from the standard livecd, run install and then choose guided on the second drive.

The format dialog hangs at 5% EVERY time.

I would love to get past this, but I really have no idea where to start.

---

### Post by perimere on 2007-06-16
I have experienced the same issue. Same hardware Shuttle XPC SD32G. The GUI install for Feisty has real issues here.

I either get a hang as it enters the UI on startup (so I get the brown background and nothing else). Or I can get as far as the end of the Install Wizard and as soon as it tries to format the root partition it hangs on 5% complete.

Interestingly the GParted Live CD 0.3 was able to partition and format without a problem, however the Feisty install insists on reformating the root partition as part of the install, and this is where it hangs.

Annoyingly, Debian 4.0 installs without any problems, so this is appears to be an issue with Ubuntu. This would have been my 4th ubuntu box at home but it's now going to be a Deb box unless someone has a work around?

All of this was with the 64-bit version of both OS's (Ubuntu and Debian). I haven't tried thr 32-bit version of Ubuntu, but suspect the same problem.

Cheers

Adam

---

### Post by zdiddy on 2007-06-18
Sorry to see no one has posted a potential solution.  It is interesting to see how the different versions react so I attempted to install openSUSE and I got the same install hang on the drive format.  Again, I used an unformatted SATA drive connected on the second sata port on my motherboard with three other hard drives that are used with a windows xp install (2 ATA, 1 SATA).  Motherboard is a ASUS a8n (or something like that) premium.  Maybe ubuntu and openSUSE do not like hard drives on the SATA port or they do not like SATA port B.  I guess I can disconnect all my hard drives and try an install on the SATA A input and see if it works.

---

### Post by D2X2903 on 2007-12-14
I just wanted to add that I've been having the same problem when trying to install the 7.04 amd64 version using the live DVD.  Interestingly enough, I have the A8N-SLI Premium too.

I tried using the partition editor to create two FAT32 partitions and a swap partition.  It completed and has been stuck at at "Please wait... 100%" for several hours.

---

