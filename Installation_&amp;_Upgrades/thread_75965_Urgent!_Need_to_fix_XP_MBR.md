---
title: "Urgent! Need to fix XP MBR"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by brschmid on 2005-10-14
i can't install linux because it wants to create a partition bigger than i have free space. i had it installed yesterday, but decided i didnt want to play with Ubunutu anymore, so i deleted the partitons and merged them back together with my XP install assuming GRUB was still installed on the MBR, but it was not. 

now i get GRUB to begin loading, then it fails and i cant boot to XP. I need some files off XP before i do a reinstall (if i need to, i don't want too)

also this is a laptop that does not have a floppy drive, so i can't even use the XP recovery console. 

is there any other way to get at this?

---

### Post by adwait on 2005-10-14
You can boot off the recovery CD of XP right? And run fixmbr..

---

### Post by brschmid on 2005-10-14
[QUOTE=adwait]You can boot off the recovery CD of XP right? And run fixmbr..[/QUOTE]
no

> also this is a laptop that does not have a floppy drive, so i can't even use the XP recovery console. 


---

### Post by sinistermilk on 2005-10-14
what grub error # is it?

---

### Post by adwait on 2005-10-14
I thought the XP recovery disk was a CD ROM!!!! Sorry.........

Maybe you could get hold of a Live CD of Knoppix and edit the grub files?

---

### Post by Guigui on 2005-10-14
The windows Recovery Disk is the Windows CD.
Boot from the CD. Then you can choose if you want to Install or Repair. When You're in the recovery console, run fixboot, then fixmbr.

---

### Post by jawaka on 2005-10-14
can you access grub's prompt?
if so, try

> rootnoverify (hd0,0)         (assuming that xp is on the 1st partition)
> makeactive
> chainloader +1
> boot

after that, inside windows you can install the recovery console as a menu option, in order to run fixmbr.

---

### Post by brschmid on 2005-10-14
i got it. i was doing the recovery console wrong *whoops*

i had to go to my school to get the master admin password to access the recovery console, but i got it now, and it is all better. 

thank you all for your ideas.

---

### Post by k3vmcd on 2006-10-28
I ran fixboot and fixmbr and now I have lost my Windows partition.  It seems that fixmbr only works for FAT partitions and my Windows install is on a NTFS partition.  How do I recover windows?

---

### Post by krazyd on 2006-10-28
Have a look at my post [here]("http://www.ubuntuforums.org/showthread.php?p=1245053#post1245053"), and read the link provided. Not sure what you mean about NTFS - it's the default XP filesystem.

Hope this helps..

---

