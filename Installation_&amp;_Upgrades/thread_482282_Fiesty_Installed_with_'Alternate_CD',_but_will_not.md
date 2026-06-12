---
title: "Fiesty Installed with 'Alternate CD', but will not boot from harddisk"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Sadi on 2007-06-23
I have installed Fiesty with the Alternate CD after my installation with LIVE CD kept giving me the /bin/sh:can't access tty; job control turned off.

But after successful installation with the alternate CD, I'm still getting the same error!!

Any help in this matter will be greatly appreciated

Thanks

---

### Post by merlinus on 2007-06-23
Almost certainly video-card related.  What are you using?

-merlin

---

### Post by Sadi on 2007-06-23
I'm using NVIDIA GForce 3.....

How can I solve this issue?

---

### Post by merlinus on 2007-06-23
Try searching for NVidia.  There are many threads helping to solve your problem.

-merlin

---

### Post by Pumalite on 2007-06-23
Check this too:

[http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html](http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html)

---

### Post by Sadi on 2007-06-26
I think I should have mentioned this before. First, I don't have a network card in my system & during installation i got a message that no network card was found; i continued the installation by clicking the button. 

Secondly, I formatted my 40GB HD in another system (which has XP on it). The HD had nothing on it before I started installing Ubuntu. But the file system I chose when formatting was NTFS. Does having NTFS instead of FAT32 might cause this problem. 

Thirdly, I've been also considering that NVidia may be causing this error. I have read lots of forums and articles, they provide a number of solution BUT for all of them I have to use the *sudo* command. The only problem is that I when I use this command I get a message that the sudo command is not recognisied!:confused: 

Any help/insight by any member will be appreciated.

Thanks

---

### Post by Pumalite on 2007-06-26
Check this page. There are a number of problems addressed here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by dabl on 2007-06-26
> **Sadi said:**
> the file system I chose when formatting was NTFS

That may be the entire problem, or most of it.  You'll get a far better result by doing the following (you can use your XP machine to do the first part of this if you want):

1. Download and burn a GParted live CD from the ISO image here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

2. Boot that CD and use it to partition your 40 GB drive as follows:

/ = 8GB (set the "bootable" flag for this one)
/{swap} = 1 GB
/home = all the rest of it

NOTE: GParted will not actually assign the names to the partitions, but I want you to see where you're headed with it.

3. After you have "written" the partitions with GParted, put the drive in the real machine where you plan to run it, boot your Ubuntu Alternate Install CD, and begin the installation.

4. Choose "guided installation", and choose each partition and assign it the appropriate mount point (/, /home, and {swap}), and let it format each partition as it installs.  Use ext3 or reiserfs for the / and /home partitions -- swap is its own special format.

5. Upon completion of installation, you should be able to reboot and have a Ubuntu desktop.  Any residual problem would be related to your Nvidia card only.

:)

---

