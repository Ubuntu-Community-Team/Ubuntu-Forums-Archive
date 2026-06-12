---
title: "Install Goes Badly Wrong"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Dacky1 on 2006-11-10
[COLOR=#666666][FONT=Verdana]Where oh where do I start [/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]First of all I downloaded burned the iso of dapper, it runs fine in live cd mode although I have to run it in safe graphics mode otherwise the screen goes blank.[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]I try to install it but it cannot create enough space, so I try gparted through Ubuntu dapper, every change I make to the hard just does not happen, it just reverts back to normal.[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]So I try a full hard drive partition (although I want to dual boot with windows) and it freezes the laptop and has to be rebooted holding down the power button.[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]So I thought download edgy that might work, but no the live cd starts to boot but then the monitor goes off but I have sound and I can’t do anything, this is when I boot up in safe and normal.[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]I have restored my system but I do not have the option to choose the partition size for XP it just runs through the motions and completes.[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]I am using another Toshiba M70 – 144 laptop (my mates laptop)[/FONT][/COLOR]
**[COLOR=#666666][FONT=Arial]Satellite M70-144 Intel® Centr... [/FONT][/COLOR]**
**[COLOR=#666666][FONT=Arial]Part Number : PSM71E-01400DEN [/FONT][/COLOR]**
**[COLOR=#666666][FONT=Arial]Key Features [/FONT][/COLOR]**
[COLOR=#666666][FONT=Arial]- Intel® Centrino™ mobile technology including Intel® Pentium® M Processor 740
- Windows® XP Home Edition
- 60GB Hard Disk Drive
- 512MB DDR2 RAM
- 15.4" Toshiba TruBrite WXGA TFT display
- DVD Super Multi (Double Layer) drive[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana] [/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana]As much help would be much appreciated.[/FONT][/COLOR]

---

### Post by encompass on 2006-11-10
You should be able to see the partition size of your windows partition during install.
Have you confirmed the cd is ok? I have burned many from windows and Linux that have not work properly.  Check the cd integrity as a boot option.
Could you tell a little more about your laptop.  Especially the graphics card and ram. Ooops got the ram.  Thanks.
If the entegrity is bad... chack the md5sum of the file you are using.

---

### Post by Dacky1 on 2006-11-10
Graphics card:
manufacturer : ATI 
type : MOBILITY™ RADEON® X700 
memory : 128 MB 
memory type : DDR Video RAM 
connected bus : 16x PCI Express 
 
other stuff:
type : Intel® Centrino™ mobile technology including Intel® Pentium® M Processor 740, Intel® PRO/Wireless 2200BG network connection and Intel® 915PM Express chipset 
clock speed : 1.73 GHz 
front side bus : 533 MHz 
2nd level cache : 2 MB 
I have run the disc checker on the ubuntu live cd and that seems fine. But when it runs and comes to the hardware devices it says something like "hm error aborted" then runs fine doodly fine.

---

### Post by encompass on 2006-11-10
You may want to just try the text based alternate cd install... it sounds like your best bet.  You can then if you get the blank screen.  Select the vesa driver and go from there.
As for your partitions.  It is never recommended that you resize any partition unless you have to.  Many times, you can't resize them.
I would first create partitions with fdisk in windows.  And then install windows... then install linux.
So jsut delete all partitions with fdisk... make one partition for windows.  And leave the rest alot for your linux install.

---

### Post by Dacky1 on 2006-11-13
> **encompass said:**
> You may want to just try the text based alternate cd install... it sounds like your best bet. You can then if you get the blank screen. Select the vesa driver and go from there.
As for your partitions. It is never recommended that you resize any partition unless you have to. Many times, you can't resize them.
I would first create partitions with fdisk in windows. And then install windows... then install linux.
So jsut delete all partitions with fdisk... make one partition for windows. And leave the rest alot for your linux install.
Got the thing installed, but just get the blank screen and can't do anything, when I use my restore disk I don't have a choice for which partition to use it just formats the whole thing. I have given up as I have had to restore the system 5 or 6 times and spent a week trying to do this. The install went perfectly well on a Powerpc g4 but not on this.](*,)

---

