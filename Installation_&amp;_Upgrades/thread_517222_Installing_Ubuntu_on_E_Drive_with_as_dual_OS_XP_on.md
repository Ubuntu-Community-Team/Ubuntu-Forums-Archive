---
title: "Installing Ubuntu on E Drive with as dual OS XP on C"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by rajumsrk on 2007-08-04
Hi guys 
I am new to Linux but very excited about it.
I have three partitions on my Hard Disk
I have Win XP on C and some application on D
I would like to install Ubunto on E which is 15 GB.
Is it possible ?

I am stuck at disk partition and root etc while trying to install.
After choosing the manual mode I am stuck up
what is the partition size etc that i need to choose
where do i have to allocate root directory?

regds

---

### Post by Pumalite on 2007-08-04
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
This Gparted is better, newer and has more functions that the one that comes with the installer. It's a small download. Burn to CD and boot. Read the documentation and you will know what to do. I recommend 500 MB for swap, 8 GB for '/', the rest for /home.

---

### Post by pigbig842001 on 2007-08-04
> **rajumsrk said:**
> Hi guys 
I am new to Linux but very excited about it.
I have three partitions on my Hard Disk
I have Win XP on C and some application on D
I would like to install Ubunto on E which is 15 GB.
Is it possible ?

I am stuck at disk partition and root etc while trying to install.
After choosing the manual mode I am stuck up
what is the partition size etc that i need to choose
where do i have to allocate root directory?

regds
Hey brother,

Try this idea. I had the same problem as yours. Put u'r WinXP CD in CD-ROM drive. Boot. Now, when you arrive at disk partition phase, delete the partition that you intend to use for ubuntu installation. As soon as that partition is deleted, remove WinXP CD and pop in the Ubuntu CD and reboot (reset button is lovely). When completely booted, start installer. Now you arrive at disk partiton phase. Select the **manual** method. Now, you will see the deleted partition as **unallocated space**. Double click on it and specify the size (I think 4 GB is enough for it, type **ext3**). Specify the mountpoint as "**/**". OK.

Now you will again see some space is left. Double click. Specify size (about 512 MB). Type **swap**. OK.

Now you will again see some space is left. Double click. Specify size (all the space which is left). Type **ext3**. Specify the mountpoint as "**/home**". OK.

Now, you are ready to roll. Next... next... next... you will know what to do next.

---

