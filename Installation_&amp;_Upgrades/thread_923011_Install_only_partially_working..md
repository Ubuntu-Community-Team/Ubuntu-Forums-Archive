---
title: "Install only partially working."
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by Newuser901 on 2008-09-17
Hi, this is my first post on this forum.

I'm trying to install ubuntu on a free drive. It's a 250gig WDC drive. I can install it fine and it even restarts after install but now won't restart to the OS. It just hits the load part and looks for cd/dvd and the says to hit CTRL + ALT + DEL. 

Does anyone know what causes this?

---

### Post by spiderbatdad on 2008-09-18
similar to this? [http://fixunix.com/ubuntu/389330-boot-hangs-indefinitely-until-ctrl-alt-del-pressed.html](http://fixunix.com/ubuntu/389330-boot-hangs-indefinitely-until-ctrl-alt-del-pressed.html)

---

### Post by Newuser901 on 2008-09-18
No, unfortunatly. I am using a CD install with the current front desktop version on the Ubuntu website. I start up the computer everything as far as the cd and HDD are concerned for it to install from the cd. 

It starts. 
I get the screen with options to check mem, check the disk(both of which I did and were fine.), try off cd, etc. 
I use the regular install option. 
It installs fine.
I start setting options like time zone/ city. 
get past step 7. though since the second time I installed, atleast, it skipped step 6.
It says you have to restart to finish installing or something. 
It gives the screen that says to remove cd from tray etc (if any)
I remove cd.
Comp reboots.
It gets to the PCI screen says Verifying DMI pool data..... checks to boot from cd/dvd twice then give the ctrl + alt + del line. As if there was no OS or something.

It does the same thing each time. I have to reinstall to get access unless I use off the cd as a trial. The only other thing I can think did was the first install I was using the live cd then started the install from there. I'm not sure if it went back to the desktop or not. But afterwords at some point it would not reboot to the OS and now just won't. Or everytime Install from just the cd without using the live cd it it won't go to the desktop and won't if I restart without starting over.

I installed by removing the HDD that had windows also. It is a fresh drive and I'm installing on the first drive listed which is to be used wholey for linux.

I can get the system specs too if htey are needed. I just need to look at some of the names again on the hardware. It's all modern though. Q6600, 2of4gigs (2X2gb) (from trying to install minix without much success.)gigabyte Mobo and vid card.

Does anyone have any clue how to figure this out? Does anyone know what can cause this?

---

### Post by spiderbatdad on 2008-09-18
It seems like the issue is one of having mbr on the other hdd. Grub should be installed on the mbr, is my understanding. Perhaps a bios setting can solve the problem, or perhaps a boot option I am not familiar with. Also I believe I have seen this issue dealt with by mapping the hdd's in menu.lst...in this case grub would still be installed to the mbr, as far as I know.

---

### Post by Newuser901 on 2008-09-18
Is there some way to see if it is loaded? and what do you have to do to make sure it is installed. Is there some official install or troubleshooting guide and info on operating systems. (I was trying to start to learn about them by installing minix but I had no success)

Do you know what type of bios settings I would be looking for. I kept thinking I saw something about making sure this type of thing was installed but it was instruction for minix 3. I was doing it before and keep thinking loosely the subjects I was looking up in it were for ubuntu and I looked at them already. lol I got myself all mixed up and I'm trying to backtrack and find info I saw earlier but I'm getting confused.

---

### Post by spiderbatdad on 2008-09-21
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
You should find everything you need here, to fix grub, discover your partitions, etc.

---

