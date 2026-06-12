---
title: "ati radeon x1600 and gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by piwi1999 on 2007-10-19
Hi, my ati radeon x1600 worked very good under 7.04 but when installing 7.10 from live cd  (which worked well....no errors reported)....when booting from grub....my computer hangs (only black screen - not possible to use ctrl+alt+backspace)...anybody knows how to help me? thanks in advance

---

### Post by jimerickso on 2007-10-19
my ati x1600 would only work after using the alternate cd to install. your mileage may vary.

---

### Post by Gutsy Vegan on 2007-10-19
My goal today after work is to get my x1600 to work on gutsy- If I'm successful, I'll let you know

---

### Post by Can+~ on 2007-10-19
black screen? Can you use Ctrl+Alt+F1/F2/F3.. to get to terminal?

---

### Post by Pumalite on 2007-10-19
If you get a command line maybe you can try this:

Re: Feisty and Gutsy not working with ATI X1400
This is a solution from [http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/](http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/)
and I listed it on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.04 should now boot into GDM/KDM.

---

### Post by MrKirby on 2007-10-20
I also had my Radeon X1600 Pro working fairly well under 7.04 with beryl and 3-d effects, but I'm still struggling to get anything working to my satisfaction under gutsy. It's kind-of disappointing.

I had no problem installing gutsy, but my card is once again running under the vesa driver with no 3-d support.

I've tried installing the proprietary driver from the restricted drivers manager, only to find a blank screen on restart, and also tried installing the ATI drivers from their website on a fresh install, as apparently somebody with an X1650 got that to work with no problem (can't imagine it was too different, but oh, well).

Each different thing I've tried so far seems to revert to the vesa driver, despite my settings, due to an apparent fail-safe mode.

I, too will continue to try to get this to work and will post if I do, but I'm kind-of tired of it now.  I wonder if I should just install all of the exact same graphics drivers, software, and configuration files I had in feisty?  Would that screw it all up? :confused:

---

### Post by GSF on 2007-10-20
hello, my ati x1600 pro (agp) works great with the restricted drivers and never had black/orange screens... only some problems with desktop effects that hopefully will be solved..

---

### Post by MrKirby on 2007-10-21
ok, so that last post made me second-guess myself and think I was just crazy or something, so I figured maybe I was just messing with it too much at the time and messed it up, so I went and enabled the restricted driver (after fresh install),didn't modify or affect anything, rebooted, and after Ubuntu loaded, the screen flashed and lots of crazy scans went across the screen for a little while, then blank screen again.  I never got the login screen, or even the sound for the login prompt, so it's safe to say it pretty much halted there.  I was also unable to bring up any sort of prompt where I could go in and modify anything.

Am I just stupid and forgetting to do something here, or what?

BTW, I noticed most of the people posting that they got their X1600 to work are ATI mobility users (laptops).  If you did something special to get your desktop PCI X1600 Pro to work, please post.  Here is the xorg.conf that I ended up with after the install of the fglrx drivers:

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
	Identifier	"Generic Video Card"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"COMPAQ &#65533;&#65533;00"
	Vendorname	"Compaq"
	Modelname	"Compaq S900 Color Monitor"
	Horizsync	30.0-95.0
	Vertrefresh	50.0-160.0
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
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"COMPAQ &#65533;&#65533;00"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1280x1024@85"	"1280x1024@60"	"1280x960@85"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@43"	"1600x1200@60"	"1024x768@60"	"1600x1200@75"	"1024x768@70"	"1600x1200@70"	"1024x768@75"	"1792x1344@60"	"1024x768@85"	"1856x1392@60"	"832x624@75"	"1920x1440@60"	"800x600@60"	"2048x1536@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection




It appears the only thing changed was the driver identifier and the addition of Composite "0".  My hardware just doesn't like that driver, apparently.  Anybody got any ideas, other than sit around and use the vesa driver forever?

If you have a radeon X1600 working, and your xorg.conf is different than this, please post.

---

### Post by MrKirby on 2007-10-21
Correction:  I have an AGP, not PCI.  Apparently I'm as confused as the computer is.

---

### Post by sensibletech on 2007-10-22
Is there anyone that could help me I have PCIE Radeon x1650 with dual monitors. I can't seem to get the thing configured right. I've tried all the drivers and manual configuration but all I seem to do is break it.

---

### Post by Gutsy Vegan on 2007-10-22
I've had no success so far.... still trying.

