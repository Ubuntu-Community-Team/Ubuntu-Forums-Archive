---
title: "606 A64 Live CD, and Alt A64 CD Problem"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by grunge09 on 2006-06-08
I have a new system, currently running XP Pro.  Wanted to get away from Bill Gates, So I heard about Ubuntu and d/led it and went to run the LIVE CD to check it out. 

I got the i386, A64 and Alt A64 CD's, boot off them Live CDS (i386, and A64) and Xserver comes up with a failure message and leaves me at a prompt.

My system is:

ASrock Dual Sata 939 MB (Has AGP & PCI-E slots) NOT OVERCLOCKED
     - Sata I Ports are on but not used
AMD 4000+ San Diego Core Retail CPU 
1 GB Corsair Value Ram
250 BG WD SATA II Drive on SATA II Controller
Some IDE DVD Rom Drive I had lying around.  It reads a burned ISO image bured at 24x so it can't be too old
Sapphire X850 PCI Express Card 256 bit GDDR3 16 Pipelines w/256MB RAM

Have a SMC Router on Cable Modem.  Router does DHCP.:-k 

I really did not mess with the bios at all.  Was not interested in overclocking the system.

I tried the Alt A64 CD, and I chose the OEM install, and it gets to the network config and right after that it hangs on me.  

Is this a bios Video card setting issue or something with RAID being enabled in bios and not being used?

Please Advise.

BTW Xp Pro runs fine, no problems, surfs web fine, I can access other systems on my local lan.

---

### Post by grunge09 on 2006-06-09
It is the Sapphire Radeon 850XT PCI Express Video Card.  

I checked the memory, ran the CD Check on affected system and comes up ok.  

AsRock Dual-Sata 939 board is listed as compatable less -eth0 not working, but when I get to a prompt I can ping other PC's on my network.

Also I took the Live disc to another A64 system with an AGP FX5200 Video Card and it worked like a charm on there, recognized sound, video, and my usb card reader for my camera.  And was surfing the internet.  

I lurked around and found that I CAN disable the SATA I controllers, and legacy USB support.  XP still works fine.  Just can not even get Xserver to run the GUI.

Any help would be appreciated, thanks in advance for a linux noobie.

---

### Post by grunge09 on 2006-07-03
I found out what fixed that.  I had to do this...

sudo nano /etc/X11/xorg.conf
go to the line that says: driver and change "ati" to "radeon"
press ctrl+x and save
Start X with "startx" followed with an enter.

that gets me into the Gui, everything works so far but SATA II HD is not detected.  I tried to run install from the lice CD Gui and the ALT CD OEM install and it hangs on the section where it should ask to create partitions.  From what I have found it is a problem with the lack of support with SATA II on the ASrock Dual 939 MB.  I guess I will ahve to wait for a future release for a fix right????

---

