---
title: "Problem with 6.10 Installation. Hangs at gui."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Freeper on 2006-10-27
Hi, this is my first time posting here. I've tried to read all the rules about and before I post. I have searched extensively and haven't find the answer yet.

This is my first time installing linux on an x86 machine. I've messed around with live cds and even put linux on my xbox. I have partitioned my hard drive to be able to dual boot ubuntu and xp. My problem is when I try to install from the cd it goes to the loading  Ubuntu screen and loads then it goes to the gui and I see my mouse cursor and can move it but then all I see is a brown background and and thin white box in the middle of the screen with pixelated colors around it. I have no idea whats going on.

I've tried booting in safe graphics mood and I tried booting with 
live acpi=off noapic nolapic
This resulted in the following errors:
VFS: Cannot open root device "<NULL>" or unknown block (8,1)
Please append a correct "root=" boot option
kernel patch - not syncing : VFS : Unable to mount root fs on unknown - black(8,1)
Not the cd because it checked out ok and tried a drappr cd with same results.
With the same results. Please help.

Specs:
AMD 3200+
DFI lanparty
1 GB of gold ocz ram
7800 GT connected by dvi to sammy flat panel
250gb hard drive

Thanks

---

### Post by sam81 on 2006-10-27
I don't really know what might be going wrong 'cause I'm not familiar with your machine, and I'm not really a linux expert. However, a possible solution if you can't use the default cd with the graphical installer, could be to use the 'alternate cd' that provides a text-mode installer. Hope this might help.

---

### Post by RichGuk on 2006-10-27
I'm having the same problem with Kubuntu, it does the inital loading and then seems to be stuck loading the bit just before the KDE splash. I baiscally get a blue kde desktop background with a mouse cursor, I have move the mouse, and my second mointor just flashes pink, it doesn't do anything else and I left it for a good 10 mins.

Specs;

AMD X2 3800+
DFI Lan Party SLI-D
G.Skill 2GB ram
GeForce 7800GT

---

### Post by nogard5 on 2006-11-09
I am having the same exact problem.  As soon as the splash screen is supposed to come up on the desktop (after the initial loading is complete), a glitched graphic comes up instead, and nothing else works besides the mouse cursor.  I have tried everything I can think of to no avail.  I'm downloading the alternate install now to try that.

I'm also using an Nvidia 7800 GT -- that seems to be the common thread here...  I'm running on an amd64 x2 3800+.  I've tried both 32- and 64-bit live CD's with the same result.

I installed 6.06 a few months ago and ran into the same problem, except there, I could choose "safe graphics mode" and it worked fine.  In 6.10, "safe graphics mode" doesn't seem to have any effect for me.

If someone wants, I could post a screenshot (photograph) of the glitched screen to explain what we're talking about.

---

### Post by minorthreat on 2006-11-10
I'm having the same exact problem stated in this thread.  My desktop machine with an Athlon 64 3200+, GeForce 7800GT and 1gig ram (I'm not sure what mobo I have) stalls/hangs after the splash screen when is should be loading up KDM or KDE.  I get the blue background, and the mouse moves around.  My keyboard doesn't do anything either.

As someone else had mentioned above, I'm having the same type of flashing colors (pink if I remember correctly, but I'm at work right now and was messing around with my desktop at home last night) on my second monitor.  I also tried it without the second monitor plugged in, and it made no difference.

If it matters, I was previously running Ubuntu Dapper on this machine.  I didn't want to just update, and wanted a clean install.  This problem is occurring on both the live cd (even with safe-mode enabled) and on a full install.

I know it's not a CD issue, as I used the cd to install Kubuntu  on an old laptop (around 4 years old or so), a Dell Inspiron.  Live CD and install went flawlessly on that, and I had zero problems.

I'll look through my logs when I get home tonight to see if I can find anything useful in them.  Hopefully this gets solved, and hopefully the solution doesn't involve getting a new video card.  I specifically got an nVidia due to the ease of getting them to work with linux.

---

### Post by minorthreat on 2006-11-10
I just got home and went through all the logs in /var/log.

The following was the only error that seemed to be occurring and showed up 4 times in a row:

/var/log/kdm.log
```

X Error: BadDevice, invalid or uninitialized input device 166
    Major opcode: 144
    Minor opcode: 3
    Resource id: 0x0
Failed to open device

```

I don't know if this sheds any light on the problem, or if it's completely unrelated.  Just figured I would post what I saw.

If there are other log files I should look into, please let me know and I'll check them too.

---

### Post by liveforfunnow on 2006-11-10
If it helps, I have a 7800GT and an AMD processor as well. I see the same issue. I have a Dapper >> Edgy installation working, but I'd like to clean wipe and do Edgy from scratch. Does anyone have any ideas (besides text-based installer)?

---

### Post by minorthreat on 2006-11-11
> **liveforfunnow said:**
> Does anyone have any ideas (besides text-based installer)?

Just to let you know, I installed Kubuntu via the text based installer.  It's about as easy as the gui installer.  However, that does not solve the problem.  Not only does the LiveCD have the problem, but the clean install has it also...

---

### Post by dickmorrell on 2006-11-12
I've installed so many Ubuntu machines I've lost count and thousands of Linux installs over the last ten years - hardly a newbie.

