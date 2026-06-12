---
title: "Screen issues after update to gusty"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by teddydov on 2007-10-19
Hello All, 
Just finished updating my Laptop from 7.04 to 7.10. As far as I could tell the update went fine no special events. 
When my computer restarted the screen has lines running across it in such a way that I can't really see anything. Everything seems to be working ok other than that. 
I am able to see enough to log in and find some basic buttons on the screen and I can recognize my desktop from the icons, but everything looks blurry for lack of a better word. This includes my login page, desktop and my screen saver. 

Please Help - I have been using Ubuntu for about a year now and this is the first time I have any real issues. 

My laptop is an HP (ze5500) the Card is an ATI (don't ask me exactly which one). 

Any help/ suggestions would be most appreciated.

Thanks, 
-Dov

---

### Post by enchesss on 2007-10-19
Have you tried to install the ATI restricted drivers in the manager? Sytem -> Administration -> Restricted Drivers Manager. - REBOOT - 

There are some instructions about reconfiguring xorg if this goes wrong too.

Boot to command line and :- sudo dpkg- reconfigure xserver-xorg

It should be the same for all types of ATI cards if there is a method to this madness.

---

### Post by teddydov on 2007-10-19
ok tried both - 
the restricted manager doesn't give me any option for ATI (just my wrieless card)

I have tried to recofigure xserver-xorg and it didn't help 

any way to figure out what the problem is?? any way to install my ATI drivers from scratch?

---

### Post by teddydov on 2007-10-19
ok more info:
it seems that there are more issues - 
My computer wont start the X now and goes to the terminal asking me to log-in from there. 
I can get the it to start by typing Startx but then I am back to my former issue!
also when I am in the terminal I can't seem to get the fglxinfo to run it tells me that command was not found! what's going on??

I want to know if there is any way to revert back to the settings I had before I updated? If not - since I seem to be having more and more issues with this - if there is any way to do a clean install without formatting my HD?? 
once again I know a bit about linux now but I am somewhat of a Noobie when it comes to fixing things when they go wrong (doesn't happen very often I am glad to say). 

once again any help advice ETC.

---

### Post by Original Brownster on 2007-10-19
Hi,
I don't think there is an easy way to go back to the old version however I am fairly confident (famous last words) that you should be able to unpickle this. 
I am guessing from what has happened that Gutsy has changed your video driver (fairly likely) but we need a bit more info.

let's find what video card you have, at a terminal type 
lspci -vv

scroll through all the lines and look for the mention of your ati card and find the model out. 

We can find out what driver was being used prior to the upgrade by looking back at the logs for xorg. then we can compare to what is currently trying to be used.

ls -l /var/log/X*

will list the log files for xorg, Xorg.0.log is your current log, look inside it to find what graphics driver was attempted to load, if it's an ati card it'll likely be the fglrx driver.

less /var/log/Xorg.0.log | grep "fglrx" if it returns lines with this entry you know it tried to use it.

look at an old log and see if it was using fglrx, the other option would be to use the ATI driver.

post back with more info and we can see what's happening

---

### Post by coolglobal on 2007-10-20
Hello, I have exactly the same issue - blurry icons. This what came from the terminal:

:~$ ls -l /var/log/X*
-rw-r--r-- 1 root root 52067 2007-10-20 21:23 /var/log/Xorg.0.log
-rw-r--r-- 1 root root 52165 2007-10-20 19:43 /var/log/Xorg.0.log.old
-rw-r--r-- 1 root root 51753 2007-08-01 13:35 /var/log/Xorg.20.log

---

### Post by Original Brownster on 2007-10-20
> **coolglobal said:**
> Hello, I have exactly the same issue - blurry icons. This what came from the terminal:

:~$ ls -l /var/log/X*
-rw-r--r-- 1 root root 52067 2007-10-20 21:23 /var/log/Xorg.0.log
-rw-r--r-- 1 root root 52165 2007-10-20 19:43 /var/log/Xorg.0.log.old
-rw-r--r-- 1 root root 51753 2007-08-01 13:35 /var/log/Xorg.20.log


Have you upgraded from Fiesty to Gutsy also? If so which graphics card do you have?
look in the current Xorg.0.log and look for a line saying something like 'loading module {name of graphics driver here like fglrx for example} 
you can look at the file with the command:
less /var/log/Xorg.0.log

look in an older log file prior to the update and see what driver was being loaded and see if a different one is now being used. 

HTH

---

### Post by norway1978 on 2007-10-20
Same problem for me also. I've got a HP compaq nx9010.

**lspci -v =** 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M (prog-if 00 [VGA])

**lspci -b =** 
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface



I tried to look in the Xorg.log files, but I was not sure what to look for....

**Xorg.0.log**
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
..
..
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2


**Xorg.20.log**
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
...
...
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1

---

### Post by Original Brownster on 2007-10-20
From what you have posted it seems you have a radeon igp345m graphics card, at least that's what one spec for that laptop I found seems to confirm do you know if this is correct?

You can see from the output that both xorg and the ati driver are newer versions in gutsy.
I suspect the issue is due to this introducing a bug. I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/133192") which seems what the problem is for you at least.

Have you upgraded from Fiesty to gutsy?

I'm trying to see if you could try the fglrx propriety drivers instead but it appears that they may not work, you could try enabling them by launching the  Restricted Drivers Manager and seeing if it lists the ATI driver in there, if it does you could try selecting this and restarting the xserver (ctrl backspace always does it)

HTH

---

### Post by shouravv on 2007-10-20
I had this same problem, this is caused by too high default refresh rate set by Gutsy that is not fully compatible with your monitor / VGA card / driver.

I solved it by replacing the new xorg.conf file with the old auto backup one.

First, do a ls on /etc/X11/xorg.*

Second, back up your current xorg.conf

Third, replace the current xorg.conf with an older version, preferably with the xorg.conf.original one.

For me, it worked like this:

{{{

bob@bob:~$ ls /etc/X11/xorg*

/etc/X11/xorg.conf                 /etc/X11/xorg.conf.20061201143855  /etc/X11/xorg.conf.failsafe      /etc/X11/xorg_config_back
/etc/X11/xorg.conf.1               /etc/X11/xorg.conf.20061201232715  /etc/X11/xorg.conf.failsafe.bak  /etc/X11/xorg.conf.original-0
/etc/X11/xorg.conf.20061027062407  /etc/X11/xorg.conf.20071019        /etc/X11/xorg.conf.fglrx-0


bob@bob:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-latest

bob@bob:~$ sudo cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf

}}}

Now reboot the machine. If something goes and you can't get GUI, you can restore the backup you just made, or try other automatic backup the system made earlier.

Note: The other solution might be to edit xorg.conf by hand editing the refresh rate. My montior's manufacturer suggested rates are 42-72 Hz, whereas Gutsy set it at 75. I prefer having it at 60.

---

### Post by johncarl81 on 2007-10-20
Im having the same problem with my ATI 345M Radeon IGP video card.  Thing is, it worked just fine before my upgrade of ubuntu.  Also, ive tried the 'ati' and 'radeon' drivers, which allowed me to start X without 3D acceleration, and ive tried the 'fglrx' driver, which didnt allow X to run at all.  Let me know what you guys find out.

~John

---

### Post by norway1978 on 2007-10-20
Hi, 

Thank you for your quick replay. In the device manager it says:

PCI Bridge [IGP340M]
   Radeon IGP 330M/340M/350M

I've upgraded from Fiesty to Gutsy.(did it today actually). My Fiesty worked perfectly.
I tried to launce the Restricted Drivers Manager, but I only got the message: "Your hardware does not need any restricted drivers"

Any ideas?

---

### Post by teddydov on 2007-10-20
ok - from what I can see (blurry screen and all) my Card is also the 345M (seems to be the source of all Evil :). 

when I try to use an older version from out of the X platform (so I can see normally) I am unable to change the names of Xorg files. so I am a little stuck there. 

Is there any way to uninstall the drivers and try to install them from scratch since it keeps telling me my system is up to date (just most likely with the wrong drivers).

I hate to say - but I am glad to see this isn't something I did.. (Sorry, but misery loves company). 

-Dov

---

### Post by fishtoprecords on 2007-10-20
> **enchesss said:**
> 
Boot to command line and :- sudo dpkg- reconfigure xserver-xorg

.

Same kinds of problems with my Thinkpad T60p
with ATI.

Do you have a typo or two in that shell command?
Is the switch really trailing on the dpkg?
or is it more like
 dpkg  -reconfigure xserver-xorg

---

### Post by fishtoprecords on 2007-10-20
My feisty setup was great. Since I've upgraded to gusty the video is slow and ugly.
Some icons, such as the lower left "hide window" and the upper right sound icon are just wavy dots.

Screen redraws are terribly slow.

In a shell window, the current cursor is some sort of blinking graph checkerboard that is very hard to read.

In many windows, simple lines of text are distorted past visibility.

This is a Thinkpad t60p with dual 2ghz CPUs, a discrete ATI card: M56GL [Mobility FireGL V5250] and two GB of ram. 

 Its running more P120.

It says its runing the ATI restricted drivers. When I did the install, it whined about Gnome and X not agreeing on the video drivers. But if went by before I could understand what it was wining about.

The driver seems to be 'fglrx'

Even switching between windows using alt-tab is painfully slow.

---

### Post by teddydov on 2007-10-20
ok something to update - 

I downloaded a copy of Gusy and burnt it onto a CD. Tried to run it and got the same results, Blurry screen filled with lines. 

I then decided to put my old 6.10 Version I still have on CD from the first time Installed Ubuntu - and all seems fine now.. 

Now come the big questions!! What was changed in regards to this card (the ATI 345M) that makes it screw up on Gusy. 

Is it worth trying to down grade back to 6.10 (then upgrade back to 7.04) for now (is that even possible without loosing all my info??) or is there some simple fix I can take from the  6.10 CD and just put it into Gusy and make it work???

Thanks for the help so far. 

-Dov

---

### Post by teddydov on 2007-10-20
Ok last post and then it's time to go to sleep (it's 4:15 in the morning) 

so I have good news. 
After loading the Gusty Cd up again I selected Safe graphics mode. That seemed to work - so using the Xorg.conf from that I copied it over to my computer and so far so good (one problem sort of solved). The solution seems to be at this time (at least until we can find a better one) to use Vesa as the option - if you can see enough of your screen you should be able to find it in System-> Admin.-> Screens and Graphics -> graphic cards -> in the Driver there is an option for Vesa see if that works for you at least to get your computer working again... 

good night all :)

