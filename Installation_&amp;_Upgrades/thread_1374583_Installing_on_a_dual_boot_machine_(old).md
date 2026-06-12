---
title: "Installing on a dual boot machine (old)"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by folini on 2010-01-07
Hi everybody,
I'm new of this community and almost new of Ubuntu.
Here my  problem:
Two years ago I installed Ubuntu 8 on my PC with a dual boot with Win XP. I was not really impress by Ubuntu and after while I gave up and went back back to use only XP. 
Recently, after reading the Jono Bacon book (The Art of Community) about the Ubuntu community, I decided to give Ubuntu one more try. In the mean time I forgot the password of my old installation (excluding the upgrade option) and I got a new PC with Win 7.
In my plan the old PC should be converted to a full Ubuntu machine. Today I created the installation CD with version 10.8 for my old PC and started the installation with the goal of wiping out the entire HD (all partitions) with a new fresh installation. When the installation reached the point "30%: Detecting File System..." the video started flashing and the installation stopped. 
To solve the problem I run the original Win XP installation CD, created one single partition (destroying existing XP and old Ubuntu installations), formatted the big partition as NTFS and then tried again with Ubuntu installation. Same result: screen flashing, non progress.

The PC is quite a standard (old) no-brand PC. 

Any suggestion on how to fix this problem?

Thank you for your help,
       
Franco

P.S. The same problem appears when I try to run Ubuntu without installation from the CD

---

### Post by Project PWNED on 2010-01-07
Burn a copy of the alternate installer and try again, this should solve your problem.

---

### Post by folini on 2010-01-07
Thank you for your prompt reply!
I'll try and I'll let you know.

-- Franco

---

### Post by Sef on 2010-01-07
The alternate cd is a text based installer.  It is easy to use.   The only hard part would be if you decided to manually set up the partitions.   It is not that difficult to do, but the first time or two, it can be a bit confusing.

---

### Post by Project PWNED on 2010-01-07
If he wants to dual boot, it'll prompt him saying that Ubuntu wants this much space.

---

### Post by folini on 2010-01-07
First of all Thank you for your suggestions. 

Status update

As suggested I downloaded the "Alternate Installation".
The new installation went very well to the end (no more flashing). When I reboot the PC I see a text screen asking for a login (good), but the screen is again flashing continuously and the keyboard is not very responsive at all. 

Any new suggestion?

-- Franco

---

### Post by Project PWNED on 2010-01-08
How fast is your processor, how much RAM do you have and what kind of video card do you have?

---

### Post by folini on 2010-01-08
SUCCESS!

I found a screen during the boot asking if I want to update the packages. I did it and now the system runs perfectly! I writing this from my Ubuntu PC! I also installed the proprietary nVidia driver for my graphic card.

I believe the problem was related to my graphic card a nVidia GeoForce 6200 with 256 MB. The computer has a Pentium 4 2.3 MHz and 2GB RAM.

Thank you for your help!

Franco

---

### Post by Project PWNED on 2010-01-08
I'm using a system with similar specs. If you find your system running sluggish while using Gnome, apt-get install icewm icewm-themes, logout of the Gnome session, choose IceWM on the bottom and login with IceWM.

It's not as flashy as Gnome, but I'm enjoying the excellent responsiveness of the Window Manager compared to the Gnome bloat. 

I've got a P4 2.4Ghz, 2gb RAM, and an ATI Radeon 7500 video card and I have another Ubuntu system with P4 3.2Ghz, 512mb RAM and onboard video.

---

### Post by Bartender on 2010-01-08
Our PC, using an ASUS EN8400GS video card (nvidia) also flashed to black intermittently.  About once a minute the screen would go black for a half second, then come back.  Installing the nvidia drivers stopped the problem.

---

