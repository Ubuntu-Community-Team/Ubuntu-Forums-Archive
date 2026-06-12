---
title: "Gutsy upgrade - stuck in BulletProof-X"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by ogryn on 2007-10-17
After upgrading to Gutsy from Feisty on the Nvidia drivers (8800GTS card), I get stuck in Bullet Proof X hell! LOL

The system upgraded, and I restarted.

System starts, X server fails to load, BP-X kicks in (yay!), I select *anything* in here (MESA, NV, Nvidia, Continue in Safe Mode) and nothing happens, just a black screen. After about 10 seconds the mouse cursor disappears and nothing. The hard disk light flashes randomly, but nothing happens! (doh!)

All I can do is reboot, and then BP-X kicks in again.

Is there any way of stopping BP-X so I can get to a terminal session? Then maybe I could find some logs at to what is going wrong? (any idea what and where to look for)

Thanks

---

### Post by TDub on 2007-10-17
have you tried ctrl-alt-F1 to get to the terminal? that works on regular X sessions, don't know about BP-X

---

### Post by ogryn on 2007-10-17
> **TDub said:**
> have you tried ctrl-alt-F1 to get to the terminal? that works on regular X sessions, don't know about BP-X

Yup. None of those Ctrl-Alt-F(x) keys appear to work. The keyboard is still active though because I can turn the Caps/Scroll/Num/Fn lights on and off (which usually stick in the case of a lockup).

---

### Post by TDub on 2007-10-18
Does your card have more than 1 head? its possible that when the mouse cursor disappears that the video is being directed incorrectly to the other head?

Just a thought.

TDub

---

### Post by buntunub on 2007-10-18
I had this issue during Gutsy RC. Seems they never bothered to fix it even though it was reported several times over, harped about in #ubuntu+1, and reported here on these forums on numerous occaisions. Bummer. Today is going to be one heck of a day with borked x configs. The problem stems from Gutsy being somehow unable to detect your video card/monitor, or at least for me it was (and has been reported). The only solution that would work for me was to get to command line using the safe mode and hack xorg.conf manually using nano. Upon reboot, all worked correctly EXCEPT for dual monitors via Screens and Graphics utility, which just broke my xorg all over again. Word to the wise, steer clear of that utility if your on Nvidia and use the nvidia-settings utility instead!

---

### Post by ogryn on 2007-10-18
Tried swapping heads on card to no avail.

Even selecting 'Test' on the driver/monitor selection screen makes the system hang in it's "on but can't do anything" state.

I tried going in to an old xorg.conf file and restoring that (recovery kernel), but no luck there either. I wonder if I can edit one to use the nv driver?

---

### Post by boudicca on 2007-10-18
> **ogryn said:**
> Tried swapping heads on card to no avail.

Even selecting 'Test' on the driver/monitor selection screen makes the system hang in it's "on but can't do anything" state.

I tried going in to an old xorg.conf file and restoring that (recovery kernel), but no luck there either. I wonder if I can edit one to use the nv driver?

Same here...after install and every reboot stuck in Could not detect screen, no matter what I select round it goes again.

Managed to get in, shutdown to root.....run sudo dpkg-reconfigure xserver-xorg setup video and screen, save my conf.....run init 3.....login and startx....but if I reboot again back to where I started could not detect......and round in circles. No matter what xorg.conf it just wrecks it on every cycle.



Running Dual Core P4 - Asus nvidia 7600GS - ASrock dual vsta 775 was running 7.04 compiz envy nvidia drivers

HELP! ;)

Shaz

---

### Post by boudicca on 2007-10-19
> **boudicca said:**
> Same here...after install and every reboot stuck in Could not detect screen, no matter what I select round it goes again.

Managed to get in, shutdown to root.....run sudo dpkg-reconfigure xserver-xorg setup video and screen, save my conf.....run init 3.....login and startx....but if I reboot again back to where I started could not detect......and round in circles. No matter what xorg.conf it just wrecks it on every cycle.



Running Dual Core P4 - Asus nvidia 7600GS - ASrock dual vsta 775 was running 7.04 compiz envy nvidia drivers

HELP! ;)

Shaz

*bump

---

### Post by rjonesx on 2007-10-19
Similar problem: 

