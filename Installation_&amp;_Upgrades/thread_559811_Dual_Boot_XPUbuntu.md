---
title: "Dual Boot XP/Ubuntu"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by JustKoichi on 2007-09-25
I just made my laptop a dual boot with xp and ubuntu but i partitioned it wrong. I put more space on ubuntu instead of xp.

My question is there a way to change that? and if i delete the ubuntu partition and install it again would I be able to change the partition size?

Also is there a way to access files from ubuntu using xp and vise versa?

---

### Post by Pumalite on 2007-09-25
Post:
sudo fdisk -lu

---

### Post by JustKoichi on 2007-09-25
I'm new to linux. what do you mean?

---

### Post by Pumalite on 2007-09-25
I assumed you had Ubuntu. If yes, then go to Applications>Accessories>Terminal and type the command: sudo fdisk -lu (l is small L). Copy and paste the output here.

---

### Post by JustKoichi on 2007-09-25
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74397014    37198476    7  HPFS/NTFS
/dev/sda2        74397015   192394439    58998712+  83  Linux
/dev/sda3       192394440   195366464     1486012+   5  Extended
/dev/sda5       192394503   195366464     1485981   82  Linux swap / Solaris


i want 65gigs on xp and 35gigs on ubuntu

---

### Post by Pumalite on 2007-09-25
You can easily erase Ubuntu, then install again. Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, right click on XP partition and in the menu choose resize, then install Ubuntu again.

---

### Post by JustKoichi on 2007-09-26
How do i uninstall ubuntu? I tried using my xp disk but it didn't show up only thing it showed was the xp home edition.

---

### Post by logos34 on 2007-09-26
You don't need to uninstall ubuntu or use the XP disc--just fire up the live cd, open gparted and delete sda2, expand sda1/XP to the right, and reinstall ubuntu into the remaining space.  

You could also choose to shrink the existing installation on sda2 (drag slider to right) and expand windows into the freed space.  But a new install might be just as quick.

---

### Post by JustKoichi on 2007-09-26
so do i burn 
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

and boot from it?

edit:

when i booted from the cd this is what I got. 

[http://img218.imageshack.us/img218/9215/dscn5351fk7.jpg](http://img218.imageshack.us/img218/9215/dscn5351fk7.jpg)

[http://img218.imageshack.us/img218/3279/dscn5349wr8.jpg](http://img218.imageshack.us/img218/3279/dscn5349wr8.jpg)


No idea what any of it is.

is there a way to just uninstall it? and just install it again or do I have to do it the way you said?

---

### Post by chrisxp on 2007-09-26
try pressing enter and see if it boots up gparted

---

### Post by JustKoichi on 2007-09-26
Press Enter on which one theres a lot of option?

---

### Post by Scroobytec on 2007-09-26
Hi There JustKoichi

Have a look at [http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm) this will help no end, it did for me.

Hope you are not in a hurry, the expanding of your XP Part will take some time that is why Logos34 said install again.

GOOD LUCK

:popcorn:

---

### Post by JustKoichi on 2007-09-26
alright thats really helpful!

also another question is there a way to access my ubuntu files while using xp?

---

### Post by logos34 on 2007-09-26
> **JustKoichi said:**
> alright thats really helpful!

also another question is there a way to access my ubuntu files while using xp?

[http://www.fs-driver.org/](http://www.fs-driver.org/)

and for NTFS write support from within linux:
sudo apt-get install ntfs-config

---

