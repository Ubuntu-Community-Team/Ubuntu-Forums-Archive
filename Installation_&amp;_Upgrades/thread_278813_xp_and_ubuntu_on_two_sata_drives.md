---
title: "xp and ubuntu on two sata drives"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by ulikhan9 on 2006-10-16
Ive been having all kinds of problems trying to get ubuntu onto my computer. I have two sata hdd drives and what I am trying to accomplish is to have windows xp on my first 80 gig hd(already set up), and ubuntu on the second 250g hd. The second hd has a 75gig mirror of my c drive, and the remaining 180gig is unallocated. Does anyone else have this setup - if not, is there something wrong with this setup that is not allowing me to install ubuntu or knoppix?:confused:

---

### Post by benblout on 2006-10-17
At what step in the install are you having problems understanding what to do next, or are you getting an error or system hang at some point?

-Ben

---

### Post by gn2 on 2006-10-17
> **ulikhan9 said:**
> Ive been having all kinds of problems trying to get ubuntu onto my computer. I have two sata hdd drives and what I am trying to accomplish is to have windows xp on my first 80 gig hd(already set up), and ubuntu on the second 250g hd. The second hd has a 75gig mirror of my c drive, and the remaining 180gig is unallocated. Does anyone else have this setup - if not, is there something wrong with this setup that is not allowing me to install ubuntu or knoppix?:confused:

This may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

There's useful info from Bulldog later in the thread which gives a means of achieving the main aim of keeping Grub off the windows MBR and dual-booting on two drives where you can't access a boot device selection menu at boot time.

---

### Post by joff13 on 2006-10-17
1)install Xp in an HD
2)install linux in the other
3)on the MBR of the disk that the bios look for install grub or whatever
4)read grub man to know how it works

(hd0) = /dev/hda = 1st master
(hd1) = /dev/hdb = 1st slave
(hd2) = /dev/hdc = 2nd master
(hd3) = /dev/hdd = 2nd slave

(hdx,0) = 1st partition
(hdx,2) = 2nd partition
and so on

---

### Post by ulikhan9 on 2006-10-17
The ubuntu installation gets to the 100% mark and then my screen turns black, cursor at top left corner, then computer hangs. I thought that all I have to do is install ubuntu on the second sata drive but other forum messages are saying I have to disconnect my first drive with xp on it.

---