---

### Post by jthirt on 2007-10-22
I experience the same symptoms with a Dell laptop with an ATI Mobility radeon 9000.

I'm not sure what to do now as I tried to change the driver to 'ati' instead of 'radeon' but it made no difference. Now, I'm not expert so maybe it needs more than just a change in xorg.conf

I successfully booted on the live CD prior to running the upgrade, so I assumed it would be fine from that point of view. Sadly, I was wrong !!!

---

### Post by icarlos on 2007-10-22
I have the same problem, but i don't have an x1600, mine is an x300. If i install restricted driver, screen gets black and nothing happens with crtl+alt+f2,f1,etc.

---

### Post by Marinodimare on 2007-10-22
I think I have a x1600 pro pci card, I'll check tonight and post the xorg.conf.

---

### Post by Marinodimare on 2007-10-22
> **MrKirby said:**
> I also had my Radeon X1600 Pro working fairly well under 7.04 with beryl and 3-d effects, but I'm still struggling to get anything working to my satisfaction under gutsy. It's kind-of disappointing.

I had no problem installing gutsy, but my card is once again running under the vesa driver with no 3-d support.

I've tried installing the proprietary driver from the restricted drivers manager, only to find a blank screen on restart, and also tried installing the ATI drivers from their website on a fresh install, as apparently somebody with an X1650 got that to work with no problem (can't imagine it was too different, but oh, well).

Each different thing I've tried so far seems to revert to the vesa driver, despite my settings, due to an apparent fail-safe mode.

I, too will continue to try to get this to work and will post if I do, but I'm kind-of tired of it now.  I wonder if I should just install all of the exact same graphics drivers, software, and configuration files I had in feisty?  Would that screw it all up? :confused:

Hi, could you tell me how you got Beryl and 3d effects working?

---

### Post by Marinodimare on 2007-10-22
Also, does anybody know how to enable transparency in Kubuntu? When I do it, by simply enabling 'composite' in xorg.conf, I get weired effects such as windows with only borders but no 'filling', and when in e.g. a wizzard, the first screen remains visible as you go to the next. Completely unworkable, as you may imagine. Btw I have the fglrx driver.

---

### Post by MrKirby on 2007-10-23
Ok, so I got so sick of it, I took out my Radeon X1600 and replaced it with my old nvidia GeForce4 MX 440.  Installed it all without a problem, and now I have all of the interface enhancements that I wanted, and they all run fine.  Maybe someday ATI will see the value in more support for linux, and I can install my faster graphics card, but until then, I submit.

I find it a bad impression of ATI's support for linux, and I may actually sell my ATI card and buy a new nvidia one.  It does, however, make me uneasy to see how many other people have had so much trouble with ATI cards in linux.  It would be good to have at least a little competition between the companies for linux.

My interface now runs better without any problems, in contrast to when I had my X1600 running in feisty! (which took a good amount of playing around, relying on online tutorials and several different installs).  I have the nvidia settings panel, and a good picture.

If anybody in ATI is reading this:

I probably won't buy another ATI card, as I plan to use linux in the future, for fear that if it becomes even slightly obsolete, I would either have to upgrade my card right away to within the sliver of your support spectrum, or change my hardware again---unless ATI provides a little more driver and software support to compete with nvidia.  I don't imagine I'm alone on this one.



BTW: to install my nvidia, I didn't mess around and just installed the drivers with Envy.  I then enabled the restricted driver afterwards to enable the extra effects.

My issue is solved.

---

### Post by MrKirby on 2007-10-23
As for how I got my x1600 working in feisty with beryl, I can't really remember how I did it, but I posted it in a couple of threads out there somewhere.  Strangely, I can't seem to find them anymore!  I tried so many things, it wasn't funny.  I DO remember, however, that I kept messing it all up by trying to enable desktop effects, not understanding at the time that that had nothing to do with beryl's desktop effects. I thought it was all integrated somehow.  So don't touch it, just leave it off.  After installing the fglrx, I THINK, drivers, I had to add a couple of things to the xorg.conf, like composite = "0" and SOMETHING 666.  I found it all in tutorials, and mixed and matched different methods.  You also have to make sure to create an xgl session, and login with that, and also add an emerald and beryl launch to the sessions menu as well, so make sure it started at boot. Believe it or not, that's what took me the longest time to figure out. I saw the beryl icon in my title bar, and just assumed it was all running.  It wasn't. Without emerald running, you don't get title bars or anything.  If I find the one tutorial that was particularly helpful, I will post it.

