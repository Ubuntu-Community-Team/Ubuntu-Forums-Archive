---
title: "xubuntu laptop install issues (no X) but laptop already runs debian..."
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by Choad on 2006-07-11
atm my sisters laptop runs debian sarge with kde. she gets on ok with it, but its only got 128 mb of ram so it tends to chug a bit wen she does more than 1 thing at a time :(

i know she'd get along great with ubuntu, but ubuntu needs 256, so i thought i'd see what the xfce branch is like :D and i must say im very impressed! last time i tried xfce, it didnt have a file manager, and was therefor useless imo.... all the stand alone file browsers were no good...

anyhow, im impressed with the live version that i got going on my laptop, but i can't get it to run on my sisters laptop. it goes through the boot procedure fine, but when it gets to switching to X it goes some crazy colours... mostly black and white and then kind of sweeps down in some crazy *** pattern...

it did this quite a bit when i was trying out other distributions on this laptop, but that was all so long ago i have forgotten most of how i fixed all the niggles.

ANYWAY....

i have done an lspci in the debian system

```

$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03)
0000:00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1420
0000:02:04.1 CardBus bridge: Texas Instruments PCI1420

```

and also, i shall attatch the whole /X11 folder. i would just attatch xorg.conf, but it runs on xfree86 and i have no idea how that thing works at all

sooooooo

how am i going to get xubuntu on this beast then? is it even worth it? is xubuntu fast on 128 mb of ram?

---

### Post by JSchwage on 2006-07-11
It'll definitely run with 128 MB of RAM. You could try using the alternate installer since 128 MB of RAM is the limit as far as I know.

---

### Post by R.v.Muilekom on 2006-07-11
Maybe you should try to change your xorg.conf driver to vesa?
Seems something with your dsplay driver..

Anyway, Good Luck

---

### Post by Choad on 2006-07-11
the problem is, i dont want to risk borking my sisters laptop, i dont know how much time i have spare to be fixing it, and i remember it wasnt the *most* fun i've ever had getting all the hardware working in debian.

its just damn anoying that you can't ctrl+alt+backspace or ctrl+alt+f(x)  to get to a terminal, then change the xorg.conf file, then try it out. what ever i try it either restarts x instantly or does nothing.

i dont suppose there is any command line arguments you can pass? i have tried the "safe graphics mode" option, and "live vga=771" but neither helped (the latter made it worse)

---

### Post by Choad on 2006-07-12
could someone at least tell me where the graphics card settings are in xfree86?  the equivilent to xorg.conf in x.org?

at least that way i have a fighting chance of getting the beast running

also, are there actually any circumstances where a card will *only* work under xfree86?

---

### Post by Choad on 2006-07-12
oooh i found these bits in a file that looks similar to xorg.conf

```

Section "Device"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
 #Option "NoUseBios" # needed for some Savage cards
# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
  Identifier  "Card0"
  Driver "i810"
  BoardName "unknown"
 #BusID  "PCI:1:0:0"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 16
  SubSection "Display"
  Depth 1
  Modes "1024x768""800x600"
  EndSubSection
  SubSection "Display"
  Depth 4
  Modes "1024x768""800x600"
  EndSubSection
  SubSection "Display"
  Depth 8
  Modes "1024x768""800x600"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1024x768""800x600"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1024x768""800x600"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1024x768""800x600"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1024x768""800x600"
  EndSubSection
  # Only the official NVIDIA driver supports twinview
  # these setting are an example
  Option "TwinView" "false"
  Option "SecondMonitorVendorName" "unknown"
  Option "SecondMonitorModelName" "unknown"
  Option "SecondMonitorHorizSync" "30-82"
  Option "SecondMonitorVertRefresh" "50-75"
  Option "MetaModes" "1024x768, 1024x768; 800x600, 800x600; 640x480, 640x480"
  Option "TwinViewOrientation" "RightOf"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection

```


am i correct in assuming that the laptop currently uses the i810 driver?

---

### Post by Choad on 2006-07-12
bump

ahaaaa! well, i stuck in my suse 10.1 cd to see if that graphical installer works, and it did!

is this proof that the laptop can work with x.org?

is this proof of anything?

---

### Post by tseliot on 2006-07-13
1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash (if not, just stop here)

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by Choad on 2006-07-13
from your stickied thread

[quote=me]
i can set the graphics driver to vga, and it works but cga is laaaaaaame! vesa does the exact same thing as i810
[/quote]

i have tried the i810, vesa and vga drivers, and the only one that worked slightly was vga. but it was on 8 bit colour depth and 640x480

i am thinking the easiest solution will be to try and get xserver-xfree86 installed.... but i can't find it anywhere!

does anyone know what i should add (and or remove) from my sources.list to enable me to apt-get install xserver-xfree86???

---

### Post by Choad on 2006-07-13
hang on a tick....

"  DefaultColorDepth 16 "

i just noticed that from my old x configuration file

do you think perhaps it is going mental because it is trying to run on colour depth = 24 ?

that is a very very likely reason no? if the laptop screen couldnt handle 24bit colour depth what would happen when i try to put 24 bit colour in to it?

---

### Post by Choad on 2006-07-13
woooooooohhhh!

glorious 1024x768 16 bit colour!

is there anywhere i should post this fix to help others with the same laptop?

---

### Post by Choad on 2006-07-13
hmmm ok this is a bit wierd.

for some reason, when i start it up it does exactly like before (by which i mean it doesnt work). only if i

a) plug in an external monitor and b) repeatedly switch back and forth between the external monitor and the laptop screen

