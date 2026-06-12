---
title: "Setting up partitions before dual booting: help"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by enth on 2007-11-25
Greetings, I just joined =]

I recently built a gaming computer with vista ultimate. I'm taking linux classes in college and.. well wow I love linux.

My situation: I have a 300gig hard drive, with vista installed. I want to have 3-4 partitions. 

One for vista, one for ubuntu, one for data that both OSs can use, and maybe one for games (only reason why I got vista to be honest, dx10)

My problem: I don't know where to start. I don't have any data on my hard drive that I care about so I figure I'll reformat and start partitioning (vistas shrink doesn't shrink enough for my liking)

Vista: 20GB
Ubuntu: 
/ 5GB  
/boot 200MB
SWAP 4GB (double my ram)
/home 3GB?
/tmp 512MB
Free space: 260ishGB (in FAT32?)

Does that seem logical? Does vista need games to be in the same partition? Or can the games be in the FAT32 partition?

Also, I don't know to start with vista install, then ubuntu or vice versa.
I'm new to partitioning :-k

---

### Post by torgrot on 2007-11-25
I would probably divvy it up this way.  Shrink the Vista Partition using the Vista disk manager to about 100GB.  Then use the GParted on the live cd to create a 20GB partition mounted as /  then an extended partition consisting of 80GB mounted as /home 2GB as swap and the rest as whatever you want Fat32 or NTFS to share between the two operating systems.  I would install Vista first.  then install Ubuntu but put grub on hd0,1 not on the mbr of your disk.  I would download EasyBCD to create the option in the Vista loader to boot Ubuntu.  FWIW

torgrot

---

### Post by enth on 2007-11-25
Hi thanks for your reply, the problem is vistas shrink only shrinks it from 300 to 260 :confused:

---

### Post by torgrot on 2007-11-25
Turn off virtual memory, defrag the disk, shrink it and turn Virtual memory back on.

torgrot

---

### Post by LaRoza on 2007-11-25
That won't work very well.

I would make:

sda1 NTFS 15 GB
sda2 EXT2 15 GB
sda3 NTFS/FAT32 (rest of drive)
sda4 SWAP 512 MB

Install Vista first, use GParted live cd (see the link in my sig) to shrink Vista and create the above partitions. GParted Live CD is very easy to use.

You can make the large partition NTFS and install games to it, make a directory for it if you do that.

You can only have 4 primary partitions, and I see no reason to complicate things.

---

### Post by enth on 2007-11-25
Hi LaRoza, your way seems good. I'm just wondering that if the rest of my free space is an NTFS partition for games, would ubuntu be able to read and write data from that NTFS partition?

---

