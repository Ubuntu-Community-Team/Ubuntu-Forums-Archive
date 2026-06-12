---
title: "Direct rendering: No"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by dood123 on 2007-11-11
I know that there is many direct rendering posts but i did not find help for my problem from other posts.

So my problem is a bit odd... My drivers should be working fine and they got all things fine but still I got direct rendering: no and my graphic card won't accelerate. Does anybody else have similiar problems?

My xorg.conf:

```
Section "Files"
        EndSection

        Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
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
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"		"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "Module"
        Load "drm"
EndSection
```

I am bit noob with ubuntu but my friend who knows nearly everything about ubuntu checked my problem and he said that drivers are working correctly and card should accelerate but it just won't. :(

---

### Post by KIAaze on 2007-11-11
Do you have those things installed?:
[LIST]
[*]libgl1-mesa-dri
[*]libgl1-mesa-glx
[*]libglu1-mesa
[*]mesa-utils
[/LIST]
(First two ones should be sufficient, but that's what I installed once under Debian to get DRI working.)

Also, what video card do you have?

---

### Post by dood123 on 2007-11-12
Yes I have those installed and i am using Ati Radeon 9600 graphics gard

---

### Post by KIAaze on 2007-11-12
I just found something very interesting:
> 
The main problem with making use of the Linux ATi proprietary drivers - fglrx is that if composite is enabled then the drivers will not be loaded properly with the OpenGL implementation Mesa. In order to have the drivers working properly with DRI the Composite option in /etc/xorg.conf must not be enabled. This is not what you want to do if you want to make use of the absolutely amazing Beryl.

Alternatively the Open Source Xorg xf86 ATi video drivers can be made use of. These drivers allow you to have DRI enabled and make use of Composite at the same time (by using the preffered method AIGLX, at the time of writing this).
[http://www.vikrammohan.com/blog/2006/11/26/dri-on-ati-radeon-9600-mobility-m10-toshiba-sp30-110-gentoo-linux/]("http://www.vikrammohan.com/blog/2006/11/26/dri-on-ati-radeon-9600-mobility-m10-toshiba-sp30-110-gentoo-linux/")

Might actually also help me, since I have DRI enabled, but compiz-fusion doen't work correctly (games do however). :)

Unfortunately, it seems you'll have to recompile your kernel if you choose the second option.
I don't have a lot of experience with that, but maybe your friend can help you.
Otherwise just google for "kernel recompilation tutorial" or something like that.

For the first option, all you need to do is probably write:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection

```
instead of Option "Composite" "Enable" in your xorg.conf file (remember to back it up) and then restart gdm (ctrl+alt+backspace).

I also recommend using [xorg-edit]("http://www.deesaster.org/progxorg.php") for editing the xorg.conf file.

Other than that, have you tried the tutorials here:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.23.7.29]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.23.7.29")
[http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html]("http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html")
If you speak french, there's also:
[http://doc.ubuntu-fr.org/fglrx]("http://doc.ubuntu-fr.org/fglrx")

And think of googling too:
[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=Swiftfox%3Aen-US%3Aunofficial&hs=fNB&q=linux+ati+radeon+9600+dri&btnG=Search]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=Swiftfox%3Aen-US%3Aunofficial&hs=fNB&q=linux+ati+radeon+9600+dri&btnG=Search") (That's how I found the probable cause of the problem.)
[http://www.google.com/search?q=linux+ati+radeon+9600&ie=utf-8&oe=utf-8&aq=t&rls=Swiftfox:en-US:unofficial&client=firefox-a]("http://www.google.com/search?q=linux+ati+radeon+9600&ie=utf-8&oe=utf-8&aq=t&rls=Swiftfox:en-US:unofficial&client=firefox-a")

If I ever get to recompiling my kernel and you still haven't done it, I'll post here again. ;)

edit:
Just in case you get a scrambled screen or DRI still doesn't work:
Try out downgrading to the Feisty ATI driver: [http://ubuntuforums.org/showthread.php?t=526947&highlight=downgrade&page=3]("http://ubuntuforums.org/showthread.php?t=526947&highlight=downgrade&page=3")

It's certainly not the best solution, but a lot of changes have been made to the ATI driver, so it might be the cause of new problems.

---

### Post by dood123 on 2007-11-12
I reinstalled the whole kernel but it didn't work.. Do you think that recompiling will do the trick if even reinstalling kernel won't do it?

---

### Post by KIAaze on 2007-11-12
Did you make the changes indicated on the site when running "make menuconfig"?

From what little I understood, you have to recompile the kernel with AGP support. So it's not exactly the same as reinstalling.

To know if your current kernel has loaded the AGP driver, run this command:
```
lsmod | grep agpgart
```

Here's what I get for example:
```
$lsmod | grep agpgart
agpgart                35016  2 drm,ati_agp

```

Here's some more info I found:
[http://gentoo-wiki.com/HOWTO_DRI_with_ATi_Open-Source_Drivers]("http://gentoo-wiki.com/HOWTO_DRI_with_ATi_Open-Source_Drivers")
[http://linuxplanet.com/linuxplanet/tutorials/202/1/]("http://linuxplanet.com/linuxplanet/tutorials/202/1/")
[http://math-www.uni-paderborn.de/~axel/config_help.html]("http://math-www.uni-paderborn.de/~axel/config_help.html")
[http://linuxreviews.org/sysadmin/kernel-configuration/]("http://linuxreviews.org/sysadmin/kernel-configuration/")

The first link is for Gentoo systems, so when there's a command like:
```
emerge package
```
replace it with:
```
sudo apt-get install package_2
```
where package_2 is the equivalent package for Ubuntu. (Search in Synaptic or [http://packages.ubuntu.com/](http://packages.ubuntu.com/))

---

### Post by dood123 on 2007-11-21
Yay! I did it! Thanks for advice. :) I solved my problem with this post: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

But huge thanks to you KIAaze you gave me the clue: :)

---

