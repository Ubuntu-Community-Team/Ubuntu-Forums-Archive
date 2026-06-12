---
title: "Need help installing from scratch"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by moe3 on 2014-03-17
Hello,
I've been looking through the forum and searched Google, but I can't seem to find an answer for what I'm doing.  And, quite frankly, I'm surprised.  I've got an extra computer, I've wiped that hard drive, and now I want to install Ubuntu.  There is tons of info about installing from Windows, dual boots, and other scenarios, but I can't seem to find any for a straight install that starts with erasing your hardrive.  

I've already tried to install Zorin 8, but couldn't get it to work.  It seemed to work, but then after the install I got a boot disk error.  Since then, I've realized that I think Ubuntu is actually what I want, so I'm looking to find a step-by-step (based on what I"m working with) that will get me up and running.  So, hopefully someone has a couple of minutes to set me straight.  I"m pretty good with computers, but my experience is all with DOS and Windows: this is my first try with anything Linux.

Here's my situation:
The computer: 
CPU: AMD 5000  2.6ghz Dual Core
RAM: 2 gb DDR2
HDD: 380 gb Barracuda something or other
and, a 1gb video card

The Software:
I've got a copy of the Ultimate Boot Disc
Latest Ubuntu iso.  

So, I'd really appreciate some help with using Parted Magic (or whatever from the Ultimate Boot Disc) to erase, partition, setup the hard drive so that I can install Ubuntu and then be up and running and happy with my new OS.

Thanks in advance!

---

### Post by Bashing-om on 2014-03-17
moe3; Hi ! Welcome to the forum.

There is good reason why ubuntu is touted as most user friendly.
> 
this is my first try with anything Linux.

May I suggest that you do your first ubuntu install in that most easy and straight forward no hassle, done and over with manner ???
The no hassle way ( 15 minutes with a broadband internet connection )

1. Did you verify the .iso file as unchanged from that of the source ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. Burn the .iso as an image to disk:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3. Boot the installDVD, soon as bios screen clears, depress and hold the right shift key -> language screen, escape key to accept the defaults -> boot options screen;
Boot options screen -> "check disk for defects".
5. Choose "try ubuntu" Play with the system and check that all devices are recognized and functioning - A wired internet connection is strongly advised ( many times the wireless connection can not be established right off the bat)
6. Disk checks/system check all  good -> choose "install ubuntu" !
The installer will take care of EveryThing ! .. Will format, set up the default partitions, detect and set up the hardware interfaces - everything -. just choose the option "erase entire disk and install ubuntu" The install wizard will do just that , erase the hard disk and install ubuntu with a default partitioning that will work great and last you a long long time.
All you have to do is answer a few simple set up questions - pay close attention to the user name you choose for the system and most important is the Password you will set .. Tattoo that password to the back of your eyelids ! You can not live life in ubuntu without that password. This default setup will more than suffice for the time being. Later when you are comfortable with ubuntu you may consider a (RE-)install that at that time will suit your particular needs. And that is only saying if there is a valid reason to change from the default setup !. - say set up a separate /home partition [later] - 


We are here in the event that there is any difficulty - or something that you do not comprehend !


1st time around, 
[INDENT][INDENT]keep it simple
[/INDENT][/INDENT]

The install wizard will take care of everything ! 20 minutes and you are done. Up and running.

---

### Post by fantab on 2014-03-17
+1 to 'Bashing-om's post.

Here is a pictoral installation Wiki: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Remember, at the 'Installation Type' dialog choose "**Erase Disk and Install Ubuntu**". This option will erase/format the HDD and install Ubuntu after partioning the HDD accordingly.

---

