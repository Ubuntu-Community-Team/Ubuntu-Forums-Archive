---
title: "Partitioning and Dual Boot Mess, Please Help Me!"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by ux5b2 on 2005-09-13
Hello, Ive gone through many forums and howto's and have had no success.  My situation is this: I currently have Ubuntu installed as the only operating system and have only 1 partition on my hard drive.  I need to install windows (I need certain applications for school - wine or something similar is not an option) on a separe partition to  have have a dual boot.  The problem is that I do not want to get rid of my current Ubuntu install.

From what I understand If I install windows, it will erase the MBR and I will have to reload GRUB using the live CD or some method.  This is not the problem.  The problem is that I need to create a new partition (probably at the start of the disk) for windows before I install it.  When I just pop in the windows cd and get the partitioning part, it doesnt give me an option to have it installed on a separate partition (only to format the entire disk).  To try and get around this, I ran qtparted from a linux rescue disk and from the live CD to try and create another partition (by resizing my current one and moving it), however, the program will not let me touch the partition where Ubuntu resides.  Please help me figure out how to create a second partition (giving it space from my current Linux partition) and get Windows installed on it.  Thanks for your time.

---

### Post by bysse on 2005-09-13
Maybe you should try [vmware](http://en.wikipedia.org/wiki/VMware)  It's virtual machine were you can install any OS (that's supported by your hardware) and it doesn't need any partitioning.

---

### Post by ux5b2 on 2005-09-13
Thanks for the suggestion but I really just want a standard dual boot with Ubuntu on one partition and Windows on the other.  Anyone have any suggestions?

---

### Post by impeteperry on 2005-09-13
[QUOTE=ux5b2]Thanks for the suggestion but I really just want a standard dual boot with Ubuntu on one partition and Windows on the other.  Anyone have any suggestions?[/QUOTE]
 Try System Commander. It costs but should work for you.

---

### Post by sir_mud on 2005-09-13
Only reliable method I would reccomend is back up your Ubuntu data, re partition your drive and then installing windows, then reinstalling Ubuntu.

*Edit*
If you're unwilling to do that, you might try Partiton Resizer found on [zeleps.com]("http://zeleps.com") It runs off a floppy and should be able to resize and move your partition around. I used it to shrink my old Windows partition without problems, but I still recommend installing windows first.

---

### Post by az on 2005-09-13
Boot the ubuntu installer and shrink your ubuntu partition down.  You did not mention the size of your hard drive, but let's assume that it is 20 Gigs.

Make your Ubuntu partition something like 7 gigs.  Then, create another partition after the former Ubuntu partition (the free space you created.)  Then, copy all the data from the first partition to the second.  

Make the original partition a fat32 partition and install windows on it.

When you chroot into the partition to run grub-install, you will need to change your fstab and /boot/grub/menu.list to make sure that your / mount point is properly changed to the new partition.

Just boot the installer and make your way to the partitioner.  then go to the second console shell (CTRL-ALT-F2) and run parted and do all this by hand.  It is easier.

---

### Post by ux5b2 on 2005-09-13
Thanks for the reply.  If I resize my Ubuntu (and only) partition will Ubuntu still boot properly afterwards?  Also could you be more specific about how and where to chroot and do what you suggested?  Thank again.

---

### Post by ux5b2 on 2005-09-13
I managed to resize the partition successfully.  Could someone please walk me through copying everything over to the new partition?  Thanks.

---

### Post by ux5b2 on 2005-09-14
I really need to get windows installed as soon as possible so if anyone can help me out it would be greatly appreciated.  Like I said, I successfully divided my linux partion into 2 (1 for Ubuntu as ext3 and 1 for windows as free space).  How do I proceed from here (moving all my data to the free space partition..)?  Thanks.

---

