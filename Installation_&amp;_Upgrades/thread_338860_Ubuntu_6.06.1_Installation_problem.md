---
title: "Ubuntu 6.06.1 Installation problem"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by Squish on 2007-01-15
Yes, I have just purchased a new computer, and have finished putting it alltogether. I have yet to do a few things, the one at issue is installing my first OS.

Situation: I am trying to install an Ubuntu version 6.06.1, that I had obtained from a "Linux Format" DVD. I got the ISO, burnt it onto a DVD (all of this done from my other computer:) ), and booted the new computer from the fresh DVD. I get to the first menu, and when I try to proceed with "Run or Install Ubuntu", It starts working, but it stops after about 7 seconds, and posts this:
[17179570.680000] MP-Bios bug: 8254 timer not connected to IO-APIC
[17179570.844000] Kernal panic - not syncing: IO-APIC + timer doesn't work. Boot with Apic=debug and send a report.  Then try booting with the 'Noapic' option.
What does this mean? How do I go about this? 
This is my first actual build for a computer, and I am pretty good with the hardware side of things, but have little experience with linux, and with installing and configuring new operating systems. I am desperate to get away from windows, and besides, I can't afford it anyways. I just want to get my desktop running, and from their I hope to be able to learn and troubleshoot the rest of the way.

Basic system specs, incase they are important...

Western Digital Caviar SE16 250GB - SATA 3Gb/s Hard Drive x 2
Asus EN7600GS SILENCER GeForce 7600GS 512MB PCI-Express x 2
Asus CROSSHAIR - nForce 590 SLI (Athlon64/X2/FX/Sempron) PCI-E Socket AM2 
G.Skill Extreme F2-6400CL5D-2GBNQ 2GB PC2-6400 DDR2 Kit 
AMD Athlon64 X2 4600+ EE (2.4 GHz) Dual-Core Socket AM2 Processor
LG GSA-H22L (Black) 18x DVD±Writer with LightScribe
Enermax Galaxy 1000W Power Supply 

Is there any other information I forgot to add?
Thanks in advance

---

### Post by glabouni on 2007-01-16
this is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/76989").
there is a simple workaround. you just have to add the 'noapic' parameter to the boot command line and you should be fine. 

I don't recall how to do it for install cd but I do recall I found how to do it from the documentation you can access with the functions keys.

you should be able to find by yourself how to do this. if you can't please post again, and I'll do my best to explain you.

---