What's weird is that I can't find those threads anymore, and I can't find any of the other threads where other people got it working.  Why is that?  Hmmm....

---

### Post by MrKirby on 2007-10-23
found my old xorg.conf:

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ S900"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"COMPAQ S900"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by Ant_Merlin on 2007-10-23
Hi, I have an ATI X1650 AGP card. I think I have it working ok now in Gutsy however have had a major headache getting there. 

After looking through the forums as to how other people managed this is what I did:

Clean Install of Gutsy using alternative CD as "Live CD" wouldnt boot.

go to restricted drivers and tick use. This then installs FGLRX driver.

when I rebooted it went to "low graphics" mode.
went to screens and graphics, selected every driver on there at least twice before settling on Fglrx and changing the box at the bottom from "open source" to "proprietry Driver".

I know this driver works as I tested with 3d games, compiz, and Wine etc, however whenever I rebooted it went back to "low graphics" mode.

Very frustrating considering I always used Geforce until 6 months ago when my last one died on me.

Anyway I then went to /etc/X11/ folder and saw 6 xorg.conf.1-6 files and 6 xorg.conf.failsafe files in there. I deleted all but the present one (xorg.conf) and rebooted. I have rebooted about 10 times since and so far so good....

however I am getting strange problems, like font sizes changing after reboot, wifi settings not saving etc. I think it has something to do with the way Gutsy is saving information when it shutsdown?

anyway if this helps anyone all the better, if not at least i got that off me chest.

---

### Post by tnaseem on 2007-10-23
I'm glad I'm not the only one having problems. I posted about mine [here]("http://ubuntuforums.org/showthread.php?t=579881").

Mine's an X1950 with Samsung 226BW Monitor. I just can't get any of my settings to stick. Keeps going back to the failsafe. Tried everything to get this working o no avail.

@Ant_Merlin: I've tried your suggestion but doesn't work in my case. I also tried removing the 'allow-failsafe' option in the Xsession.option file as someone else suggested, but that doesn't work either.

I never had any problems under Feisty. All I had to do there was to enable the restricted drivers and set the resolution. All worked fine! Something's gotten broke in this new version. :(

If anyone gets to the bottom of this, please post your findings here!

Cheers,
Taz

---

### Post by Ant_Merlin on 2007-10-23
> I just can't get any of my settings to stick. Keeps going back to the failsafe

In my opinion its gotta be the way Gutsy is closing, when i log out and log in as same or different user it works fine, its only when you turn off or reboot that it goes back to low res. which to me means that Gutsy isnt saving the info right when it closes. anybody any further ideas, anybody logged as an error?

---

### Post by tnaseem on 2007-10-23
> **Ant_Merlin said:**
> In my opinion its gotta be the way Gutsy is closing, when i log out and log in as same or different user it works fine, its only when you turn off or reboot that it goes back to low res. which to me means that Gutsy isnt saving the info right when it closes. anybody any further ideas, anybody logged as an error?

I see what you mean. 

Actually in my case, I can never actually get it to set itself to 1680x1050, even before a reboot. I'm always stuck in 640x480. :(

Also, if I change the monitor settings to 'Samsung Syncmaster 226BW (digital), which is my model, and then set the resolution, the whole screen goes garbled, as if the monitor refresh rate isn't set properly.

If I make any changes and hit 'Test' it drops out to the console (no gfx) and eventually comes back to the login prompt. This is driving me nuts!

I've even contemplated buying an NVidia card to replace the ATI one. But that would be defeatist, not to mention an expensive proposition! :)

---

### Post by a2597 on 2007-10-23
I'm in a simular situation with my PCIX x1950...

useing vesa it comes up. Detects that it needs proprietary driver, that goes through fine...then it reboots, brings up a black screen that I honestly can't read all of because it's so quick, something about cfg/rc.local though, then login window loads fine. I enter info, then back to that black screen that says something about cfg/rc.local, repeat ad infinium...can't get into the GUI past the login. 

*sigh*

oh, and manually changing xorg.conf doesn't help...whatever that black screen is doing it's rewriting the xorg file.

---

### Post by margaf77 on 2007-10-23
I had the same issue after I upgraded to gutsy, I have an X1900 AIW, I did a hard reset and it started up fine after. Im assuming you probably did this already but try it if not. 

