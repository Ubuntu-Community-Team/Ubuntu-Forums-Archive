---
title: "No sound in Fiesty when Dual Booting XP and Fiesty"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by atek101 on 2007-09-19
I have a strange sound problem that I haven't been able to find a viable solution for, despite many attempts and troubleshoots. 

I have Windows XP Professional on my Compaq Presario V3000Z laptop on one partition; I installed this first. XP runs fine in all instances and I have had no trouble doing anything in XP (that's out of the ordinary).

Now, I run the liveCD for Ubuntu 7.04 Fiesty Fawn and everything works great. Sound works fine. I install it to another partition on my HDD with total success. GRUB is installed and easily recognizes both OS's. 

Immediately after installing Ubuntu, I restart the computer and boot up Ubuntu. It works like a charm! Sound works fine. I updated all the default packages as well. No trouble. 

I restart the computer and load Ubuntu again. No trouble at all. Sound works fine.

THEN, I restart and boot XP. XP works fine, no trouble. I shut it down. 

Then I turn it back on and load Ubuntu, and everything works fine except I have NO SOUND AT ALL. No Ubuntu drums, no system sounds of any kind, and when I play music it will play in the player but no sound will come out of the speakers. I've shut off the digital s/pdif device (IE something or other), turned on the alsa manager, raised the volume of every channel to maxiumum and unmuted, and still nothing.

 Even if I shut down Ubuntu and turn it back on and boot it up, I still get no sound. What's more, even when I boot up from the LiveCD I get no sound. What could be causing this problem?

I tried a couple fixes, including the m2-2 'flavour' thing. No luck at all. I've read that it could be a Plug and Play BIOS setting, but if so, I have no way to change that in my BIOS. 

What's more interesting is that if I wipe my HDD completely clen and then install JUST Ubuntu, the sound starts to work in Ubuntu again. 

EDIT: Even MORE amusing is that when I have no sound in ubuntu then delete my windows partition, sound in Ubuntu starts working again the next time I boot up!

Furthermore, with Ubuntu 6.10 dual booted I NEVER HAD THE PROBLEM. Sound always worked regardless of scenario. Ironically enough, 7.4 actually recognizes my quick launch buttons (touch buttons for volume above the keyboard) better than 6.10 did.



So what is my problem? Someone more skilled in Linux than I must have an answer to this question! 

Here are my basic specs:
Presario V3000Z CTO Notebook
AMD Turion X2 TL-52 (1.6Ghz)
nVidia GeForce Go 6150
Conexant HD Audio
80GB SATA HDD (2 partitions)
HP Quicklaunch Buttons
Windows XP Professional
Ubuntu 7.04 Fiesty Fawn 
GRUB

---

### Post by alejo on 2007-09-20
Same preblem here... compaq presario v3000 brand new

---

### Post by Pumalite on 2007-09-20
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