---

### Post by Original Brownster on 2007-10-21
Yes the vesa mode should work whatever and at least that is usable.

It might be worth checking your xorg.conf file and seeing if disabling 'Composite' helps.
It will most likely been enabled on the upgrade to gutsy. 
Post the output of your xorg.conf file and something might be obvious (even better compare an old version to the current one)

$ cat /etc/X11/xorg.conf

---

### Post by teddydov on 2007-10-21
This is my current (working) xorg.conf


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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

It is basically the one that was created by the CD when i used safe graphics. 

The good news is that I can see my screen again (and I don't feel nauseous every time I load the X). On the other hand - there must be a better solution for this - I know that my card was working before and I was even able to at one point or another use Beryl (I stopped it because at the time it was crashing - not Video related - stability related). 

So I know my card should run all sorts of fun things but now everything is really slow graphics wise. (I can see a huge difference on my screen saver).

---

### Post by Whateverist on 2007-10-21
I'd just like to say that I've got the same problem - IGP340M, an unreadably blurred screen (strangely enough, only at 1024x768 ) and switching to vesa or a lower resolution brings the screen back to normal. This started under 7.10.

Is this graphics adaptor no longer supported or something?

---

### Post by romana on 2007-10-21
ATI driver works fine on ATI Radeon IGP 330M/340M/350M card, but like everyone else, fglrx falls over, so no 3D. So, neverwinter nights, beryl, and anything else shiny is big fail. would love to hope there is a solution out there, but it seems like fglrx is broken for this type of card atm.

---

### Post by teddydov on 2007-10-21
> **romana said:**
> ATI driver works fine on ATI Radeon IGP 330M/340M/350M card, but like everyone else, fglrx falls over, so no 3D. So, neverwinter nights, beryl, and anything else shiny is big fail. would love to hope there is a solution out there, but it seems like fglrx is broken for this type of card atm.

how did you get your ATI driver to work?? If I try to change my driver to anything but VESA i get "ol' Fuzzy" again! 

well - I hope we have an answer since I would love to use all the new stuff in Gusty

---

### Post by romana on 2007-10-21
> **teddydov said:**
> how did you get your ATI driver to work?? If I try to change my driver to anything but VESA i get "ol' Fuzzy" again! 

well - I hope we have an answer since I would love to use all the new stuff in Gusty

posting my xorg.conf. it auto detects as ati using dpkg-reconfigure xserver.xorg. hth:)
(still no fglrx luck, despite googling like crazy for it. seems to be a noted bug though...)