Also if you can get to the command prompt try installing the ATI drivers from there.

---

### Post by Ant_Merlin on 2007-10-23
Ok, so get home this evening and computer running fine!!!, seems to be behaving itself, compiz running ok. Very strange, even little issues I had are gone (fonts resizing, Icons changing).

So fingers crossed maybe its gonna be ok. Or maybe tomorrow it will be back to messing up the display, who knows.

I have read on another post that one guy got ATI X1900 working by installing ATI drivers from the ATI website as apparently better compatibility with Xorg 7.2. Still think its how gutsy is closing down though.

---

### Post by Mariano Oliveto on 2007-10-23
I have an ATI Radeon x1600 Pro AGP 8x 256 MB. I did a fresh install of Gusty a few days ago and I must say I had no problems... Live CD worked just fine and the installation went smoothly, so I'm not sure if this will help anyone.

When I enabled the restricted drivers using the "System -> Administration -> Restricted Drivers Manager" feature, 3D acceleration didn't work very well. E.g.: Skyrocket Screensaver was VERY choppy and all my videos (avi, wmv, mpg, you name it) had a blueish tone. I think also Penguin Racer (which worked OK) had this blueish tone. (All these problems I also had on Feisty)

Since I was using Debian Etch and got my x1600 Pro working I figured I could use the same installation method.

I followed this intructions:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Choosing Gusty this time ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide))

I used Method 2 for installing (reffer to the guide), in other words, I used ATI's driver installer. 

It didn't work for me just yet. I got the following output:

$ fglrxinfo 
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

So I checked the Troubleshooting page ([http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)) and followed the rest of the instructions. They did the trick, Sryrocket screensaver is OK and my videos play normally (no more blue aliens :) )

I don't know if this'll be of any help. I hope it will though.

By the way, wouldn't it make sense for us, ATI users, to ask ATI for better Linux support?? I saw somewhere that there was a request for ATI support for a specific family of ATI's GPUs but I think that it was one that had no driver installer whatsoever. 

Any suggestions??

---

### Post by orthorim on 2007-10-24
I have an ATI X1600 Mobility (Acer TravelMate 8204 laptop here).

The drivers seem to be working now, but I was a bit disappointed that it didn't work as well as in Feisty - in Feisty, the system detected the card, offered to install the restricted drivers, I did that and I was good to go! Everything exactly like it should be.

In Gutsy, I installed the restricted drivers, but then I was still stuck in 1280x1024 resolution. My screen (laptop LCD) is 1680x1050 so this looked rather out of place. Worse, there is no option to enter a new resolution (why not?).

I then followed the advice in another ubuntu forum, and did this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

In the first screen, you need to select flgrx as driver - the system had selected vesa for me, I moved up to flgrx and selected it.
In the second screen, I went to the 1680x1050 resolution and hit "space" which selects it.

Then hit return and restart.

After restart, go to 
System->Preferences->Screen Resolution, and select 1680x1050. Done!

I don't use a 3D GUI yet but I can report that all the screen savers work very well, extremely smooth like they should with an X1600 behind them. So I am 100% sure that the 3D acceleration is working as advertised. 
Fantastic screen savers, BTW - no other OS beats linux at screen savers, so much is certain.

I do have a complaint for the ubuntu community though: Why the regression? Feisty automated all this - it detected my card and my screen rez, and I didn't need to futz around with the command line at all. 
One good thing is that the warning for "restricted" drivers seem to be less harsh than last time - or maybe I am imagining it. I am generally not happy with it - show some respect. I don't care if my drivers are proprietary as long as they work. I don't need the many warnings, as if I was about to do something bad. I am not doing anything bad, I am just making my hardware work. /rant.

---

### Post by Gutsy Vegan on 2007-10-24
I finally gave up,,, put my old GEFORCE FX5500 card... everythings working great with the NVIDIA generic drivers.... you win this time Gutsy Gibbon.

---

### Post by MrKirby on 2007-10-25
On the whole "weird stuff when gutsy closes" thing:  I also get weird things happening on my computer after reboots, running my nvidia card.  My particular thing is that my title bars and borders shrink to tiny sizes.  By turning off extra effects, and turning it back on again, things go back to normal--until after a reboot.  This may not be an issue just related to ati users.

---

### Post by Ant_Merlin on 2007-10-25
> On the whole "weird stuff when gutsy closes" thing: I also get weird things happening on my computer after reboots, running my nvidia card. My particular thing is that my title bars and borders shrink to tiny sizes. By turning off extra effects, and turning it back on again, things go back to normal--until after a reboot. This may not be an issue just related to ati users