AMD Turion 64 X2 mobile technology TL-52 / 1.6 GHz
NVIDIA GeForce Go 6150

Boots directly to command line after x fails to start.

---

### Post by Envirotech on 2007-10-19
I have had the same problems as you. Everytime i enable the restriced driver and reboot I end up at the safe boot promt.  I choose my monitor (plug n play (it has the proper vertical and horizontal sysnc settings)) and chose the propitary nividia driver 7600gs it boots but nividia-settings shows no nividia driver.  When I look at my xorg.conf it is full of failsafe info.  I have a backup of my original xorg.conf from before the update and paste that into the new xorg.conf and reboot I still end up at the bulletproof X menu.

7600gs

---

### Post by ogryn on 2007-10-19
Seems to be varying levels of success with NVidia's prop. drivers, but no fully desired outcome. Is there anything we could do that'd help the Bullet Proof X developers? (logs, dumps, whatever?)

I have a feeling I'm just going to have to reinstall when my disks come (thank you Shippit!)

---

### Post by Envirotech on 2007-10-19
Take a look at this thread.  [http://ubuntuforums.org/showthread.php?p=3575383&posted=1#post3575383](http://ubuntuforums.org/showthread.php?p=3575383&posted=1#post3575383)

It worked for me.

> **m2006h said:**
> try this:

Modify /etc/default/linux-restricted-modules-common to skip unnecessary kernel modules. 

DISABLED_MODULES="nvidia nvidia_legacy"

---

### Post by ogryn on 2007-10-20
> **Envirotech said:**
> Take a look at this thread.  [http://ubuntuforums.org/showthread.php?p=3575383&posted=1#post3575383](http://ubuntuforums.org/showthread.php?p=3575383&posted=1#post3575383)

It worked for me.

Nope. That one didn't work for me. Same old issues. :(

---

### Post by ogryn on 2007-10-23
Downloading the Nvidia drivers from the Nvidia website, then running the setup program under the Kernel Recovery mode (ignoring the warning messages from the installer), then a couple of reboots seems to have sorted out all my issues. 

I'm kinda glad I have Vista on a separate partition so I could get the drivers... :shock:

---

### Post by hfw on 2007-10-24
I had the same problem with my Gutsy upgrade.  After going in Buletproof circles, I gave up.  I created a seperate partition for /home, and reinstalled Gutsy from scratch...

So far I'm ok, but I haven't enabled my second monitor.

Tonight is my first night getting this far.

Good luck!
Hal

---

### Post by Falcorian on 2007-10-24
I have the exact same problems with the 8800 GTS.

I can get it to work fine with the drivers from nVidia's site, but bullet proof x (BPX) kills it pretty bad. I've gotten BPX to recognize one screen now, and the card with full drivers... But my other monitor is stuck off.

I may just go back to hand installing the drivers... :-/

---

### Post by hfw on 2007-10-24
ok, got two monitors after using the screen and graphics tool.  (i'm not a big fan) and messing around with my xorg.conf.

I think I used the nvidia-settings tool on feisty, w/o any issues,  Thenew Screens and graphics tool is not quite ready for prime time yet.  Feels like I'm beta testing it.

Only problem is now, compiz is not starting...

time to go look for answers...

hal

---

### Post by hfw on 2007-10-24
ok...everything works...

Here's my xorg.conf, which I pasted some of my old feisty xorg.conf into to get it to work.

Basically I turned off xinemera and enabled twinview....

Good Luck,
Hal


```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Boardname	"nv"
	Busid		"PCI:1:8:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"HP MX70"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option         "TwinView" "1"
    	Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0; CRT-0: 1024x768 +0+0, CRT-1: NULL; CRT-0: 832x624 +0+0, CRT-1: NULL; CRT-0: 800x600 +0+0, CRT-1: NULL; CRT-0: 720x400 +0+0, CRT-1: NULL; CRT-0: 640x480 +0+0, CRT-1: NULL"
	SubSection "Display"
		Depth	24										   Modes	"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  #screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "device" #   
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:8:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1280x1024"
	Horizsync	31.5-81.0
	Vertrefresh	50-75
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection
```

---

### Post by Falcorian on 2007-10-24
Glad it worked for you. I saved my Fiesty xorg that I created with nvidia-settings and it worked fine.

---

