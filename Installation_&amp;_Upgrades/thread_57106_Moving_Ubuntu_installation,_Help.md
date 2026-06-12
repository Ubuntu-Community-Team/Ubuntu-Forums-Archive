---
title: "Moving Ubuntu installation, Help"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by carguy0625 on 2005-08-15
This is my situation.  Right now I have an 80 Gig HD with XP on it and a 10 Gig HD with Ubuntu on it.  Is there anyway I can repartition the 80 Gig HD and move my current Ubuntu installation on to it without having to start from scratch and reset everything up??  Thanks for any help.

---

### Post by anarki on 2005-08-15
First of all, you must use some good tool for partitioning hard drives. Like Partition Manager. That's the most dangerous part :wink: I recomend you to make 'free space' for Linux partition from PM, and then use some live CD (Ubuntu,... ) to run cfdisk and mke2fs, or what. It'll be good to make new partition with the same file system as is on the old Linux partition (or double check what file system modules are compiled in the kernel, and what modules is loaded from initrd). 

Ok, now copy all the contest from old to new partition.

First of all, you must edit your /etc/fstab. It's easy. Read 'man fstab' for more info. You should change only one line: the one contains description of your / partition. You have to change device of your / partition to new one. Notice: If you do not make that new partition as the last on your hard drive, than you have to edit some more lines.

Then you have to reconfigure your boot loader. If you use lilo it gonna be easy and safe. It's harder for GRUB.
Ok, for lilo: edit /etc/lilo.conf. You should find the desription that is used to boot up your Linux, and change the root partition. Read 'man lilo' and 'man lilo.conf' for more details. After you edit files just run 'lilo'.
For GRUB: There's a problem 'couse GRUB uses a configuration file on your Linux partition (/boot/grub/something :) ), and it seek for it everytime computer is started. (Lilo is installed in MBR and needs no file to boot) So, you should edit that file onto yours new Linux partition, and install GRUB into MBR using that new file. It can be done from Live CD. But, if you don't do it properly, you will NOT be able to boot any system. Ok, it can be fixed later, but...

All you done is at your own risk. I reinstall Knoppix on that way long time ago, and it works. 
Good luck!

---

### Post by carguy0625 on 2005-08-15
I might just wait until Breezy comes out and do a fresh install with it on the 80 Gig HD and put OSX on the 10 Gig HD.  I don't think I want to mess with the GRUB changes.

---

