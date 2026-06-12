---
title: "How to dual boot OS X and Ubuntu?"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by dailyplanet on 2006-02-22
Hi everyone.
Let me say first off that I'm completely new to Ubuntu and Linux. I downloaded a LiveCD and really liked Linux so I decided to go ahead and try to install it on my iBook G4. However, I'm currently having issues getting Ubuntu to install on my Mac. I did a search here on the forums to see if any threads might be able to help me out but came up with none. I've wasted a good 3 hours trying to get this to work. I hope someone will be able to help me.

Here's what I did
1. Partitioned my HD: 60Gb (Mac OSX Extended journaled) & 20 Gb (free space)
2. Booted up Ubuntu 5.10 install cd
3. Partitioning part of the installation: I selected install in free space or something like that
4. Everything was going fine until it came to installing yaboot. That part of the installation failed. I had to abort the installation.

Help?

---

### Post by profclimber on 2006-02-23
i have the same problem he says cannot find other sytem?

---

### Post by Weneedsound on 2006-02-23
This is the same type of project that I am getting ready to attempt. 

Currently, going through the motions of backing up everything and moving files over to my other PC.

I have a:

PowerPC G4 1.67GHz PowerBook w/512MB of RAM.
80GB HD

I am new to linux and I am looking forward to seeing some replies to this post!

\\:D/

---

### Post by linear on 2006-02-23
Suggestions here:
 
[http://ubuntuforums.org/showpost.php?p=755739&postcount=4]("http://ubuntuforums.org/showpost.php?p=755739&postcount=4")
 
When partitioning the disk, I believe it's important to have the block of free space as the first partition, and put the OS X partition second.

---

### Post by dailyplanet on 2006-02-23
Alright guys, I went on a whim last night and did it! I am now posting from my iBook G4 that's running 5.10 Breezy Badger! Here's the how to, hope it helps:

How to Dual Boot OS X and Ubuntu
You will need:
1 OS X install disk (Tiger, Panther, whatever)
1 Ubuntu 5.10 install disk PPC version

*Make sure to back up your HD before you start this, Disk Utility deletes everything!*

1. Boot from Cd-Rom drive by restarting and pressing 'C' while the Mac restarts.
2. Once you enter into the installation program, click on Utilities from the menubar and select Disk Utility.
3. Partition your disk into 2 parts. The first one (i.e. the top partition) you will leave as Free Space for Ubuntu. The second one (i.e. the bottom partition) you will partition as Mac OS X Journaled (Extended). My partition sizes were 20 Gb for Ubuntu and 60 Gb for Mac OS X.
4. After partitioning your HD, (re)install Mac OS X. Go through the whole installation set up and reboot. 
5. After you have OS X up and running, insert Ubuntu install CD and reboot from the Cd-Rom drive by restarting and pressing 'C'.
***Make sure you don't have any external hard drives connected to your Mac at this point! It's the external HD that makes Ubuntu unable to install yaboot!***
6. Once you are to the Partitioning screen, choose "Use largest free space". This tells Ubuntu to install on the first partition we made earlier. 
7. Ubuntu should then go ahead and create the partitions it needs and install the base OS and yaboot.
8. Sit back, reboot Mac, and yaboot will ask if you want to boot Ubuntu (press 'L') or OS X (press 'X') or from Cd-Rom drive (press 'C'). Press 'L' and enjoy!

DP :D

---

### Post by ssam on 2006-02-23
the order of the partitions is not that important (as far as i can tell). my mac os partiton is before my ubuntu ones.

it is a good idea to use the mac os disk utility to do the partitioning. macs need a few hidden partitons at the start of the drive.

also if you want a dual boot install mac os x first, then linux

---

### Post by nargilamonster on 2006-04-05
i agree...my install kept getting hung on yaboot install...so I reinstalled Tiger and put it on my 2nd partition, yaboot and unbuntu must be on the first partition...it's nicer that way since the Mac Boot manager (if pressing "Alt" can be called that really) sucks.

---

### Post by jrgillam on 2006-04-27
If use Disk Utility to partition my drive, then reinstall Os X, can I then transfer a bootable clone of my current mac setup to the new mac partition, and have it be the same as it is now? Thanks in advance.

---

### Post by nargilamonster on 2006-04-27
[QUOTE=jrgillam]If use Disk Utility to partition my drive, then reinstall Os X, can I then transfer a bootable clone of my current mac setup to the new mac partition, and have it be the same as it is now? Thanks in advance.[/QUOTE]
I am not sure what making a bootable clone of your System has to do with installing Linux. Doesn't OS X come with tools for "migrating" between 2 computers?
Anyway, I would advise a file transfer, I have Ubuntu working now but it installed only after I reformatted, reinstalled OS X (to the 2nd partition), & etc.

On a related note:
Has anyone had any success in getting OS X to recognize the partition of the HD with Linux on it? Namely, can Linux (Ubuntu) run smoothly with HFS ?

---

### Post by jrgillam on 2006-04-28
The bootable clone would enable me to partition my hard drive, creating a partition for Ubuntu, and make it possible to keep my Mac OS the same is it was.

---

