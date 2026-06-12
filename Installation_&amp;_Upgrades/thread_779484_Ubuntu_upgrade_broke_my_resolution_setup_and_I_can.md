---
title: "Ubuntu upgrade broke my resolution setup and I can't get it back!"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Daminator on 2008-05-02
My projector was a pain in the *** to set up. It literally took me months of coming back to it on and off to get the resolution I wanted. I finally got a xorg file that worked just right, and then upgrading to 8.04 of ubuntu seems to have completely broken my display.

I've posted below a copy of the old xorg file that I've been using fine in the past. Is there anything in here that would break 8.04, but work fine in 7.10? I've also attached the current xorg.conf which the system has modified during my efforts.

Also (this could be the cause of the problem), the nvidia drivers don't seem to like me in 8.04. I've always used Envy yo install my driver and it's worked flawlessly. I'm trying to use EnvyNG in 8.04, but it's struggling. If I try to install 169.12, it crashed every time. It seems to install 96.43.05 ok, but I can still only get 800x600 when I use the old xorg file.

I tried uninstalling all drivers and just enabling the Ubuntu restricted driver. It didn't like that, and too me to a low resolution mode.

I'm now running without any 3d acceleration at 800x600. Any ideas what could be going on? By the way, I have a FX5200 card.

Thanks
Damian

Old and worked well:
# xorg.conf (xorg X Window System server configuration file)
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

# Attempt to stop monitor going to sleep and need waking up
##Section "ServerFlags"
##	Option		"BlankTime"	"0"
##	Option		"StandbyTime"	"0"
##	Option		"SuspendTime"	"0"
##	Option		"OffTime"	"0"
##EndSection

Section "Files"
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


# these were the ones in the working benq 10W xorg.conf file that I modified.
#Section "Module"
#    Load           "glx"
#    Load           "v4l"
#    Load           "vnc"
#EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
###	Load		"vnc"
	Load		"glx"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"
	Identifier	"BenQ W100"
	Modelname	"BenQ W100"
	##    HorizSync       31.0 - 82.0
	##    VertRefresh     48.0 - 85.0
	##    # These are 'standard' mode lines I found at
	##    # [http://www.mythtv.org/wiki/index.php/Modeline_Database](http://www.mythtv.org/wiki/index.php/Modeline_Database)
	##    ModeLine       "480p" 23.94 640 664 736 760 480 482 488 525
	##    ModeLine       "720p" 74.16 1280 1320 1376 1648 720 722 728 750
	##    ModeLine       "1080i" 74.25 1920 1960 2016 2200 1080 1082 1088 1125 Interlace
	##    ModeLine       "1080p" 148.5 1920 1960 2016 2200 1080 1082 1088 1125
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Option		"DPMS"
	Option		"UseEdidDpi"	"FALSE"
	Option		"DPI" "120 x 120"
	##	see if removing this stops the weird movig edge of screen thing
	##	DisplaySize	325 182
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	##	Screen	0
	Option		"AddARGBVisuals"	"True"
####		Option		"AddARGBGLXVisuals"	"True"		Not sure where this came from, why it was there, or why it got removed
	Option		"NoLogo"	"True"
EndSection

#Section "Device"
#    Identifier     "nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
#    Driver         "nvidia"
#    BoardName      "nv"
#    Option         "AddARGBVisuals" "True"
#    Option         "AddARGBGLXVisuals" "True"
#    Option         "NoLogo" "True"
#EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"BenQ W100"
	# Allow VNC access to this screen
####	Option		"SecurityTypes"	"VncAuth"
####	Option		"UserPasswdVerifier"	"VncAuth"
####	Option		"PasswordFile"	"/root/.vnc/passwd"
	Option		"UseEDID"	"False"
	Option		"FlatPanelProperties"	"Scaling = native"
	Option		"ExactModeTimingsDVI"	"true"
	Option		"ModeValidation"	"NoDFPNativeResolutionCheck, AllowNon60HzDFPModes, NoEdidMaxPClkCheck, NoMaxPClkCheck, NoHorizSyncCheck, NoVertRefreshCheck, NoEdidDFPMaxSizeCheck, NoEdidModes"
	Option		"AddARGBGLXVisuals"	"True"
	# Disable modeline validating as much as possible
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		##		Virtual	1920	1200
		Modes		"1280x720@50"	"1280x800@60"	"1280x768@75"	"1440x900@75"	"1280x800@75"	"1440x900@60"	"1280x720@60"	"1600x1024@60"	"1280x768@60"	"1680x1050@60"	"1280x854"	"1680x1050@75"	"1152x768@54"	"1920x1200@60"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"720x400@85"	"640x350@85"	"640x400@85"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection



