---
title: "how to run fsck manually."
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by berkayonen on 2007-09-08
I want to run fsck manually. But i cant. 


I started my computer and i saw the boot screen . ubuntu , win xp , and other chooses. 

i opened command line with c button and typed fsck/dev/hd6 but """ unrecognized command "" 


how can i run fsck manualy.

---

### Post by Herman on 2007-09-08
Hello berkayonen,
It's best to run a file system check from a LiveCD without mounting the hard drive. Most LiveCDs won't mount the hard drive anyway unless you tell them to, but they usually do use the swap area.
We should never run a file system check on a mounted partition.

The easiest Live CD to use is [GParted -- LiveCD]("http://gparted.sourceforge.net/") because it's made for doing all kinds of work with file systems and partitions. All you need to do with that is right-click on the partition and look for the option 'Check' and click on it. Wait a while and your file system check will be complete. You won't need to know any commands.

The Ubuntu Live CDs are fine, you just have to know a couple of commands, here is my favorite one for an ext3 file ssytem to begin with,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
``` Where" hda2 is your ext3 (Ubuntu) partition, if not, replace those letters and numbers with whatever suits your particular computer.

Here's one that's a bit more powerful,
```
sudo e2fsck -y -f -v /dev/hda2
``` It does no harm and probably a lot of good to run that one once in a while.

This one's only for coping with bad blocks in your hard disk, it should rarely  be needed, 
```
sudo e2fsck -c -c -k -v /dev/hda2
```Type 'man e2fsck' if you want to learn what all those options will do for you, there may be more that could help you. You can customize your own commands by reading the man pages and picking out options you think will make the command do what you want. ```
man e2fsck
```Regards, Herman :)

---

### Post by Herman on 2007-09-08
>  i opened command line with c button and typed fsck/dev/hd6 but """ unrecognized command ""
Probably if you typed 'sudo fsck /dev/hda6' that command will work, if hda6 is your Ubuntu partition.
But do it from a Live CD of some kind.

You need to type commands exactly right or they won't work, they need gaps in the right places and a few little things like that.
You can nearly always cheat by copying someone else's commands from somewhere, like this web page, and paste them into your own computer.
Then before you use them, check to make sure there isn't something there you will need to edit to make it suit your computer before you apply the command.

---

### Post by berkayonen on 2007-09-09
Thanks herman everything works great about file system check. Check is done and ubuntu ststus bar under ubuntu logo finished. But when desktop about to seen my computer screen shows something like old tvs :) . I have the same problem at install. I changed resolution 1024x768x32 and problem fixed. How can i change my resolution for opening desktop :guitar:

---

### Post by Herman on 2007-09-09
berkayonen, 
I'm not exactly sure what you mean, but I'll try to explain what I think you want to know. 
When the computer first begins to boot up and you see the GRUB menu, (if your machine is dual booting), and then you see the usplash screen with the progress bar while Ubuntu is loading,  During that time we are using the VGA mode from the BIOS for our display.
To control the display for that we use settings in GRUB, like [ defoptions]("http://users.bigpond.net.au/hermanzone/p15.htm#defoptions") here is a good article about that, **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), by **[Indras]("http://www.ubuntuforums.org/member.php?u=126305").

But I don't think that's what you mean. I think you mean you can see that part okay, but then your X server isn't able to start. Are you able to see the desktop at all? Or do you only see a black monitor with a command line?
If that's what you mean then maybe this webpage will help you, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")   sudo dpkg-reconfigure xserver-xorg (video, keyboard & mouse drivers, settings)

And if that still doesn't help then I have one more idea, boot the LiveCD and mount your hard disk installed Ubuntu and get your  etc/X11/xorg.conf like it says in this link, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD. Then either try to edit it so it will work if you know how, or if you aren't sure you can try copying the LiveCD's etc/X11/xorg.conf to you hard disk and see if that fixes it. You should normally get a backup of your etc/X11/xorg.conf and other important files like that before you make changes.

I hope one or two of those ideas will be some help to you, berkayonen. If you still have trouble be sure to post back here again and explain what's wrong again and I or someone will be around to help you after a while.

Regards, Herman :)
[COLOR=#666666][/COLOR]

---

### Post by berkayonen on 2007-09-09
> **Herman said:**
> berkayonen, 
I'm not exactly sure what you mean, but I'll try to explain what I think you want to know. 
When the computer first begins to boot up and you see the GRUB menu, (if your machine is dual booting), and then you see the usplash screen with the progress bar while Ubuntu is loading,  During that time we are using the VGA mode from the BIOS for our display.
To control the display for that we use settings in GRUB, like [ defoptions]("http://users.bigpond.net.au/hermanzone/p15.htm#defoptions") here is a good article about that, **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), by **[Indras]("http://www.ubuntuforums.org/member.php?u=126305").

But I don't think that's what you mean. I think you mean you can see that part okay, but then your X server isn't able to start. Are you able to see the desktop at all? Or do you only see a black monitor with a command line?
If that's what you mean then maybe this webpage will help you, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")   sudo dpkg-reconfigure xserver-xorg (video, keyboard & mouse drivers, settings)

And if that still doesn't help then I have one more idea, boot the LiveCD and mount your hard disk installed Ubuntu and get your  etc/X11/xorg.conf like it says in this link, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD. Then either try to edit it so it will work if you know how, or if you aren't sure you can try copying the LiveCD's etc/X11/xorg.conf to you hard disk and see if that fixes it. You should normally get a backup of your etc/X11/xorg.conf and other important files like that before you make changes.

I hope one or two of those ideas will be some help to you, berkayonen. If you still have trouble be sure to post back here again and explain what's wrong again and I or someone will be around to help you after a while.

Regards, Herman :)





Yes my x server is not working. I tried ctrl+alt+f1....f6 but not works. I can see my partition on windows and my xorg file like this. I want to change my default desktop resolution



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
	Option		"XkbVariant"	"alt"
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
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
	Driver		"nv"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Genel Monitör"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [Geforce 6150 Go]"
	Monitor		"Genel Monitör"
	DefaultDepth	32
	SubSection "Display"
		Depth		32
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Herman on 2007-09-10
```
 Section "Monitor"
    Identifier    "Genel Monitör"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Genel Monitör"
    DefaultDepth    32
    SubSection "Display"
        Depth        32
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "1280x800"
    EndSubSection
EndSection
```You probably only need to change this part of it.




```
 Section "Monitor"
    Identifier    "Genel Monitör"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Genel Monitör"
    DefaultDepth    32
    SubSection "Display"
        Depth        32
        Modes        "**1024x768**"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "**1024x768**"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "**1024x768**"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "**1024x768**"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "**1024x768**"
    EndSubSection
    SubSection "Display"
        Depth        32
        Modes        "**1024x768**"
    EndSubSection
EndSection
```That should at least get you started.

Regards, Herman :)

---