Sounds like Gutsy problem in general then, this also happens to me, fonts and window buttons go tiny etc. I am also having a problem running games in general.

some wont run in full screen, some have distorted textures, all worked fine in Feisty. I really like the improvements Gutsy make but am seriously considering going back to Fiesty or a different Distro altogether.

---

### Post by Gutsy Vegan on 2007-10-25
edit

---

### Post by Ant_Merlin on 2007-10-26
Ok so latest info, I made he mistake of trying to build the latest ATI driver and install that, ended up totally messing up, couldnt even get fglrxinfo to work. As this was going to be messy to unpick, I decided to start again.

So, fresh install of gutsy again, I have found that it wasnt the graphics driver that was causing the problems but the monitor selection in screens and graphics hat caused the low graphics mode after reboot, managed to get it working straight away this time.

After Install, Enable extra repositories first, then goto restricted drivers and select driver (tick box). This will then install driver.

Restart and select monitor.
mine is an AOC Spectrum 9ltr, but that wont work and has been causing the problems with blank screens and reverting to failsafe. I chose instead generic driver and this has been fine since. Still getting fonts and window icons changing size though....

---

### Post by oaschal on 2007-10-27
> **Mariano Oliveto said:**
> I have an ATI Radeon x1600 Pro AGP 8x 256 MB. I did a fresh install of Gusty a few days ago and I must say I had no problems... Live CD worked just fine and the installation went smoothly, so I'm not sure if this will help anyone.

When I enabled the restricted drivers using the "System -> Administration -> Restricted Drivers Manager" feature, 3D acceleration didn't work very well. E.g.: Skyrocket Screensaver was VERY choppy and all my videos (avi, wmv, mpg, you name it) had a blueish tone. I think also Penguin Racer (which worked OK) had this blueish tone. (All these problems I also had on Feisty)

Since I was using Debian Etch and got my x1600 Pro working I figured I could use the same installation method.

I followed this intructions:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Choosing Gusty this time ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide))

I used Method 2 for installing (reffer to the guide), in other words, I used ATI's driver installer. 

It didn't work for me just yet. I got the following output:

$ fglrxinfo 
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

So I checked the Troubleshooting page ([http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)) and followed the rest of the instructions. They did the trick, Sryrocket screensaver is OK and my videos play normally (no more blue aliens :) )

I don't know if this'll be of any help. I hope it will though.

By the way, wouldn't it make sense for us, ATI users, to ask ATI for better Linux support?? I saw somewhere that there was a request for ATI support for a specific family of ATI's GPUs but I think that it was one that had no driver installer whatsoever. 

Any suggestions??

THIS WORKED for me (ATI Readon X1600 on Ubuntu 7.10) !!!!!! :guitar:

Hint 1: Install Ubuntu 7.10 and don't upgrade!
Hint 2: Don't use the "System->Administration->Restricted Driver Manager" to install your graphics driver!
Hint 3: Follow the instructions carefully and don't forget to do the troubleshooting as mentioned above.

greets and good luck

---

### Post by tnaseem on 2007-10-31
> **oaschal said:**
> THIS WORKED for me (ATI Readon X1600 on Ubuntu 7.10) !!!!!! :guitar:

Hint 1: Install Ubuntu 7.10 and don't upgrade!
Hint 2: Don't use the "System->Administration->Restricted Driver Manager" to install your graphics driver!
Hint 3: Follow the instructions carefully and don't forget to do the troubleshooting as mentioned above.

greets and good luck

It's also worked for me too (up to a point). My card is an X1950 with a Samsung BW226 Monitor. Many thanks Mariano for your tip by the way!

I followed 'Method 2' as suggested, and rebooted. It booted into the native resolution of 1680x1050, which it's never done before; so half way there! No 3D support yet, so I followed the troubleshooting section...

However, when I did the fglrxinfo command, I got the following error:

```

fgrlxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

This was easily solved by issuing the following command:
```

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