Current xorg file:
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# Attempt to stop monitor going to sleep and need waking up
##Section "ServerFlags"
##	Option		"BlankTime"	"0"
##	Option		"StandbyTime"	"0"
##	Option		"SuspendTime"	"0"
##	Option		"OffTime"	"0"
##EndSection
# these were the ones in the working benq 10W xorg.conf file that I modified.
#Section "Module"
#    Load           "glx"
#    Load           "v4l"
#    Load           "vnc"
#EndSection
#Section "Device"
#    Identifier     "nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
#    Driver         "nvidia"
#    BoardName      "nv"
#    Option         "AddARGBVisuals" "True"
#    Option         "AddARGBGLXVisuals" "True"
#    Option         "NoLogo" "True"
#EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	###	Load		"vnc"
	Load		"glx"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"
	
	##    HorizSync       31.0 - 82.0
	##    VertRefresh     48.0 - 85.0
	##    # These are 'standard' mode lines I found at
	##    # [http://www.mythtv.org/wiki/index.php/Modeline_Database](http://www.mythtv.org/wiki/index.php/Modeline_Database)
	##    ModeLine       "480p" 23.94 640 664 736 760 480 482 488 525
	##    ModeLine       "720p" 74.16 1280 1320 1376 1648 720 722 728 750
	##    ModeLine       "1080i" 74.25 1920 1960 2016 2200 1080 1082 1088 1125 Interlace
	##    ModeLine       "1080p" 148.5 1920 1960 2016 2200 1080 1082 1088 1125
	##	DisplaySize	325 182
	Identifier	"BenQ W100"
	Modelname	"BenQ W100"
	Gamma	1
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.5 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.1 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Option		"DPMS"
	Option		"UseEdidDpi"	"FALSE"
	Option		"DPI"	"120 x 120"
	##	see if removing this stops the weird movig edge of screen thing
EndSection

Section "Device"
	
	##	Screen	0
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	Boardname	"nv"
EndSection

Section "Screen"
	
	# Allow VNC access to this screen
	####	Option		"SecurityTypes"	"VncAuth"
	####	Option		"UserPasswdVerifier"	"VncAuth"
	####	Option		"PasswordFile"	"/root/.vnc/passwd"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"BenQ W100"
	Defaultdepth	24
	Option		"UseEDID"	"False"
	Option		"FlatPanelProperties"	"Scaling = native"
	Option		"ExactModeTimingsDVI"	"true"
	Option		"ModeValidation"	"NoDFPNativeResolutionCheck, AllowNon60HzDFPModes, NoEdidMaxPClkCheck, NoMaxPClkCheck, NoHorizSyncCheck, NoVertRefreshCheck, NoEdidDFPMaxSizeCheck, NoEdidModes"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	# Disable modeline validating as much as possible
	####		Option		"AddARGBGLXVisuals"	"True"		Not sure where this came from, why it was there, or why it got removed
	SubSection "Display"
		
		##		Virtual	1920	1200
		Depth	24
		Modes		"1280x720@50"	"1280x800@60"	"1280x768@75"	"1440x900@75"	"1280x800@75"	"1440x900@60"	"1280x720@60"	"1600x1024@60"	"1280x768@60"	"1680x1050@60"	"1280x854"	"1680x1050@75"	"1152x768@54"	"1920x1200@60"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"720x400@85"	"640x350@85"	"640x400@85"
	EndSubSection
EndSection

Section "Extensions"
EndSection

---

### Post by slumcat05 on 2008-05-03
I have the same problem, although I have an older and much crappier monitor, and slightly crappier video card.

Anyway, I've tried everything to get the Nvidia drivers (including Envy), and I've done everything I can think of to the xorg.conf, but I'm still stuck in 600x800 hell.

---

### Post by bobnutfield on 2008-05-03
Did you do an upgrade via Synaptic or a fresh install?  Many are having this problem doing an upgrade rather than a fresh install because Hardy is using the original menu.lst from Grub and booting the Gutsy 2.6.22-14 kernel with Hardy and the kernel-dedicated drivers bork it.

Sorry for the question if you have already considered something like this.  If not, type:

uname -a 

and check which kernel you are running.

Bob

---

### Post by slumcat05 on 2008-05-03
Bob:

I don't know about the original poster, but uname tells me I'm running  2.6.24-16-386.

EDIT: Whatever updates I recently installed seems to have fixed the problem, and after going to **System > Preferences > Screen Resolution** I now have a whole list of resolutions where before I had only two.

---

### Post by Daminator on 2008-05-06
I seem to be running the correct version

---