IBM Thinkpad X30 machine - exact same problem as above - took three attempts to get it to install too.

This is the most problematic ISO install (tried upgrade - killed the box, tried Live and now Alternate - hangs at same place) that I've ever seen. I also don't remember a distro having so many problems with a release before yet silence from the "team".

Clues ?

Richard

---

### Post by InsomniacUK on 2006-11-12
Exact same problem here.

NVIDIA 6800XT this time.

---

### Post by java1 on 2006-11-12
Hey I'm getting father then you...my hangs al installing software at 15% left it over night..same.. Then tried Alt text base install it hangs just after chosse your country...blue screen...

---

### Post by chuckn on 2006-11-12
Hi,

Just installed 6.10 and have a little problem. When i get to the log in screen and enter my pasword, the screen goes black for a few seconds and then jsut goes back to the login screen.

Thanks for the help.

Chuck

---

### Post by nogard5 on 2006-11-13
I got it working!  :D 

> **liveforfunnow said:**
> I have a Dapper >> Edgy installation working, but I'd like to clean wipe and do Edgy from scratch. Does anyone have any ideas (besides text-based installer)?

I also had a Dapper >> Edgy installation working, and wanted to wipe clean.   I had the same problem (I posted a couple days ago in this thread), but I finally got it to work.

I had to install using the alternate install CD, since the Live CD wouldn't boot.  Once Edgy was installed, it still had the same problem at login, however.  So I booted into recovery mode (single user) and installed the following packages:

[LIST]
[*]linux-restricted-modules-2.6.17-10
[*]nvidia-glx
[/LIST]

Then I modified /etc/X11/xorg.conf, under the "Device" section, and changed the driver from "nvidia" to "nv".

I'm pretty sure that was all I did to get it to boot into X.  I have changed a few things since then though (trying to get beryl & the nvidia beta drivers going), so I may be missing something.

It must be a driver compatibility problem with the 7800GT(X) and whatever NVidia driver is included with Edgy.  Strange that Dapper worked fine with it though...

---

### Post by liveforfunnow on 2006-11-13
thanks for the info, nogard5. i'll try this tonight and post again with my results!

---

### Post by minorthreat on 2006-11-13
nogard5: Thank you very much!  I just tried that out and it worked perfectly (at least for one monitor).

I used my old xorg.conf (that I thankfully backed up) to get both monitors working.  I have two Dell 1703FP's.  This is my xorg.conf at the moment, in case anyone wants to see how I got dual monitors working.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Mar 29 14:43:26 PST 2006

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

Section "ServerFlags"
	Option		   "Xinerama" "false"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#	Identifier		"Configured Mouse"
#	Driver			"mouse"
#	Option			"CorePointer"
#	Option			"Device" "/dev/input/mice"
#	Option			"Protocol" "ExplorerPS/2"
#	Option			"Buttons" "7"
#	Option			"ZAxisMapping" "6 7"
#EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
  identifier "DELL 1703FP"
  vendorname "Dell"
  modelname "Dell 1703FP (Digital)"
  HorizSync 30.0-80.0
  VertRefresh 56.0-76.0
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
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 1.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
	Option		   "RenderAccel" "True"
	Option		   "TwinView"
	Option		   "MetaModes" "1280x1024,1280x1024; 1280x1024"
	Option		   "TwinViewOrientation" "RightOf"
	Option		   "SecondMonitorHorizSync" "31-80"
	Option		   "SecondMonitorVertRefresh" "56-76"
	Option		   "ConnectedMonitor" "DFP,DFP"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NVIDIA Default Card"
  Monitor "DELL 1703FP"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@75" "1280x960@60" "1152x864@75" "1280x1024@60" "1024x768@60" "1280x960@75" "1024x768@70" "1400x1050@60" "1024x768@75" "1600x1200@60" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection



```

---

### Post by Brain_Recall on 2006-11-13
I'm suffering the same problem. Like others, I wanted to do a reinstall since my upgrade went less then stellar.

Specs:

    * AMD Athlon 64 X2 3800+
    * ABIT AN8-Ultra with uGuru Pannel
    * Corsair XMS Pro 2x512MB
    * eVGA nVidia GeForce 7800GT
    * 2x 250GB Wester Digital WD2500YD RAID Edition
    * Leadtek WinFast TV2000 XP Deluxe
    * Creative SoundBlaster Live! Value
    * US-Robitics 56K Performance Pro PCI modem
    * Toshiba  SD-R5002 DVD-RW
    * Yamaha CRW-F1E CD-RW
    * Koolance PC-601BW
    * Antec TrueBlu 480

Dapper LiveCD would work if I did the safe graphics mode. Edgy doesn't work for any of them. I hate Edgy more every day.
It actually almost looks like the driver is trying to force a color bit depth other then 24 bit, something I saw in some early Dapper Flights. Is there any way to edit the xorg.conf before it is used?

---

### Post by minorthreat on 2006-11-13
Brain_Recall: You should be able to do a text install.  Even though I couldn't boot up the LiveCD, the text install worked perfectly.  Once you have it installed, boot in recovery mode.  From there, install the nVidia drivers.  If you need help on that, TSEliot (not sure on spelling) has some detailed HowTos that are very easy to follow.  Everything should then be working perfectly.

---

