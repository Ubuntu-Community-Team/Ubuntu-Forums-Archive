---
title: "AM2 X2 3800+, Asus M2NPV, Installer Crashes.  Need advice"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by coreyt on 2006-07-29
I know the risks of a new system, but I did not see any red flags other than some problems with Audio.


When installing the system the installer crashes out on "Installing Software" graphical and text mode.  I've tried turning the network off, acpi=off, noapic nolapic.

About to give the 64bit version a go and see what happens, but would rather go 32bit for compatiblity reasons.


What else can I try?

---

### Post by coreyt on 2006-07-29
I've gone back into the text installer and it's crashing out on thai-ttf packages on OEM setup.  On the regular setup it crashed out on some of the audio stuff.

---

### Post by coreyt on 2006-07-30
Seems a BIOS upgrade was necessary to get the problem to go away.  No extra options needed in the Kernel as well after I upgraded.

---

### Post by coreyt on 2006-08-01
and after all that mess we had a segfault party..


Took the memory back and luckily they had what I wanted..  the other memory one stick would not pass memtest.

---

### Post by resistfascism on 2006-11-10
After skimming over the thread, I see that a basic outline of what needs to be done to install edgy on a machine with this hardware is here, but it's a little light on details, so I thought I'd fill them in.

First of all, when I downloaded/burned both edgy 64 desktop & server install CD images, my system froze after selecting the option to install edgy from the menu that is displayed after booting off the CD.

So, as is indicated earlier in the thread, I had to update the bios firmware.

I got a copy of the latest firmware from the asus web site: 0504.bin.

Now, I needed a way to get the 0504.bin into the bios update utility.

For some reason, I don't know why, I thought I needed to make a bootable memory stick, but I'm pretty sure an ordinary memory stick with a vfat file system would work.

Anyway, it's a good trick, so I'll digress and say how I built the file system on the memory stick I used to do the bios update:

Open a terminal window

type mount

make sure your memory stick hasn't been automoutned, unmount it if it is

*warning, next step will destroy all data on the memory stick*

first, make a fat 16 file system on the memory stick (fat 32 may work, I didn't test so I can't say for sure):

Unmount the memory stick if your system's automounted it

mkdosfs  -F 16 /dev/sda 

(your memory stick may be represented by a different node in the /dev/directory, the way to find out which one it is is type dmesg | less and look for a message with a time stamp during which you plugged the memory stick in, if you just stuck it in, it should be near the bottom of the output - hint type 'G' if you did dmesg | less)

now, you need an image for the memory stick.  I chose freedos because it'd be compatible with the file system created above.  You need to download the image from:

[http://www.fdos.org/bootdisks/autogen/FDSTD.288.imz](http://www.fdos.org/bootdisks/autogen/FDSTD.288.imz), and unzip it.

The archive manager program that's default in dapper desktop will will work, but you could also just unzip it from the command prompt:

unzip FDSTD.288.imz

And that'll give you the image file fdstd.288

Now, copy that image on to the memory stick:

sudo dd if=fdstd.288 of=/dev/sda

(make sure to change sda to whatever node the o/s associated with your memory stick - see note about dmesg above)

If you're curious, you can mount the memory stick and make sure you've really got a file system and a directory tree and all that.

You need to mount the stick anyway, because you've got to copy the firmware update to it.

sudo mount /dev/sda1 /mnt

sudo cp 0504.bin /mnt

Now, you're good to go.

sudo umount /mnt

sudo reboot

OK, make sure you hit delete to get in to the bios before it's too late, or just for kicks, see if you can boot off the mem. stick - and by the way, maybe somebody can tell me, why is it that sometimes when you hit f8 to get into the boot menu, sometimes it hangs with a memory stick in the usb port, and sometimes it starts just fine?

Say no to all the questions your prompted to answer when booting off the stick, and you'll get a command prompt (yay).

OK, enough fooling around! Back to the original mission: update the bios.

Hit delete to get into the bios, and navigate to the firmware update screen.

The memory stick showed up as the b drive for me.  Select 0504.BIN and let the updater do its thing.

By the way, its a good idea to have a very stable source of electricty, such as an ups when running the bios update (i.e. don't do this with power coming straight from the wall in New Jersy during a 150 degrees F heatwave in the middle of the day, when your entire city is running their air conditioners at full blast, if you loose power you'll wind up with a very large paperweight).

OK, so now the bios is updated, you can reboot to the cd, and install edgy!

I chose the LAMP server install, but I actually wanted to use the server as a development test-bed for my web site, so I had to add some extra software to get the gnome-desktop environment going.

My first problem with that was apt-get install gnome-desktop-environment wouldn't work because /etc/apt/sources.list didn't have pointers to the right archives.

To fix that, I copied /etc/apt/sources.list from a previous dapper install and overwrote the default /etc/apt/srouces.list.

In case you don't have an old dapper install from which to copy sources.list, I've pasted my /etc/apt/sources.list below, so you can just use that:

deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

If you want to use another sources.list from an older version of ubuntu, just make sure you substitute all occurences of the name of the older version (i.e. "dapper") with "edgy" so you're downloading compatible software.

Now, get all that good gui stuff that makes life so much easier, but actually has no business being on a server:

When the install is finally done, and you boot edgy for the first time, you get a console log in prompt. So log in and start grabbing some software!

Just FYI, since I had to do some googling to figure out what packages I needed to install, I first grabbed lynx:

apt-get install lynx

That got me a basic web browser, that worked well enough to search with google.

Then I used the virtual console switching trick that is so useful when working with console only, that everyone should know about:

Hold down the left 'alt' key and press f1, f2, f3, etc. to get yet another log in prompt.  This is especially useful if you've got documentation you need to read, and commands you have to enter.  
apt-get install gnome-desktop-environment
apt-get install xserver-xorg
apt-get install xfonts-base

and now you're ready to fire up gnome, but you might need to generate /etc/X11/xorg.conf

Once again, I just copied over /etc/X11/xorg.conf from my old dapper install, and used that.  Once again, I've pasted that file below, so you can use that for a starting place.

*warning*

Make sure you modify the monitor definition's horizsync and vertrefresh settings because you can FRY your monitor if you put the wrong values in.

Either use google or consult the manual that came with your monitor for those settings.

I have a dual monitor setup, with another nvidia graphics card in the pci express slot, so that's what this xorg.conf is set up to do.  If you're just using the on board 6150, all you need to do is comment out the stuff for the second monitor, and change the screen definition.

/etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Load	"i2c"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card0"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card1"
	Driver		"nv"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor0"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	55-75
EndSection

Section "Monitor"
	Identifier	"Generic Monitor1"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	55-75
EndSection

Section "Screen"
	Identifier	"Default Screen0"
	Device		"NVIDIA Corporation NVIDIA Default Card0"
	Monitor		"Generic Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen1"
	Device		"NVIDIA Corporation NVIDIA Default Card1"
	Monitor		"Generic Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	#Screen		"Default Screen"
	Screen        "Default Screen0"
	Screen        "Default Screen1" RightOf "Default Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	#Option "Twinview" "On"
	Option "Xinerama" "On"
EndSection

Section "DRI"
	Mode	0666
EndSection

Alternatively, you can use a utility to generate xorg.conf

Now, you can start the gnome desktop environment:

startx

The first thing I did after that was install the wonderful synaptic package manager.  I'm not sure if it was already there or not, but at that point I'd had a lot of coffee and my eyeballs were moving a little faster than I could read.  Anyway, it didn't hurt to do:

apt-get install synaptic

and now you're good to go and grab all the rest of that terrific open source software and tailor the system to your needs.

Cheers!

---

