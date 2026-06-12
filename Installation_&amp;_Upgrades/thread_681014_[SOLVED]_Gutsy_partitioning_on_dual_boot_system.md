---
title: "[SOLVED] Gutsy partitioning on dual boot system"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2008-01-28
I'm attempting to upgrade from Feisty to  Gutsy, but I'm not sure what's happening here.  I get through the installation process to the point where the program wants to partition my hard disks.  How do I get the program to continue without changing any partitions?  The main problem is that I'm running a win modem and don't want anything regarding it changed as its a real b - - - ch to set up.

The screen the partitioner shows is as follows:


Device                 Type             Mount Point            Format          Size                    Used

/dev/hda

     /dev/hda1        fat32             /media/hda1                                 30721 MB            17300 MB

     Free Space									              8 MB

/dev/hdb

	/dev/hdb1	ext2		/media/hdb1                                38938 MB	        9600 MB
	
	/dev/hdb2	swap								  1077 MB		0 MB

As you can see, I'm dual booting with Ubuntu on hdb and Windows XP on hda.  The installation program says I need to designate a mount point with at least 2 GB of space.  Can someone tell me where to go from here?

---

### Post by CheShA on 2008-01-28
Can you explain how you are doing the upgrade?  By loading the live CD and choosing upgrade?

---

### Post by zvacet on 2008-01-28
If you want to upgrade from CD it must be alternate.From what I see in your post you are on the way to do fresh install,and that is not what you want,isn´t it?

---

### Post by Goldpin on 2008-01-30
Unfortunately, I did start to install from the live CD and now have a corrupt system!:(  If I try to upgrade from the alternate CD it will not do so as it falls over after trying to install the base system.  I've pretty well resigned myself to having to do a clean install from the live CD.  The only thing I'd really like to recover are the addressbook and emails from the evolution's inbox.  Is there any way to do this?  The rest of my /home folder was copied to the other hard drive so I've not lost all that much.  It will just be a major pain if I've lost the addressbook and emails.  Any suggestions please.

---

### Post by zvacet on 2008-01-30
Try run Live CD(not installing just run) and see if you can go to the home **directory>view>show hidden files>.evolution**

---

