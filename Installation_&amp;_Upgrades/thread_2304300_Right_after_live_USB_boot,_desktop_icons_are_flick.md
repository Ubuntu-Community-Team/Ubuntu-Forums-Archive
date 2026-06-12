---
title: "Right after live USB boot, desktop icons are flickering and unclickable"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by Dane_Iracle on 2015-11-25
After booting into the live USB version of Ubuntu 15.10, I am unable to proceed with installation because the desktop icons are rapidly flickering and slightly relocating, as seen on the attached video. I don't understand why this is happening, how to fix it, or how to proceed.

I am trying to follow the guides for the difficult case of the Intel Atom Processor, which is 32 bit, but running on a UEFI instead of BIOS. I've been struggling with this for the past 4 days and have lost a lot of sleep over it. 


Video of the problem: [http://tinypic.com/r/2iw2639/9](http://tinypic.com/r/2iw2639/9)


Computer I am trying to install on: [http://us.toshiba.com/computers/laptops/satellite/click/LX0W-C64](http://us.toshiba.com/computers/laptops/satellite/click/LX0W-C64)

---

### Post by sammiev on 2015-11-25
On boot at the menu press F6 and select nomodset.

---

### Post by Dane_Iracle on 2015-11-25
First off, you probably mean to say "press e" - not f6. Second, you probably mean to say "nomodeset" - not "nomodset". Third, I've already tried that. I have tried the commands to no avail: nomodeset acpi_backlight=vendor acpi_osi=Linux

---

### Post by sammiev on 2015-11-25
Press e then f6 and nomodeset... sorry was on my tablet .

Seems you tried most, hopefully others will be by soon.

Do you know what graphic card you have?

---

### Post by Geoffrey_Arndt on 2015-11-26
From your link, the graphics seem OK re chipset (Intel Integrated).   RAM is OK too.   

>  Have you checked if the install image re download integrity?

>  Before you proceed with install - - it's important to disable or turn off fast start/hibernation.

---

### Post by Dane_Iracle on 2015-11-26
What do you mean by "install image re download integrity"? The ISO I put on the USB stick is fine. I checked its integrity using the boot option. I also disabled fast start as well as secure start. 

I feel like I'm so close. I am able to boot into the OS on the USB stick, but it's just this damn flickering thing that doesn't make any sense. Yes - it seems like a graphics issue, but I have no idea where to start with fixing something like that. Are there any other boot commands to try?

---

### Post by RobGoss on 2015-11-27
Is this a old machine your trying to installing Ubuntu on? I find that most problems like this in my experience on older machines is do to a much needed updated graphic card and not enough ram..

---

### Post by Dane_Iracle on 2015-11-28
This is a brand new Toshiba Satellite Click LX0W-C64 Laptop, with the following stats, as pasted from the Toshiba web site [http://us.toshiba.com/computers/laptops/satellite/click/LX0W-C64](http://us.toshiba.com/computers/laptops/satellite/click/LX0W-C64)

> 
[SIZE=4]Performance[/SIZE]


**PROCESSOR***
Intel® Atom&#8482; x5-Z8300 Processor
**OPERATING SYSTEM***
Windows 10 Home
**GRAPHICS ENGINE***
Mobile Intel® HD Graphics


[SIZE=4]Memory and Storage[/SIZE]


**MEMORY***
2GB LPDDR3 1600 ( not user upgradeable)
**HARD DRIVE***
64GB solid state flash memory (eMMC)
**OPTICAL DRIVE***
Sold Separately: Toshiba USB Portable DVD SuperMulti Drive


[SIZE=4]Audio and Video[/SIZE]


**DISPLAY SIZE**
10.1" widescreen
**DISPLAY TYPE***
10 point multi touch support,WUXGA TruBrite® LED Backlit display with Wireless Display Support
**DISPLAY RESOLUTION**
16:9 aspect ratio,1920x1200
**AUDIO**
Dolby® Digital Plus&#8482; audio processing,Built-in stereo speakers


---

### Post by Geoffrey_Arndt on 2015-11-28
The atom cpu's with 2 Gib ram sometimes choke on the 3d hardware accel. on Gnome3 based DE's (unity, standard Gnome, Cinnamon).    I think Ubuntu Mate might be a logical next step re hardware compatibility.   It's a nice distro, and 100% Ubuntu.

---