___________________________________________________________________



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
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by romana on 2007-10-21
Found this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
It is the best unofficial Linux/ATI resource I found.

I did follow the guide, no success. BUT. I have increased the speed of glxgears. 
Following a suggestion on the page above, I decided to reinstall libgl1-mesa, since installing the fglrx driver to trial messed that up. Hmm, doesn't exist.

A quick sudo apt-cache search libgl1-mesa produced a nice list - I (re)installed libgl1-mesa-glx

sudo apt-get install --reinstall libgl1-mesa-glx

I also added to my xorg.conf, down the very end, 
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"

Following a suggestion on another site. I don't actually know if this makes a difference, and will try without it next boot:) (X worked fine without it before, its the game I am interested in).

Anyway, glxgears much happier, and neverwinter nights, while not speedy smooth, now playable. It will do for now. I don't know if this will help with compiz/beryl though.

---

### Post by teddydov on 2007-10-22
When I tried using ""ATI Technologies Inc Radeon IGP 330M/340M/350M""
and ATI driver - that is when I started having all my issues. I don't really get it and don't understand why that would happen unless they stopped supporting this card. 

Anyways.. Will try the install when I get home (at work now) and will see if my gears work any better (everything is REAL slow right now...)

---

### Post by mdev on 2007-10-23
If it's any consolation, this problem is not limited to Ubuntu.

