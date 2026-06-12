---
title: "Display drivers"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Billyh on 2009-11-27
Since upgrading to UBUNTU 9.10 my only display choice is 800X600 which is not what I want. The display is a BENQ 22 inch and the video is part of the INTEL chip set 865G I have looked at the forums and cant find a fix for my problem

---

### Post by Grenage on 2009-11-27
What is the exact model of your monitor?

Also, please post the output of:

```
lspci | grep VGA
```

---

### Post by Billyh on 2009-11-27
Monitor is E220HD
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Gee that was quick

---

### Post by Grenage on 2009-11-27
If you make a backup copy of /etc/X11/xorg.conf and then replace it with:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "BenQ E2200HD"
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1080"
EndSubSection
EndSection
```

Reboot the machine; how does it fare?  If that doesn't work, try adding a BusID:

```
Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
BusID "PCI:0:2:0"
EndSection
```

---

### Post by Grenage on 2009-11-27
If the refresh rate is off, try changing:

```
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
```

to:

```
HorizSync 67.16 - 67.16
VertRefresh 59.96 - 59.96
```

That should 'hard-code' it to 60Mhz.

---

### Post by Billyh on 2009-11-27
These changes made no difference at all. It looks like XORG isn't being used at all

---

### Post by Billyh on 2009-11-29
> **Billyh said:**
> These changes made no difference at all. It looks like XORG isn't being used at all
How do I find out if xorg is being used?

---

### Post by Grenage on 2009-11-29
There appears to be an issue with the Intel drivers on Karmic, a lot of people are having issues, specifically with higher resolutions.  While I doubt it will work, what does the following xorg.conf do for you?

```
Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1920x1080"
EndSubSection
EndSection
```

---

### Post by Grenage on 2009-11-29
Also, can you post the output of the following:

```
sudo apt-get install xresprobe
sudo ddcprobe
```

---

### Post by Billyh on 2009-11-29
> **Grenage said:**
> Also, can you post the output of the following:

```
sudo apt-get install xresprobe
sudo ddcprobe
```
bill@billubuntu:~$ sudo apt-get install xresprobe
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  op-panel python-pychart python-quixote1 binutils-static python-medusa
  sqlite3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xresprobe
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 19.6kB of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe xresprobe 0.4.24ubuntu9 [19.6kB]
Fetched 19.6kB in 0s (49.6kB/s)
Selecting previously deselected package xresprobe.
(Reading database ... 138102 files and directories currently installed.)
Unpacking xresprobe (from .../xresprobe_0.4.24ubuntu9_i386.deb) ...
Setting up xresprobe (0.4.24ubuntu9) ...
bill@billubuntu:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)865G Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)865G Graphics Controller Hardware Version 0.0
memory: 8000kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail
bill@billubuntu:~$

---

### Post by Billyh on 2009-11-29
> **Grenage said:**
> There appears to be an issue with the Intel drivers on Karmic, a lot of people are having issues, specifically with higher resolutions.  While I doubt it will work, what does the following xorg.conf do for you?

```
Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1920x1080"
EndSubSection
EndSection
```

You were right this code made no difference at all as far as I can see.
I don't know if it makes any difference but the sound and display hardware are both on the motherboard and I noticed that I don't have any sound either.
Also I noticed that since I installed Karma the previous version in the boot list is changed i,e, games have been changed to Karma but the screen is the same as before the upgrade.

---

### Post by Grenage on 2009-11-30
Then I can only assume the graphical problem is down to the Karmic Itnel drivers.  What do you mean by:

> the previous version in the boot list is changed i,e, games have been changed to Karma but the screen is the same as before the upgrade

---

### Post by Billyh on 2009-11-30
The previous version Jaunty I think. When I upgraded it left the previous entries in the boot list when booting so I Just select Jaunty and I get a decent screen which makes it much easier to read this forum but the sound has gone. The funny thing is that the xorg.conf in jaunty is the same as whatever I put into Karma so is xorg being used?.
I will be away for 4 days and will watch the forum but I won't be able to try anything on the computer so don't give up on me as I really want to use UBUNTU instead of windows

---

### Post by jaylsi on 2009-11-30
Did you try 9.10 live CD? What kind of resolution do you get from it?

---

### Post by u.b.u.n.t.u on 2009-11-30
> **Billyh said:**
> How do I find out if xorg is being used?

If xorg.conf exists in /etc/X11 then by default it is used. The problem is however, that xorg.conf may be incorrect or read incorrectly and thereby cause problems.

For example, my montor 22" displays the correct resolution and refresh rate when no xorg.conf file exists. As soon as a xorg.conf file exists, Ubuntu freezes at boot, I need to reboot into recovery mode and use the terminal to delete the file.

---

### Post by Grenage on 2009-12-01
```
Section "Monitor"
Identifier "Monitor0"
VendorName "DCLLCD"
ModelName "DCL20A"
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1920x1080"
EndSubSection
EndSection
```

Try this; someone had some success using metamodes yesterday.

If that doesn't work, try swapping *Depth 24* with *Depth 16*.

---

### Post by Billyh on 2009-12-02
[QUOTE=jaylsi;8417411]Did you try 9.10 live CD? What kind of resolution do you get from it?[No I didnt]

---

### Post by Billyh on 2009-12-02
> **Grenage said:**
> ```
Section "Monitor"
Identifier "Monitor0"
VendorName "DCLLCD"
ModelName "DCL20A"
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82G33/G33"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1920x1080"
EndSubSection
EndSection
```

Try this; someone had some success using metamodes yesterday.

If that doesn't work, try swapping *Depth 24* with *Depth 16*.
What is metamodes and how do I get it?

---

### Post by Billyh on 2009-12-02
> **Billyh said:**
> [QUOTE=jaylsi;8417411]Did you try 9.10 live CD? What kind of resolution do you get from it?[No I didnt]

No I havent yet.

---

### Post by u.b.u.n.t.u on 2009-12-02
To my understanding the Live CD uses the default VESA driver, that is, no xorg.conf.

---

### Post by Grenage on 2009-12-03
> What is metamodes and how do I get it?

My mistake, I meant modeline; when you get back to your PC, let us know if the config makes any difference.

---

### Post by Billyh on 2009-12-06
:KSModeline did the trick see [http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/) . I still don't have any sound can you help or should I make a new query.
Oh! Thanks for all your help I learned a lot from the exersize!!!!!!!!!!!!!!!!!:KS:KS:KS

---

### Post by Grenage on 2009-12-06
Glad you got it working :)

I'd make another thread regarding the sound issue, you'll get more relevant attention.

---

### Post by motford on 2009-12-28
I had a similar problem with only two resolutions (640x480) and 800x600) after installing Ubuntu 9.10 with the Intel 865G Graphics Chip. 

I tried some of the other xorg.conf examples in this thread, then modified it a little and got the following one to work allowing higher screen resolutions.

Here is a copy of my xorg.conf file:

Section "Monitor"
    Identifier      "Monitor0"
    VendorName      "Unknown"
    Modelname       "Monitor 1024x768"
    HorizSync       31.5 - 61.0 
    VertRefresh     50 - 75 
    modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
    Identifier	    "Device0"
    Driver          "intel"
    VendorName      "Intel 82865G"
    BusID           "PCI:0:2:0"
EndSection

Section "Module"
    Load            "glx"
EndSection

Section "Screen"
     Identifier      "Screen0"
     Device          "Device0"
     Monitor         "Monitor0"
     SubSection	     "Display"
          Depth    24
          Modes   "1280x1024@60"   "1024x768@60"   "1024x768@75" "800x600@60"   "800x600@70"   "640x480@70"   "640x480@60"
     EndSubSection
EndSection

---

