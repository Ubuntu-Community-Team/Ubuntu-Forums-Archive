---
title: "computer does not boot to ubuntu 14.04 after installation"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Newbehans on 2014-04-30
I have bought a new computer an HP 110-200ed with windows 8.1. I want to change it to Ubuntu 14.04. 
I have an image dvd and have installed it, but when I restart the computer it displays the text
"media detected"
then it starts doing something with IPv4, succesfully it seems
after that it continues to do somthing similar with IPv6 and then it gives the message that there is no bootdisk or a faulty bootdisk

I tried a reinstall of ubuntu. It said that there was already a version of Ubuntu 14.04 present, but I don't seem to get there from the bootsector.

I have also noticed that the startup options have changed from when windows 8.1 was still active.

I doubt not that the faulty bit in all this is me, but what do I do wrong and how do I fix it.I work the computer at this moment managed by the live dvd which is far from ideal

---

### Post by kc1di on 2014-04-30
The problem is that you have secure boot/UEFI enabled. you can boot that way but the installer does not always configure it correctly.

Download and run boot-repair - you can find it[ Here.]("https://help.ubuntu.com/community/Boot-Repair")  follow the instructions on the web page and pay careful attention to the boot-repair dialogues when it tells you what to do. 
good Luck.

---

### Post by Newbehans on 2014-04-30
I had already suspected that the problem would be in the transition from BIOS on my old computer to EFI, but was at a loss what to do. I 'll try your remedy and thank you for helping

---

### Post by Newbehans on 2014-04-30
Hi, I've tried bootrepair, but it gives me no solution

The computer says it has the following startup options:
UEFI IPv4 Realtek PCIe FE Family thingi
UEFI IPv6 Realtek PCIe FE Family thingi
ubuntu

when I run it it tries the IPv4 option first with the message
Checking Media Presence
Media present
Start PXE over IPv4
Start PXE over IPv6

and then I suppose it tries ubuntu and comes up withe the message
No boot disk or flawed boot disk

Running bootrepair gave me an URL [http://paste2.org/](http://paste2.org/)698xvXBe

It has lots of information, but i cannot take it all in.
 Who could help me. It seems to me that my harddisk has no UEFI commands in it MBR

---

### Post by oldfred on 2014-04-30
I have not installed in 14.04 yet.

But I have this in my notes:

[https://sites.google.com/site/picasaresources/Home/Picasa-FAQ/picasa/troubleshooting/picasa-won-t-upload-sync-to-web-or-gmail](https://sites.google.com/site/picasaresources/Home/Picasa-FAQ/picasa/troubleshooting/picasa-won-t-upload-sync-to-web-or-gmail)
env WINEARCH=win32 WINEPREFIX=~/.tmp winetricks ie8
wine 'C:\Program Files\Internet Explorer\iexplore'
C:\Program Files\Internet Explorer\iexplore

---