I found the exact same problem with OpenSUSE 10.3 and the latest Frugalware, amongst others (and Xubuntu, which you would expect). The only thing they have in common is kernel 2.6.22.

Latest PCLinuxOS and Mint works with no problem, 3D desktop and all, but I notice they're both using earlier kernels.

Probably no relationship (unless most distros are still using the kernel IGP driver?). It irks me that all of these recently updated distros have ALL munted ATI IGP support and didn't beforehand. Holding off upgrades for now, but I want me some new shinies!! :lolflag:

---

### Post by mwero001 on 2007-10-24
Hi people,
I've been trying to install kubuntu gutsy gibbons dvd version in my computer. The process goes well until it comes to loading the window manager. When I use text mode, it installs well but upon rebooting, the window manager isn't loaded. I am using a generic monitor - Tangerine, which ha a frequency of 60hz. Never had this problem with dapper and feisty. I'd really appreciate any assitance.

---

### Post by hyliker on 2007-10-24
maybe you can try to install startupmanager to fix the usplash problem.

1.install startupmanger
$ sudo apt-ge install startupmanager
2.after finish installation. then you can change boot setting for usplash.
$ sudo startupmanager

try above you will fix some problem you meet.:)

---

### Post by kingkookie on 2007-10-27
I've posted a bug on this issue.  Note that you can blindly change the resolution to 800x600 despite the fuzzy screen, then you will get a nice clean display.  It also allows you to run desktop effects by default.  Whereas with Feisty, I couldn't get that working at all.

From what I have read, these new ati drivers are the problem.  ATI has open-sourced some of there drivers and I think that this is one of those drivers.  But, from a posted bug that I found on x.org, it seems as though the driver is taking control of the screen frequency, which is too high for many laptops.  No matter what frequency you place in xorg.conf, the driver ignores it and uses something else.  That explains why when you try to change frequencies from the Screen Resolution setting, you only get one option.

There is a patch available, but it's just source code and I have no idea how to implement it.  My experience is too limited.

Anyway, have a look at this bug report and checkout the follow-up post to find the link to the x.org bug report.  The patch is found on the x.org's bug report.  Hopefully with that information, we can get this problem fixed.

For now, I recommend just using the vesa driver if you desire a res of 1024x768.  Else, live in 800x600 world for a while, until the issue is resolved.

---

### Post by romana on 2007-10-31
> **kingkookie said:**
> I've posted a bug on this issue.  Note that you can blindly change the resolution to 800x600 despite the fuzzy screen, then you will get a nice clean display.  It also allows you to run desktop effects by default.  Whereas with Feisty, I couldn't get that working at all.

From what I have read, these new ati drivers are the problem.  ATI has open-sourced some of there drivers and I think that this is one of those drivers.  But, from a posted bug that I found on x.org, it seems as though the driver is taking control of the screen frequency, which is too high for many laptops.  No matter what frequency you place in xorg.conf, the driver ignores it and uses something else.  That explains why when you try to change frequencies from the Screen Resolution setting, you only get one option.

