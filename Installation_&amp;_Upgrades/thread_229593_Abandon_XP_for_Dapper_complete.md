---
title: "Abandon XP for Dapper complete ?"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by azmrb on 2006-08-04
I like Dapper64, A LOT.  So much so that I am considering switching to Dapper exclusively as I have gotten nearly everything I need to work in only a few days.  Now here is my current configuration and question.

250gb drive partitioned approximately 150gb for Xp and 100gb for Dapper.  Using grub boot loader.  

If I delete the NTFS partition is there any way of resizing my current ext3 filesystem to use the rest of the drive ( except of course the swap partition ) and be reasonably sure it will boot properly or should I just wipe the drive and start over.  The only reason I ask is that I have compiz running great and I would hate to not be able to get it working again.

Thanks in advance for your suggestions and input.

---

### Post by zxee on 2006-08-04
Some people swear by gparted others at it. It could do what you want but backing up is of course a very good idea. [http://www.linux.com/article.pl?sid=06/04/25/1917228](http://www.linux.com/article.pl?sid=06/04/25/1917228)
[http://www.55rueplumet.com/2006/02/22/gparted/](http://www.55rueplumet.com/2006/02/22/gparted/)
[http://www.linuxquestions.org/questions/showthread.php?p=2256257](http://www.linuxquestions.org/questions/showthread.php?p=2256257)
This last link (above) from linuxquestions has some useful options.
Personally I've never found the gui tools to be as precise or even as understandable as learning the terminal-which I am far far from an expert on.
Hope that helps.

---

### Post by Cynical on 2006-08-04
azmrb, if you are interested in an easy to setup compiz + xgl check out [automatix bleeder]("http://ubuntuforums.org/showthread.php?t=225967")

And as mentioned above, the tool gparted can both delete the ntfs partition and resize your ext3 partition without issue.

---

### Post by Herman on 2006-08-04
>  250gb drive partitioned approximately 150gb for Xp and 100gb for Dapper.  Using grub boot loader.  If I delete the NTFS partition is there any way of resizing my current ext3 filesystem to use the rest of the drive ( except of course the swap partition ) and be reasonably sure it will boot properly or should I just wipe the drive and start over. I am a big fan of Gparted LiveCD and I'm one of the people who swear by it.

I want to explain a little more about what will happen with your partition numbering and how it will affect booting. 
As mentioned in the first link provided by zxee, your partition numbers will be changed. This is not something exclusive to GParted, (as far as I know any partitioning software will do the same thing). 
Say for example, Windows is numbered /dev/hda1, (partition 1), and Ubuntu is /dev/hda2, (partition 2). If you delete partition 1 and copy and paste partition 2 somewhere, the new partition you create will be given the name /dev/hda1. This happens because the number will be made vacant by deleting your old partition 1 (Windows), so /dev/hda1 (partition 1) will now be the lowest vacant partition number. The next partition to be created will be automatically given the lowest available partition number. (If you didn't delete partition 1 first, and you copied and pasted partition number 2 somewhere, it would be named /dev/hda3, (partition 3).)

If your Ubuntu operating system was called /dev/hda2, and is now called /dev/hda1, you will need to make a couple of minor adjustments to make it boot and function correctly again. It will still be configured as /dev/hda2 , and your MBR will still be pointing to /dev/hda2 for booting with Grub.

To make your new copy of Ubuntu boot on /dev/hda1, you just need to [re-install Grub bootloader to MBR for /dev/hda1]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") and it will boot up alright. If you use the example in the link given, replace 'root (hd0,1) with 'root (hd0,0)' if you want to install Grub to make the MBR point to partition 1 rather than partition 2.  After that you will need to edit your /etc/fstab file and let your operating system know it isn't on /dev/hda2 anymore, it's on /dev/hda1 now instead. After those two quick, easy operations your Ubuntu operating system will be booting and working  perfectly  on  /dev/hda1, (partition 1).

If you want to make GParted preserve the Ubuntu partition's original partition number, you can do that in the following way. 
1) Delete your  Windows partition.
2) Shrink Dapper as small as you can.
3) Copy and paste your Ubuntu partition to the end of your hard disk (temporarily). It will be given the number /dev/hda1 (partition number1), because that will be the first available partition number now.
4) Delete /dev/hda2 (you present Ubuntu partition).
Copy and past /dev/hda1 from the end of your disk to the start of your disk. It wll be given the partition number /dev/hda2 like it had before. Then it will boot up and function right away without doing anything more. You can resize it to fill up all the available free space as you like.

I hope this doesn't sound too confusing, it's really very simple once you try it. Any questions, just ask. :D

I have read theat a new version of GParted is expected sometime soon, (but I don't know when), that will be able to 'move' Linux partitions (you won't need to copy and paste, or worry about changing partition numbers).

---

### Post by azmrb on 2006-08-14
I ended up shrinking the ntfs partition with paragon and then creating a new ext3 partition which named home and moved the home directory to this new partition according to instructions I found on the net.

Works great, I like the idea of the seperate home partition because now I can install a new linux OS on the filesystem partition in the future but still have the same home as before so I keep all my files, preferences, and settings in apps like firefox.

---

