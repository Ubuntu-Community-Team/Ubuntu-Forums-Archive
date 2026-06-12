---
title: "Hotplug subsystem"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by hacksign on 2005-11-22
I installed Ubunt 5 times now and finally understood I had to press CTRL+C when the voice hotplugs ubsytem.  However it says something about a CD-Rom problem and some other failings. After updating or installing after the first boot. I left the computer working because I am at school now and so I cant tell you what happened next. Can someone please help me? Nothing is plugged on the USB. I'll leave the specifics of my laptop.
Sistema operativo Microsoft® Windows® XP 
Processor INTEL Pentium Mobile Centrino 
Model 750 
Frequency processor 1860 
Memory RAM installed 1024 
Memory RAM modules DDR 2 SODIMM 400 
hard disk drive 160 2 hdd of 80 giga each
Burner DVD int/Dual Double Layer 
screen 17'' 
nVidia GeForce Go 6800 ram DDR dedicata 
RAM-video 256 
Modem PSTN internal 
LAN Card 10/100 Mbps 
Battery max. Idle Mode 2 howes 
Dimension in cm (LxAxP) 40,8 x 3,81 x 28,9 cm 
Weight 4,1 kg.

P.S. I reinstalled, stopped installation and did many stupid things before finally installing, did I ruin the laptop?

Thanks for help

---

### Post by magicfab on 2005-11-22
It's unlikely you have "ruined" your laptop while experimenting with install options.

Regarding the USB subsystem, I would check the BIOS to see if there are any options related to USB and I would experiment with that.

A good place to start looking after the machine has booted is in a terminal window, by typing "dmesg" you will get all hardware-related information and messages.

lsusb will list the USB devices you may have. Keep in mind even if you don't have anything *connected*, the fact that you have USB ports presente means the usb support is still loading.

---

### Post by hacksign on 2005-11-22
Well, I finally managed to install it, but I am really worried I ruined something on the pc. I did so many force shutdowns (Pressing the button more then 5 seconds), wrong installations that I think I broke something. Is there a way to check?

---

### Post by schdefan on 2005-11-24
If your system is running and everything is working then you don't have to worry about some damages. I installed more than 20 linux system on my laptop with so much partitions and a lot of times had to force a reboot with the power buttons.

When you boot you see a menu Ubuntu, memtest86+ in the grub menu to check your RAM. 
Try to find out what kind of harddisc do you have and download a disc utility program from the manufactors homepage. But be careful to not erase your disc with that tool!

But as I said if your system is running fine you don't need to worry. What do you think could be broken?

schdefan

---

