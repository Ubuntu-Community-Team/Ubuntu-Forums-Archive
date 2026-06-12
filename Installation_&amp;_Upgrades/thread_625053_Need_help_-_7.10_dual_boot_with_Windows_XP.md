---
title: "Need help - 7.10 dual boot with Windows XP"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Bozebo on 2007-11-27
OK, I'm wanting to get Ubuntu 7.10 to dual boot on this machine with my currently installed Windows XP (it came on the computer).

I am running Ubuntu off the live CD at the moment and I had a look at the install process but I will need some help getting it installed without removing Windows, I have tried to follow some tutorials (including this one: [http://digitalgraphy.wordpress.com/tag/dual-boot/](http://digitalgraphy.wordpress.com/tag/dual-boot/))

But I get confused at step 5 because my HD (about 360 GB) is not currently partitioned in a way that I can follow the tutorial. Here is what I am shown on the manual disk partition part
(can't save any screenshots)
----------------------------------------
(Device  Type  Mount Point  Format?  Size  Used)

/dev/sda
  /dev/sda2  fat32  /media/sda2  [ ]  4375 MB  2900 MB
  /dev/sda1  ntfs  /media/sda1  [ ]  355702 MB  unknown
----------------------------------------

so, I presume /dev/sda1 is the partition that Windows is on (quite fresh, I am sure it is only using about 20GB at the moment), it doesn't seem to want me to resize that partition to free up space for the swap and for Ubuntu.

I need a lot of help getting this working, and I noticed that this forum is very active and I am also quite sure that a lot of people here like Linux and want more people using it, so help me join you :D

TY in advanced

---

### Post by CanonKen on 2007-11-27
[This thread]("http://ubuntuforums.org/showthread.php?t=602650&page=2") helped me when I was doing it, I managed it no trouble at all, have a read but sure someone will be along to help you better than I can

---

### Post by twist2b on 2007-11-27
DO NOT do it on ubuntu (creating a seperate volume
GO ON XP
then when you open start menu right click on computer and click on manage.
go to something like disk management i think
right click on the XP volume and select shrink.
choose the size you want
go to live cd and install and then when it asks you what you want to do with your partitions select *use largest continous free space*
there you go. very simple and let me know if you have any problems.

---

### Post by Bozebo on 2007-11-27
ooh, I am trying that now (actually i used the gnome partition editor instead of the windows one). Well It has shown me the options that the tutorials always mentioned but didn't exist for me, about to install it now :D

thanks
:popcorn:

EDIT:
OK, now it wants to know 'device for boot loader installation'
the default is '(hd0)'
Does that mean it will be the default selection and windows will be hd1?

Because I want windows to be the default option

---

### Post by torgrot on 2007-11-27
sda2 is probably a recovery partition to restore the computer to an as purchased condition.  I have used Gparted on windows xp systems with no problem, on Vista systems it can be a little risky, which is I suppose like being a little pregnant.  Even a little bit is to much.

torgrot

---

