---
title: "How should I go about installing Ubuntu and XP?"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by sroark on 2008-02-04
Hi, I know this is a noob question, and truth is is that I kind of know what I am doing (I think). I have been using XP until about 3 weeks ago I started using Ubuntu and I really like it and I find myself hardly ever using XP anymore, so what I want to do is to take my 140 gb partition with XP and my 20 gb partition with Ubuntu, and basically swap them around. I know I will have to reinstall both systems, which is where I'm stuck on what to do. Should I just delete the existing partitions, create a 20 gb one for XP and then use whatever is left for Ubuntu? And how do I do this? Just put the XP disc in and boot from it? Thank you very much for any help/tips.

---

### Post by Battie on 2008-02-04
Actually, off the top of my head, you should be able to use a freeware XP tool (others can recommend)l to shrink the XP partition too the desired size.  When that is done, boot your Ubuntu install disc and use gparted to expand the Ubuntu partition.  If all goes well, you shouldn't have to reinstall.  I'd suggest GParted to do *everything*, but XP is very finicky about these things.

(Back up, of course.  Doing this is fairly safe, but things can always go wrong...)

Sorry this is brief, but I'm at work.  Just wanted to give you an idea before you erase everything.

---

### Post by zvacet on 2008-02-04
First of all back up your data from win and Ubuntu partition(in case you have something you want to keep).If you want to shrink win partition defragment it few times before you do that.That way you will make sure that you will not erase some files.If you want to do it that way download [Gparted Live Cd](http://gparted.sourceforge.net/) and burn it on disc.With it you can delete,resize...your partitions.Now you can rersize your win partition and what is left change to unallocated space and merge to Ubuntu partition.Other option is to delete everything you have on HDD and start all over.In that case install windows first and give to them as much spaceyou think is enough.Rest of space give to Ubuntu,and it will be good idea t omake separate home partition.

---

### Post by Pumalite on 2008-02-04
That's basically a good idea, but dangerous. I'd get Gpated Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. (after backing up all you want to save)
Delete everything in your drive. Make two new partitions. The first, 20 GB, formatted ntfs. The rest for Ubuntu, formatted ext3 if you want. Then install XP in the first partition and following, install Ubuntu in the second partition. Let Grub install to MBR. You'll have dual boot.

---

### Post by sroark on 2008-02-04
Thanks for the quick response guys. If I don't have to reinstall XP that would be nice because of drivers on this PC, they are aggravating. Truth is, I dont mind to reinstall Ubuntu because it has been a learning experience since I installed it and I have installed so many packages and done so much to it that I know I don't want or need, but don't want to remove out of risk of screwing something up. I guess I just want to start over now that I semi-know what I am doing if that makes any sense. So I guess I can just shrink my Windows parition (I backed everything valuable up just a little bit ago) and then form a new partition with the extra space I get and Ubuntu's current space to form one partition to reinstall it on? Thanks to all the help :)

---

### Post by Pumalite on 2008-02-04
That option is also valid. Don't forget to back up.

---