There is a patch available, but it's just source code and I have no idea how to implement it.  My experience is too limited.

Anyway, have a look at this bug report and checkout the follow-up post to find the link to the x.org bug report.  The patch is found on the x.org's bug report.  Hopefully with that information, we can get this problem fixed.

For now, I recommend just using the vesa driver if you desire a res of 1024x768.  Else, live in 800x600 world for a while, until the issue is resolved.


Actually, I can
1) use ATI driver and have 1024x768 with no issues
2) NOT use fglrx at all, the error message is : no screens found.

---

### Post by kingkookie on 2007-10-31
I tried your xorg.conf, but on my system, it just doesn't work.  My Laptop's LCD screen just goes "fuzzy" or out of sync.  The driver doesn't use the correct frequencies for my display. I've even specified the correct frequencies using modeline, but the driver ignores it and uses it's own.  Now, if I knew where to find where the driver stores it's own frequency settings, perhaps I can force it to use the right frequencies, but for now, I don't know how and so I am stuck with a generic VESA driver.

---

### Post by chenhsun on 2007-11-10
Hey guys I have a t60p and I just upgraded to gusty too, I think the problem is with the newest version of the Kernel.
I have vista/ubuntu dual boot so I get to choose which version I get to log into. If I go into the new one it's all messed up, the old kernel works fine. Hope this helps, cheers

---

### Post by Statik on 2007-12-13
Just installing Gutsy on a Compaq NZ9010 and I'm running into the same issue. Any solutions out there yet?

Statik

---

### Post by snacker on 2007-12-30
I am also having the same problem with the upgrade.
HP ze5500us : Radeon IGT 345M

I've attached pictures of the fuzzy screens.  This is from the iso put on cd and booted.  Note the screen is fuzzy and appears to be shifted to the left.

---

### Post by snacker on 2007-12-31
It looks like the problem I am having is the same as the one reported in:
     [INDENT]_[Bug 165326 - ... fuzzy screen...]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/165326")_[/INDENT]

In that bug activity _[Tormod]("https://bugs.launchpad.net/~tormodvolden")_ wrote 
[INDENT]Can you please try the newest version from _[https://wiki.ubuntu.com/XorgOnTheEdge]("https://wiki.ubuntu.com/XorgOnTheEdge")_ [/INDENT]

That page has a section titled "ati driver (a.k.a radeon)" which says a new ati version is available "xserver-xorg-video-ati_6.7.197-1ubuntu1~tormod"
 
Following the link _[https://launchpad.net/~tormodvolden/+archive]("https://launchpad.net/~tormodvolden/+archive")_ you find that the files are listed under _[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/")_

My question is :confused:[FONT="Arial Black"]how can I install this newer version?[/FONT]:confused:  The version I have is 1:6.7.19**[COLOR="Red"]5[/COLOR]**

I assume there is an apt-get command to do this, but "sudo apt-get install xserver-xorg-video-ati_6.7.197-1ubuntu1~tormod" didn't work.

Do I need to update the apt.conf before I can do this??

---

### Post by Statik on 2007-12-31
Snacker, the problem you screen-shotted is the exact problem I had on a laptop I rebuilt for my wife for Christmas. The solution that worked for me is the third post on page two here: [http://ubuntuforums.org/showthread.php?t=579596&page=2]("http://ubuntuforums.org/showthread.php?t=579596&page=2")

Hope it works for you too!

Statik

---

### Post by snacker on 2007-12-31
Thanks, Statik I will try that!

---

### Post by snacker on 2007-12-31
That worked!

I just replaced my xorg.conf with his and rebooted!

Thanks a lot!

---

### Post by kingkookie on 2008-01-29
It worked for me too.  Finally after all my failed tries, the solution has been found.  Thanks to wargames for posting the solution.  Here is a copy of his xorg.conf file:


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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "ati"
BusID "PCI:1:5:0"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Option "LVDSBiosNativeMode" "false"

EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by snacker on 2008-01-30
oops.

---

### Post by snacker on 2008-01-30
I installed "xserver-xorg-video-ati_6.7.197-1ubuntu1~tormod" (had to get other libraries installed as well), but it didn't work for me.
So I ended up having to unistall it.

The xorg.conf wargames posted worked for me, but OpenGL apps are fuzzy in fullscreen mode, so I can't use them still.

---

