---
title: "Cant install Ubuntu 7.10"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by brenoelvio on 2007-11-21
I have a hp pavillion 1120 touchscrean.

when i try to boot from the live cd here is what happens:

1. i choose to boot or install ubuntu
2. it goes through a few loading screans
3. black screen with blinking cursor in top left
4. completely black screen

why won't it start? can anyone help me?

AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-64

12.1" WXGA High-Definition HP BrightView Widescreen Touch-screen Display
Display (1280 x 800) - Panel rotates 180° and folds flat

NVIDIA GeForce Go 6150 (UMA) with up to 559MB Total Available Graphics
Graphics Memory

2048MB DDR2 System Memory (2 Dimm)

200GB (4200RPM) Hard Drive (SATA)

802.11a/b/g/n (draft 802.11n) WLAN & BluetoothTM

LightScribe Super Multi 8X DVD±R/RW with Double Layer Support

Any one with a solution for this problem?

Thanks.

---

### Post by dustin0 on 2007-11-21
Its the graphic card, I have a geforce 6150 and I have the same problem

---

### Post by brenoelvio on 2007-11-22
Is there a solution for this problem?

---

### Post by Newbie1978 on 2007-11-22
Hello! I only try once to install Ubuntu ultimate 1.4 which I believe is base on Ubuntu feisty 7.04, the results where horrible not only the live dvd never load even when I try with "noapic" (which works fine in my other laptop an HP pavilion DV6000 Athlon 64 X2 1.7Ghz) but also when I try to get back in windows to research some info about my problem, I was shock to discover that I ruined my Windows Vista, I try some quick fixes to get back in graphics mode but nothing works so I end up re installing from partition (good thing this is a brand new laptop so I didn't t loose anything) I use the same Ubuntu Live DVD in both laptops and my HP DV6000 works pretty well on Linux, also both laptops uses x64 so I'm don't think the problem is the version of the OS or the DVD it self, when I try to load the Live dvd I get the PIDOF error first after a while goes on and then I get the xserver config error I set the configuration in the xserver and the progran goes on loading the live DVD but never finish the installation, I'm yet to try another time with a newly downloaded version of Ubuntu Gusty 7.10 x64, I don't know what to do now I'll appreciate all the help possible I'll even try any other distro of Linux before settle to run on Vista for the time being. Thanks for the help

PIDOF [3266] can't read sid from proc /1/stat
PIDOF [3266] can't read sid from proc /10/stat
PIDOF [3266] can't read sid from proc /11/stat
PIDOF [3266] can't read sid from proc /163/stat

Not sure if Gusty works in my HP laptop because Feisty didn't

---

### Post by Mangrove on 2007-11-23
The problem is not necessarily your graphics card, it is your monitor. Your Monitor does not support the "default" screen resolution/frequency that Ubuntu 7.10 uses once it enters a graphics mode.

I have an embedded nvidia 6100 and am using an RCA l32wd22 HDTV as my monitor and I am having the same problem. Hopefully someone here will have an answer. I had the same problem with CentOS 5, but with that distro, I had the option to install using a "text" mode...though once installed and rebooted, the "default" resolution X server wanted was still not right for my monitor...

---

### Post by drabzz on 2007-11-23
Sounds like a refresh rate issue; many flat screens operate within a very narrow range of refresh rates - usually around 60 Hertz. Sorry; I'm too green on Ubuntu/Debian to help any further :(

---

### Post by derby007 on 2007-11-23
I tried the AMD 64 Live CD version of Gutsy, and I couldn't get it to load either, i had to install with the Alternate CD. But..........Fiesty works OK. They must have changed the graphics (xorg.conf) settings from Fiesty to Gutsy !!

---

### Post by burgerearl on 2007-11-23
I have the same problem on my AMD64 desktop (loading, blinking cursor, then completely black). I am completely new to Linux, so I may be missing something. 

I tried booting in "safe graphics mode" and got a command prompt. I tried startx and got several errors:

sb_bread failed reading block 0x6fd7d
unable to read block (hex) size (more hex)
usr/bin/X11/X: error while loading shared libraries: /usr/lib/libz.so.1: cannot read file data: Input/output error
xinit: server error

re: refresh rates, I am doing this on an old CRT monitor

I have a factory graphics card (low end AGP).

Is there a solution here by installing with command line and modifying xorg or do I need to use 7.04?

Update: I've tried a different monitor, as well as 7.04, with similar results.

---

### Post by Newbie1978 on 2007-12-03
Hello, I try again to install Linux Ubuntu in my HP dv 6660SE, unsuccessfully this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work. Thank you

---