```

This fixed that problem, and fglrxinfo now gave the following output, which is what I expected:

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

The problem is that even though I've worked through the rest of the troubleshooting section, I can't seem to get the 3D effects to work. I keep getting the 'Mesa' output above, even after a reboot.

Any clues?

Cheers,
Taz

---

### Post by tnaseem on 2007-10-31
Ok. I've finally got it to work!

That troubleshooting guide didn't work in the end for me. It still listed the Mesa driver instead of the ATI one. So, working on a hunch, I enabled the Restricted Driver (assuming it's now the newer ATI one). Then rebooted.

On enabling the 'Extra' desktop effects in the Appearance Preferences, I received an error message stating 'Composite Extension is not available'.

So I installed it by following the instructions in this forum post:

[http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045)

Once done, I logged out and back in again. Then enabled the effects again. Voila! it worked. :)

Many thanks to all who have provided pointers along the way. 

The only reason I updated was to see if Gutsy would now support my printer. After all this, I bet it doesn't work and all this would have been for nothing :)

Don't you just love technology?

Cheers,
Taz

---

### Post by fsm on 2007-11-02
> **MrKirby said:**
> On the whole "weird stuff when gutsy closes" thing:  I also get weird things happening on my computer after reboots, running my nvidia card.  My particular thing is that my title bars and borders shrink to tiny sizes.  By turning off extra effects, and turning it back on again, things go back to normal--until after a reboot.  This may not be an issue just related to ati users.


Wow...I have the exact same problem, with a GeForce 6600.  It all worked fine in feisty, but now I get everything just right, and when i reboot I'm donw to 800 x 600, or I get tiny title bars.  If I restart X (via ctrl-alt-backspace) it usually comes up fine. Usually...

---

### Post by Mariano Oliveto on 2007-11-02
> **tnaseem said:**
> It's also worked for me too (up to a point). My card is an X1950 with a Samsung BW226 Monitor. Many thanks Mariano for your tip by the way!

You're welcomed! :D but you really should thank the people that wrote the instructions!! :lolflag:

It feels good being able to help someone out after so much help I've found in Linux's Forums (mostly searching ;) )

---

### Post by krutow on 2007-11-05
> **Mariano Oliveto said:**
> I have an ATI Radeon x1600 Pro AGP 8x 256 MB. I did a fresh install of Gusty a few days ago and I must say I had no problems... Live CD worked just fine and the installation went smoothly, so I'm not sure if this will help anyone.

When I enabled the restricted drivers using the "System -> Administration -> Restricted Drivers Manager" feature, 3D acceleration didn't work very well. E.g.: Skyrocket Screensaver was VERY choppy and all my videos (avi, wmv, mpg, you name it) had a blueish tone. I think also Penguin Racer (which worked OK) had this blueish tone. (All these problems I also had on Feisty)

Since I was using Debian Etch and got my x1600 Pro working I figured I could use the same installation method.

I followed this intructions:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Choosing Gusty this time ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide))

I used Method 2 for installing (reffer to the guide), in other words, I used ATI's driver installer. 

It didn't work for me just yet. I got the following output:

$ fglrxinfo 
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

So I checked the Troubleshooting page ([http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)) and followed the rest of the instructions. They did the trick, Sryrocket screensaver is OK and my videos play normally (no more blue aliens :) )

I don't know if this'll be of any help. I hope it will though.

By the way, wouldn't it make sense for us, ATI users, to ask ATI for better Linux support?? I saw somewhere that there was a request for ATI support for a specific family of ATI's GPUs but I think that it was one that had no driver installer whatsoever. 

Any suggestions??

This worked awesome for me... I've been strugglin' with this one for ages it feels like.
Now I can focus on what's really important... who am I kidding, now I haven't got a clue what to do. But thanks anyway!! :)

---

### Post by Gutsy Vegan on 2007-11-19
> **tnaseem said:**
> Ok. I've finally got it to work!

That troubleshooting guide didn't work in the end for me. It still listed the Mesa driver instead of the ATI one. So, working on a hunch, I enabled the Restricted Driver (assuming it's now the newer ATI one). Then rebooted.

On enabling the 'Extra' desktop effects in the Appearance Preferences, I received an error message stating 'Composite Extension is not available'.

So I installed it by following the instructions in this forum post:

[http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045)

Once done, I logged out and back in again. Then enabled the effects again. Voila! it worked. :)

Many thanks to all who have provided pointers along the way. 

The only reason I updated was to see if Gutsy would now support my printer. After all this, I bet it doesn't work and all this would have been for nothing :)

Don't you just love technology?

Cheers,
Taz

OH MY - IT WORKED!!!
the X1600 is working with all it's glory with the advanced 3d effects

thanks dudes!!

---