does it work. it stops completely, no processor or hdd activity, until i switch the screen modes

wierd no?

where are the log files for the xserver kept? if i could have alook at them maybe i would be able to figure something out.

but hey, at least im writing this from with xubuntu ;)

---

### Post by Choad on 2006-07-13
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rowan"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (xfwm4:4599): WARNING **: The display does not support the XComposite extension.

** (xfwm4:4599): WARNING **: Compositing manager disabled.
glibtop: This machine has 1 CPUs, 1 are being monitored.
smooth_refresh is active = 1
/bin/sh: /usr/bin/esd: No such file or directory

(epiphany:4769): libgnomevfs-WARNING **: Failed to create service browser: Bad state

/bin/sh: /usr/bin/esd: No such file or directory
Error: No running window found
Thunar: Failed to open "~/": Failed to stat file "/home/rowan/~": No such file or directory
Thunar: Failed to open "~/": Failed to stat file "/home/rowan/~": No such file or directory
ssion manager is already running





--------------


that is my .xsession-errors file.

can you make anything of it?

---

### Post by Choad on 2006-07-14
bump

ffs....

---

### Post by Choad on 2006-07-14
i seriously can't believe no one has anything to say at all!

how popular is this distro again??

... :(

please someone help!

---

### Post by tseliot on 2006-07-15
> **Choad said:**
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rowan"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (xfwm4:4599): WARNING **: The display does not support the XComposite extension.

** (xfwm4:4599): WARNING **: Compositing manager disabled.
glibtop: This machine has 1 CPUs, 1 are being monitored.
smooth_refresh is active = 1
/bin/sh: /usr/bin/esd: No such file or directory

(epiphany:4769): libgnomevfs-WARNING **: Failed to create service browser: Bad state

/bin/sh: /usr/bin/esd: No such file or directory
Error: No running window found
Thunar: Failed to open "~/": Failed to stat file "/home/rowan/~": No such file or directory
Thunar: Failed to open "~/": Failed to stat file "/home/rowan/~": No such file or directory
ssion manager is already running





--------------


that is my .xsession-errors file.

can you make anything of it?
Did you try to set up XGL or what?

I would like to see your /etc/X11/xorg.conf.

Otherwise I guess I can't help you

---

### Post by Choad on 2006-07-16
no, this is an absolutely fresh install of xubuntu, with just the xorg.conf modded to use 16 bit colour by default

ill see about posting the xorg.conf.... will edit later

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82830 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82830 CGC [Chipset Graphics Controller]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

there ye go!

and my .xsession_errors for this session:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rowan"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (xfwm4:4654): WARNING **: The display does not support the XComposite extension.

** (xfwm4:4654): WARNING **: Compositing manager disabled.

(epiphany:4738): libgnomevfs-WARNING **: Failed to create service browser: Bad state

/bin/sh: /usr/bin/esd: No such file or directory

```

---

### Post by waldo05 on 2006-08-14
Im having the same problem, done a clean install of Xubuntu using the alternate cd on my laptop, but I cant get the screen to display properly and keep having to switch to an external screen, if i dont all the writing goes fuzzy. I have tryed using the dpkg-reconfigure xserver-xorg command to try and put in my settings but they dont seem to take effect. I managed to boot up to a GUI once, created some user accounts and restarted, but then was stuck back at the command line and cant get the GUI again.

---

