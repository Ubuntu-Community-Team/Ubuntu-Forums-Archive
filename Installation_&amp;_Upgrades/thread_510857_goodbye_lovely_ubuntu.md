---
title: "goodbye lovely ubuntu"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by youdidntseenothing on 2007-07-27
loved ubuntu, i learnt a frick of things that should be in every os. but, its goodbye for now, hardrive is smaller than a pea. i have windows and i have installed it (so its a dual boot system). how do i get rid of ubuntu+GRUB?
i can get rid of the partition and remake it to a ntfs, but how do i get rid of the mbr, which GRUB sits in? am i doing this right? thankkkkks

---

### Post by stchman on 2007-07-27
> **youdidntseenothing said:**
> loved ubuntu, i learnt a frick of things that should be in every os. but, its goodbye for now, hardrive is smaller than a pea. i have windows and i have installed it (so its a dual boot system). how do i get rid of ubuntu+GRUB?
i can get rid of the partition and remake it to a ntfs, but how do i get rid of the mbr, which GRUB sits in? am i doing this right? thankkkkks

Keep Ubuntu and ditch Windows.  That is my recommendation.

---

### Post by eentonig on 2007-07-27
Sad choice, but if you really want it. Boot in windows or a DOS bootdiskette and enter the following at the prompt

> FDISK /MBR

---

### Post by youdidntseenothing on 2007-07-27
should i do this before or after i have deleted ubuntu?

---

### Post by eentonig on 2007-07-27
Doesn't matter. But you wont be able to boot Ubuntu anymore once you did it.

---

### Post by mikewhatever on 2007-07-27
Take a look [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by romul on 2007-07-27
> **eentonig said:**
> Sad choice, but if you really want it. Boot in windows or a DOS bootdiskette and enter the following at the prompt


sad choice?
this is @@@@@@@@ system.im not a newbe and couldnt even install this ubuntu.
too many bags for now.definitely bye bye ubuntu.

---

### Post by mikewhatever on 2007-07-27
> **romul said:**
> sad choice?
this is @@@@@@@@ system.im not a newbe and couldnt even install this ubuntu.
too many bags for now.definitely bye bye ubuntu.

Bags or bugs, off you go. Good luck.

---

### Post by Pumalite on 2007-07-27
> **romul said:**
> sad choice?
this is @@@@@@@@ system.im not a newbe and couldnt even install this ubuntu.
too many bags for now.definitely bye bye ubuntu.

Obviously you are not for Linux.

---

### Post by M$LOL on 2007-07-27
> **stchman said:**
> Keep Ubuntu and ditch Windows.  That is my recommendation.

Advice like this doesn't really help the OP.

---

### Post by romul on 2007-07-27
> **Pumalite said:**
> Obviously you are not for Linux.


if you are for Linux then help me to install it.i never used Linux before but its not the problem.i tried both live cd and alternate one.with live cd my screen goes black forever when i press any option after booting for the first time to install.with alternate cd i can start the installation.then it stuck on 86% trying to download something.ok i turned my modem off and got lucky to finish the installation.but then the system wont load.have the black screen again.
i am sure it is all about bugs and incompability with my pc  which have latest hardware....nothing to do with me
but anyway if theris some walkaround then please tell me Linux guru.i know it is easier to say "im not for Linux"

---

### Post by Pumalite on 2007-07-27
Post your specs so we can help you better.
( I'm not a Guru, but I'll do my best to help you )

---

### Post by romul on 2007-07-27
i do dual boot with vista ultimate
gigabyte DQ6 board
2GB of ram
conroe 6600
BFG 8800
creative X-FI sound
WD SATA drive
ASUS 22" LCD
logitech G15 keyboard,G5 mouse

i dont know.maybe theris a special approach for installation.what i did is:left 2 partitions for vista and created 2 new.1 for root and 1 for swap.then restarted and booted the alternate cd.
choosed first option to install.choosed manual partition and choosed the partitions i created for root(bytheway what file system is better) and swap.all went good until it came to 
86% and was stuck.so i pressed ALT+F2 or something and saw its trying to connect to some http but have an error.so i turned modem off and started the installation again.
this time all went good until the end of installation but when i restarted it wont load.everything is working but have black screen stuck forever.and thats what happened with live cd from the begining
before i could even start the installation

---

### Post by Pumalite on 2007-07-27
You HAVE TO do the partitioning from WITHIN Windows, otherwise Vista will not allow you to run anything in that computer. In other words, you have to use Vista's partitioner. You have a good amount of memory, but your graphics card will represent a problem. So, after you have partition with Vista, I recommend you get the Ubuntu Alternate CD to avoid graphical interface problems. Once you are INSIDE the system, I'll help you get the appropriate driver for your card. Post back if you have problems. 

Cheers

---

### Post by romul on 2007-07-27
> **Pumalite said:**
> You HAVE TO do the partitioning from WITHIN Windows, otherwise Vista will not allow you to run anything in that computer. In other words, you have to use Vista's partitioner. You have a good amount of memory, but your graphics card will represent a problem. So, after you have partition with Vista, I recommend you get the Ubuntu Alternate CD to avoid graphical interface problems. Once you are INSIDE the system, I'll help you get the appropriate driver for your card. Post back if you have problems. 

Cheers

well.just edited my post before yours.read it please

and THE PROBLEM IS i cant get inside the system.it wont load or it is loading but i cant see cause of black screen

---

### Post by Pumalite on 2007-07-27
I believe the problem is your monitor. To make it work you have to edit your xorg file, but you cannot do it until you are in the system or at least you have a command line. I advise to try with a regular CRT monitor for the installation. In the meantime consult the Manual of your monitor and things like HorizRefresh, VertRefresh, frequency, etc. You will need that data to edit the xorg file later in the section 'Monitor'

---

### Post by romul on 2007-07-27
the problem is i dont have crt monitor at home.all TVs and monitors are LCD....
what now

---

### Post by romul on 2007-07-27
if ill connect some old tube Tv will it work?

---

### Post by pofigster on 2007-07-27
If you have s-video out on your card it ought to work.

---

### Post by Pumalite on 2007-07-27
I don't know, but it can't hurt if you try.

---

### Post by youdidntseenothing on 2007-07-27
best and easiest way i found was :
first run compmgmt.msc and format the linux partition
then get fixmbr.exe and put it in c:
then goto cmd, cd c:\ and then C:\> MbrFix /drive 0 fixmbr /yes
worked brilliantly.
thanksguys
dont worry, when i get a bigger harddrive, ubuntu will be there !

---

