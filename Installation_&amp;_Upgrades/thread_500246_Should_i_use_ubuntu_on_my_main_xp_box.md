---
title: "Should i use ubuntu on my main xp box?"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Synth3t1c on 2007-07-13
Okay, I've used ubuntu on my laptop off and on from breezy until dapper. at dapper, i decided it was time to just shove it down my own throat. Now, I love it. I have everything exactly how I want it, and I didn't have to jump through any hoops to do it. I only used that laptop for web browsing and word processing though, so not any funky stuff going on.


Here's the problem with switching to Fiesty on my xp box:
I have an ATI card (the lowly x300). First off I want to make sure it can display at 1280x1024.

Secondly, If i have cedega, can i run WOW at that resolution (or any fps's?).
what about WINE with photoshop cs2?

I got a p4 3.4 ghz with h/t and 2 gigs of ram, about 500 gigs total of hard drive space including my external drive. I think the only limiting factor is the driver support for my gfx card.


I also have a TV tuner card of unknown brand (came with my computer - sony vgc-rb38g). I don't use it much, but will that work as well?


thanks in advance for all the help

---

### Post by tgm4883 on 2007-07-13
> **Synth3t1c said:**
> Okay, I've used ubuntu on my laptop off and on from breezy until dapper. at dapper, i decided it was time to just shove it down my own throat. Now, I love it. I have everything exactly how I want it, and I didn't have to jump through any hoops to do it. I only used that laptop for web browsing and word processing though, so not any funky stuff going on.


Here's the problem with switching to Fiesty on my xp box:
I have an ATI card (the lowly x300). First off I want to make sure it can display at 1280x1024.

Secondly, If i have cedega, can i run WOW at that resolution (or any fps's?).
what about WINE with photoshop cs2?

I got a p4 3.4 ghz with h/t and 2 gigs of ram, about 500 gigs total of hard drive space including my external drive. I think the only limiting factor is the driver support for my gfx card.


I also have a TV tuner card of unknown brand (came with my computer - sony vgc-rb38g). I don't use it much, but will that work as well?


thanks in advance for all the help

Hmm, I don't know about the ati card, or WOW.  Check [www.winehq.org](www.winehq.org) in the apps section to see about photoshop CS2.  Computer looks fine to run it.  As for the video card.  Pop in a live CD (may be a good way to test the video card too) and post the output of lspci from the terminal.  Will help figure out what TV card is in there.

---

### Post by tgm4883 on 2007-07-13
Did a little googling around, I think this is the card you have
Sony's Giga Pocket TV Tuner

It looks like it works in mythtv as one guy wrote his own driver for it, but the rest of the thread I see are old. Maybe it works now, but maybe we will have to ask him for it.

---

### Post by Synth3t1c on 2007-07-13
i will ask him for it, and that sounds about right.

im gonna do the livecd now.

---

### Post by Synth3t1c on 2007-07-13
okay, first off im on the livecd now and i tried to change resolution to 1280x1024.  It can only go to 1024x768, making my monitor look like $h!t.  is that just the livecd?


heres my lspci

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
06:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

---

### Post by tgm4883 on 2007-07-13
> **Synth3t1c said:**
> okay, first off im on the livecd now and i tried to change resolution to 1280x1024.  It can only go to 1024x768, making my monitor look like $h!t.  is that just the livecd?


heres my lspci

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
06:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

Thats the live cd, its because you don't have the restriced drivers installed for your video card.  It looks like your card works well, i'll do a little more checking in it though

---

### Post by Synth3t1c on 2007-07-13
ok thanks.

so what do u think about cs 1.6?

---

### Post by tgm4883 on 2007-07-13
> **Synth3t1c said:**
> ok thanks.

so what do u think about cs 1.6?

Haven't played it in a long time (about 3 years)

---

### Post by Synth3t1c on 2007-07-13
> **tgm4883 said:**
> Haven't played it in a long time (about 3 years)

lol will it work with cedega and my ati card?

---

### Post by tgm4883 on 2007-07-13
Looks like it works in Cedega [http://games.cedega.com/gamesdb/games/view.mhtml?game_id=3542](http://games.cedega.com/gamesdb/games/view.mhtml?game_id=3542)

Before you try that, you should try it in Wine, as I have installed Steam and Half Life 2 in Wine and it works.  

Still don't know about your card though, you should search around for other people with that card.  I have an nVidia card and am more knowledgeable in the TV tuner area.

---

### Post by Synth3t1c on 2007-07-13
> **tgm4883 said:**
> Thats the live cd, its because you don't have the restriced drivers installed for your video card.  It looks like your card works well, i'll do a little more checking in it though

i installed ubuntu and the restricted drivers, and after restarting I can't select that resolution still.  :(

---

### Post by tgm4883 on 2007-07-13
> **Synth3t1c said:**
> i installed ubuntu and the restricted drivers, and after restarting I can't select that resolution still.  :(

What is your desired resolution?  And can you post your xorg.conf?

---

### Post by Synth3t1c on 2007-07-13
> **tgm4883 said:**
> What is your desired resolution?  And can you post your xorg.conf?

1280x1024

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
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
	Option		"Composite"	"0"
EndSection

---

### Post by tgm4883 on 2007-07-14
do 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then change the modes lines from

Modes "1024x768" "800x600" "640x480"

to 

Modes "1280x1024"

Then restart GDM

---

