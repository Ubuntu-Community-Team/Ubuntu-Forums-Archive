---
title: "Black screen problem with nvida geforce4 440 go"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by rav3 on 2008-03-25
ok, i decided to give ubuntu YET another chance to bring me over, however the inability to install drivers for my nvida geforce4 440 go. 

if i get the old nvidia drivers, im totally unable to get them working, i just keep getting told i dont have permission even when i use su, or sudo

and when i use the restricted drivers manager, it tells me it succeded, and i should restart, but when i restart i just get a black screen.

WHAT am i doing wrong?

please im desperate and i really want to see if this thing is good for me.

on a side note, is my video card good enough to see all the eye candy in this thing?

and last what is all the eye candy/?

thanks in advance

---

### Post by CrimsoniteX on 2008-03-25
First, I'm kind of new, but I think you should be using sudo over su.

Anyway, How long did you wait for that blank screen after it restarted? It is a fairly common problem with ubuntu that has a fix. When you restart, leave it go for up to ten minutes (mine only took about 2), if you still get nothing then we need to find you better drivers. But if you get to the log in screen, follow these instructions:

[QUOTE=orange2k]
I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u[/QUOTE]

If it is your drivers, try the first section of this guide:
[http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200)

As far as eye candy goes, I can run every kind with a Radeon 7500 Mobility (32 mb) on my old Thinkpad t42, so maybe that will put it into perspective.

---

### Post by FerN(SA) on 2008-03-25
Hey,  I had a similar problem to yours.  I have a nvidia geforce 4 Ti, but i could install the glx driver fine.  But the problem came in when I wanted to upgrade, then I also got the black screen.  I just reinstalled everything, but I think it should be possible to re-install your old drivers.  It should go something like this:  When you get your black screen type Ctrl+Alt+F1 then log into your machine.  Then sudo apt-get remove nvidia-glx.  Then sudo apt-get install nvidia (or is it nvidia-legacy?).  Then you should atleast be able to see stuff again.  Then you could try to install the drivers again atleast.  There are some effects that I cant see like the raining effect or something like that but that is all fine with me.  Sorry that I couldn't help more

---

### Post by forestpixie on 2008-03-25
I have a GeForce4 MX 440 with AGP8X - it runs the eye-candy, or could if I wanted it to do so. Have you tried to use envy to install with
 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

you do need to reinstall after kernel upgrades though I think.

---

### Post by rav3 on 2008-03-25
thanks for the suggestions, ill let you know if they work

---

### Post by Lord Illidan on 2008-03-25
I edited the thread title as the old one was obviously sensationalist.

---

### Post by rav3 on 2008-03-25
im a designer i cant help it :P

and hey it got me answers!

---

### Post by rav3 on 2008-03-26
Arghhh! i got the blue screen again.

I used envy, it said it was all right and if i wanted to restart

i did, then waited for 30 mins in a black screen before i gave up and then decided to post this.

any ideas?

---

### Post by forestpixie on 2008-03-26
This might work and again it might not - I had a problem at first with gutsy and getting the driver to work properly.

I ended up uninstalling all that I could find in synaptic related to nvidia and envy and starting again. Sounds worse than it is.

If you want to try you need to do these in this order, boot to recovery mode - run the first command and choose vesa as the graphic driver

```
sudo dpkg-reconfigure xserver-xorg -phigh
```then 
```
reboot
``` I think that works :)

You should hopefully get into buntu with pretty awful graphics meaning that none of the nvidia stuff is working - at this point this is what we want. Don't choose the pick driver option if you get the application that trys to get graphics working.

Assuming you still have the envy driver installed - run envy and use it to uninstall the driver. If it prompts to restart x - do so, graphics will still be poor.

When you boot back in go to synaptic - search for nvidia - select all that are installed and mark for complete removal.

Reboot - you will still have poor graphics.

At this point you can try 2 things - run envy and let it install and see if it works - if not boot back in to recovery and run dpkg-reconfigure command again.

Or go for restricted driver manager installation, which I ended up doing - you will likely be told it can't run because something is missing, install that package first - I can't remember which one though - could be linux blah blah restricted manager something or other :)

Then run restricted driver again and use it to install the driver, then restart x.

Hope that is of some help - long list but not that painful really. Good luck.

---

### Post by rav3 on 2008-03-26
what is synaptic?

im seriously ubuntu illiterate

---

### Post by rav3 on 2008-03-26
ok found synaptic

and second of all i tried everything you mentioned and still black screen

---

### Post by forestpixie on 2008-03-27
Ok - did you have a black screen when you were using the vesa driver or just with nvidia drivers ?

---

### Post by rav3 on 2008-03-27
with the nvidia drivers, when i use vesa drivers i have no problems

---

### Post by forestpixie on 2008-03-27
Beyond me I'm afraid then - I know that others have had this card working, there are a good few threads on this card.  

Might try a thread in the multimedia/video forum - sorry I can't be of more help.

