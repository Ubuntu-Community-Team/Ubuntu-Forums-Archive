---
title: "Freezes on installation (partition table?)"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by dmix on 2007-07-06
I'm trying to install ubuntu 7 x86 but my computer freezes during installation everytime. 

The freeze: sometimes stalls completely on the screen, other times the screen will be distorted with lines shaking (video card style error) and 1 time it rebooted randomly

From what I can see the problem could be in 2 areas.

1- partition is messed up, install freezes at 5% where it says creating partition. Originally I reformatted from an XP installation, after I wasnt able to resize the current partition due to an error (no details) so I completely removed xP and started from scratch. I've run partition magic and get table related errors. All tutorials say to delete the partitions and recreate them. I've done this about 20 times and restarted the install as many times with no luck. 

Is there a way to completely remove the partition table and start from scratch? 

2- video card, under "restricted drivers" a NVIDIA-glx driver comes up from my geforce 6100, which is not properly installed from the beginning. It downloads fine from the cd-boot up but theres no way to restart tp get it to come in effect. But otherwise ubuntu runs smoothly from the disk... pre-installation.

Set up:
nForce 405 (6100) Asrock motherboard
AMD 64 3800+ 1gb ram
On board ethernet connection

Currently posting from ubuntu disk boot, love it so far, shame it doesnt install properly

---

### Post by bmorency on 2007-07-06
are you using the desktop install cd?  when I tried the desktop install cd on my system it would freeze when i tried to partition my hard drive.  So I downloaded the alternate install cd and i got it installed no problem. I find the alternate cd works a lot better for some reason.

---

### Post by dmix on 2007-07-08
Found the solution to both the problems:

1) parition was fixed after using the repair console from an XP disk and using FIXMBR

2) video problems were fixed by selecting a different resolution instead of VGA in the  pre-installation drop down menu

works beautifully

I'm downloading kubuntu and I'll definatley use the alternate iso

---