[http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by rav3 on 2008-03-27
no worries you did all you could

its back to windows for me then 

thanks for all the help i really appreciate it

---

### Post by forestpixie on 2008-03-27
One last thing - maybe have a go with hardy - it worked with my 440 with AGP much easier than it did with gutsy, just a thought. ANyway - good luck

---

### Post by rav3 on 2008-03-28
was that the previous version of ubuntu?

---

### Post by forestpixie on 2008-03-28
no the new beta, but saying that feisty which was the previous versnio didn't have the problemes that gustsy did for me..

hardy is here - [http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)
feisty is here - [http://releases.ubuntu.com/releases/](http://releases.ubuntu.com/releases/)

---

### Post by jecker on 2008-04-09
Please post this log file /var/log/Xorg.0.log.

---

### Post by rav3 on 2008-04-09
ok ill try to find it

---

### Post by jecker on 2008-04-10
What type of computer is this? If it is a laptop, chances are the driver is interpeting the display device incorrectly. I had the same problem and I was able to fix it by adding a line in the xorg.conf defining the display device as a "DFP".

---

### Post by mikesbo on 2008-07-02
Has anyone found an answer to this blank screen issue?  I have a Dell C840, and see the same thing, regardless of Ubuntu version, when using the nvidia driver.

Even with the "nv" driver, I still have problems with this machine waking from sleep/suspend: the display is there, but not re-lit.

---

### Post by mikesbo on 2008-07-02
OK, I did some more searching and found this hint.  It seems the card is trying to use an external monitor by default and the "UseDisplayDevice" option forces it to use the LCD.

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	        "True"
	Option		"UseDisplayDevice"	"DFP-0"
	Option		"DynamicTwinView"	"false"
EndSection

---

### Post by upchucky on 2008-07-02
Just so everyone knows, in his earlier post he stated that envy said that the driver was installed, at this point it was, however what needed to be done from there was to manually edit the xorg file and enter the screen and resolutions. this is stated on the last few lines of the install completion notice.

every time i have had the envy install say it was successful, it either worked on a reboot, or the file had to be edited.

look at the following xorg file, i have entered several mode settings to fall back on if a setting does not work right off the bat.

this is a xorg i use to test different flavors of Linux, do not use it but just compare settings for your screen and edit your xorg as needed.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
	Load		"glx"
	Load		"v4l"
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
	Option		"Protocol"	"ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
#	Horizsync	31.5	-	64.0
#	Vertrefresh	56.0	-	65.0
	Gamma	1
######added from working xorg file on usb drive#####
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
######end of addition###################
#  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
#  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
#  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
#  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
	# 
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
######added from my old working bery conf########
        Option          "UseFBDev"              "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "backingstore"          "true"
        Option          "AddARGBGLXVisuals"     "true"
        Option          "TripleBuffer"          "true"
######end of addition#####
	Screen	0
EndSection

Section "Device"
	# 
	Identifier	"device1"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
######added from my old working bery conf########
        Option          "UseFBDev"              "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "backingstore"          "true"
        Option          "AddARGBGLXVisuals"     "true"
        Option          "TripleBuffer"          "true"
######end of addition#####
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
#		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
                Modes      "1920x1200" "1024x678" "960x600" "840x600" "1280x960" "800x600"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
	# 
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

#######added from my working beryl conf########
Section "DRI"
        Mode    0666
EndSection
##########end of addition########
```

---

### Post by rav3 on 2008-07-02
.... ok thats it i give up on ubuntu

---

### Post by DarinB on 2008-07-02
don't give up i have the same geforce4 440 
it does work out of the box with Hardy.
with feisty i used the included common nvidia driver. and had to add and remove the restricted drivers then reboot and all was fine again.
and never add the restricted drivers or reboot after an update > i would first add and remove the restricted drivers ignore the reboot and then reboot after the add then remove....
some up dates adds them or pieces of the restricted drivers
and the legacy drivers were a disaster avoid it. 
and it should work fine 
geforce4 440 is a strange beast but with hardy it works with no additions. 
i have been on a clean install of hardy since release no issues even after
updates.

---

### Post by helloWorld2 on 2008-07-08
I just installed ubuntu today on INSPIRON 8200 with geforce4 440 go, this was the only extra configuration that was needed to be done after the nvidia-glx drivers were installed. Thanks mikesbo

> **mikesbo said:**
> OK, I did some more searching and found this hint.  It seems the card is trying to use an external monitor by default and the "UseDisplayDevice" option forces it to use the LCD.

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	        "True"
	Option		"UseDisplayDevice"	"DFP-0"
	Option		"DynamicTwinView"	"false"
EndSection

---

### Post by joexs on 2008-07-11
About the just prior post from helloWorld2.  When I try to add those lines to the xorg.conf file, it says I don't have permissions.  How can I get around this problem?

---

### Post by joexs on 2008-07-12
Never mind.  I'm definitely glad I made the switch to Linux, but it's tough teaching an old dog new tricks.

---

