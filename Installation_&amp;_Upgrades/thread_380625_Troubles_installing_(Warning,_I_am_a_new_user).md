---
title: "Troubles installing (Warning, I am a new user)"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by chilin_dude on 2007-03-09
Hi all,

first off thanks for spending any time reading over this thread - any help is much appreciated. 
I am currently a Windows user, however I have decided that it is time for me to switch to Linux as I'm getting frustrated at Windows and I like the open source side of Linux (I'm first year of a computer Science degree and hoping to contribute in the future.) After researching the various distro's I decided that Ubuntu was the one that I wanted and proceeded to find a install guide, in the end I was hoping to use the following one:  download the amd64 bit CD. This took ages as the internet I'm on is appaling, however today it finished and I successfully burnt it to CD and booted it up. However I'm having troubles because when the first screen on the CD pops up, when I select option 1 I get the message '"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"' After about 2 minutes. 
So I turned my computer off and this time selected option 2 (something about a safer graphic option I believe) however I got the same message again.
I have googled about this error and found various people with similar problems, however most of them were AFTER they had installed and people were giving tips of editing this and that in the config files. However I dont believe I can do this since I haven't installed it yet. So my question is, how do I go about getting around this error and continue with the install?

My Video card: RADEON X700 Series Secondary (Omega 3.8.330)  
AMD 64 Processor 3200+
1GB Ram
1 SATA2 Hard drive
1 IDE Hard drive.


Thanks in advance for any replies, no matter how trivial you think they may be!
Chilin

---

### Post by taurus on 2007-03-09
Sounds like you need to use the alternate CD to install it on your machine.  Your school should have a fast network connection so why not use the computer lab, download, and burn the alternate CD.

---

### Post by chilin_dude on 2007-03-09
Thanks for the speedy reply, can you tell me where I may aquire the alternate CD and if theres a 64bit version available? I'll get the download going overnight and hopefully have it done for tomorrow night.
Unfortunately the university I'm at doesn't have computer labs open on a weekend.

---

### Post by taurus on 2007-03-09
Here you go.  Just scroll down and download whichever version you want.

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by chilin_dude on 2007-03-09
Thanks a lot, I'm downloading it now.
Can I ask why you believe this will work? And do I still follow the same install routine as I was previously?
Thanks

---

### Post by taurus on 2007-03-10
Sometimes the LiveCD is having a little technical difficulty with some graphic cards.  Therefore, you would get that kind of error message about X or monitor is out of range.  Meanwhile, the alternate CD will use text base and it doesn't have to boot into Live first.  Therefore, you just hit the enter (with the first option) and you are installing it right away.  Even though it's a text installer, it's real easy to follow so you shouldn't have any problem with it.

---

### Post by chilin_dude on 2007-03-11
Hello again.
I downloaded and burnt the CD and went through the install proccess successfully (all be it using the non GUI version.)
However now when I start up the computer I still get the message I was receiving before of '"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"'

And then when I click ok I'm booted to what I believe is a command line where I can type whatever I want. However I dont know how to quit or anything so typing 'exit' or 'reboot' or 'shutdown' doesn't do anything so I keep manually turning the PC off.

What can I do?
Thanks.

---

### Post by chilin_dude on 2007-03-11
Man this is annoying, Last 30 mins I've been trying various things such as removing my secondary monitor to see if this helps but it doesn't =[

---

### Post by wesley_of_course on 2007-03-11
Wesley here ;

  At the command prompt try typing , startx
 worth a try , Good Luck and Welcome - 
This is a blast !

---

### Post by chilin_dude on 2007-03-12
Hi, just tried booting ubunutu again, this time after I got the xserver message I get the login prompt, (all be it in the black command line), after I logged in I typed 'startx' and got the same message error as before "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"'
:(
Thanks for the continued help though, I want to get this running!

---

### Post by taurus on 2007-03-12
After you log in to a console, run

```
sudo dpkg-reconfigure xserver-xorg
```
And if you are not sure about a question, just use the default and use **vesa** driver for your graphic card.

Then, reboot and see if X is coming up this time.

```
sudo shutdown -r now
```

---

### Post by chilin_dude on 2007-03-12
> **taurus said:**
> After you log in to a console, run

```
sudo dpkg-reconfigure xserver-xorg
```
And if you are not sure about a question, just use the default and use **vesa** driver for your graphic card.

Then, reboot and see if X is coming up this time.

```
sudo shutdown -r now
```

Just tried this, firstly I couldn't get to the console as after I got the xserver message it took me to a blank screen where I could type but no commands or anything were being process (the login prompt didn't pop up.) So I ran the 'recovery' option from Grub and typed what you said, it then took me through the walk through process of the graphics card, it auto recognised it was ATI and also it was the 700 version, then it started asking lots of questions which i used the default option mainly. However at the end of it I typed the restart command you wrote and it rebooted and I had the same xserver error message.
Thoughts I have:
Could it be caused because I am using two different monitors? They are running 2 different resolutions currently, when it asks me for the resolution in that xorg thing what should I type? In windows I have my primary running 1280x1024 and my secondry 1440x900.

Thanks in advance.

---

### Post by chilin_dude on 2007-03-12
Or maybe it's because I dont have any ATI drivers installed? Or should they automatically still display on the screens?

---

### Post by taurus on 2007-03-12
You should use **vesa** driver when you run that command to reconfigure your X.

---

### Post by chilin_dude on 2007-03-12
> **taurus said:**
> You should use **vesa** driver when you run that command to reconfigure your X.

How do I chose this driver please?

---

### Post by chilin_dude on 2007-03-12
Nevermind I figured it out (had to click 'no' at detect automattic driver.')
Anyhow I selected Vesa and went through the whole progress and now when I boot up my two screens go to standby and I have no display what so ever.

---

### Post by taurus on 2007-03-12
You need to disconnect a secondary monitor and try to get X running with one monitor first.  Then, install a driver for your graphic card and then configure it dual monitor.

---

### Post by chilin_dude on 2007-03-12
> **taurus said:**
> You need to disconnect a secondary monitor and try to get X running with one monitor first.  Then, install a driver for your graphic card and then configure it dual monitor.
Ok, I will try doing that now, but do I need that VESO driver to be in use or the ATI one when I try to set it up?

---

### Post by chilin_dude on 2007-03-12
I just have disconected one of my monitors, and then configured ubuntu to use the ATI driver first, then rebooted. When I then booted up Ubuntu I got the xserver message again and when I click the log I see:
'(EE) No devices deteceted. 
Fatal Server error: No screens found.

So I tried reconfiguring using the VESA driver. This still just turns the monitor off.

:(

---

### Post by chilin_dude on 2007-03-12
Could this be something to do with the fact I'm using a PCI-Express card?

---

### Post by weedos on 2007-03-12
hi! i had the same problem, and its because of ATI (i have x800XT). I am newbe to ubuntu and linux to, so i asked for help guys in local ubuntu community. you see, it will not work with vesa drivers, you should use fglrx instead.

---

### Post by weedos on 2007-03-12
i searched the forums, and i just got this topic. it can help, try it. [http://ubuntuforums.org/showthread.php?t=190133&highlight=install+ati](http://ubuntuforums.org/showthread.php?t=190133&highlight=install+ati)

---

### Post by chilin_dude on 2007-03-12
Thanks for the help - Unfortunately I've allready read that thread to no avail so far, hear is my XORG.CONF file:
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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"ATI Technologies, Inc. Radeon X700 (RV410)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Acer AL1715"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X700 (RV410)"
	Monitor		"Acer AL1715"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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


And here is my Error log:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux Chilin 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 12 23:57:04 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Acer AL1715"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X700 (RV410)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10b9,1695 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10b9,524b card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 10b9,524c card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10b9,524d card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10b9,1689 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:05:0: chip 10b9,5246 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10b9,5249 card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 00:07:0: chip 10b9,1563 card 1849,1563 rev 70 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 10b9,7101 card 1849,7101 rev 00 class 06,80,00 hdr 80
(II) PCI: 00:08:0: chip 10b9,5455 card 1849,0850 rev 20 class 04,01,00 hdr 00
(II) PCI: 00:11:0: chip 10b9,5263 card 1849,5263 rev 40 class 02,00,00 hdr 00
(II) PCI: 00:12:0: chip 10b9,5229 card 1849,5229 rev c7 class 01,01,8a hdr 00
(II) PCI: 00:13:0: chip 10b9,5237 card 1849,5237 rev 03 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 10b9,5237 card 1849,5237 rev 03 class 0c,03,10 hdr 80
(II) PCI: 00:13:2: chip 10b9,5237 card 1849,5237 rev 03 class 0c,03,10 hdr 80
(II) PCI: 00:13:3: chip 10b9,5239 card 1849,5239 rev 01 class 0c,03,20 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,5e4d card 148c,2116 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5e6d card 148c,2117 rev 00 class 03,80,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2360 card 1849,0360 rev 00 class 01,06,01 hdr 00
(II) PCI: 05:05:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x0000bfff (0x3000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff100000 - 0xff1fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xb7f00000 - 0xd7efffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff200000 - 0xff2fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xff300000 - 0xff3fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:5:0), (0,4,4), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xff400000 - 0xff4fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:6:0), (0,5,5), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xff500000 - 0xff5fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV410 [Radeon X700 (PCIE)] rev 0, Mem @ 0xc0000000/28, 0xff1f0000/16, I/O @ 0xb000/8, BIOS @ 0xff1c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV410 [Radeon X700 (PCIE)] (Secondary) rev 0, Mem @ 0xff1e0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xdc000000 from 0xdfffffff to 0xdbffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xff5ffc00 - 0xff5ffcff (0x100) MX[B]
	[1] -1	0	0xff3fe000 - 0xff3fffff (0x2000) MX[B]
	[2] -1	0	0xff6fe800 - 0xff6fe8ff (0x100) MX[B]
	[3] -1	0	0xff6fb000 - 0xff6fbfff (0x1000) MX[B]
	[4] -1	0	0xff6fc000 - 0xff6fcfff (0x1000) MX[B]
	[5] -1	0	0xff6fd000 - 0xff6fdfff (0x1000) MX[B]
	[6] -1	0	0xff6fec00 - 0xff6fecff (0x100) MX[B]
	[7] -1	0	0xff6ff000 - 0xff6fffff (0x1000) MX[B]
	[8] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[9] -1	0	0xff1c0000 - 0xff1dffff (0x20000) MX[B](B)
	[10] -1	0	0xff1f0000 - 0xff1fffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[16] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xff1e0000 - 0xff1effff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff5ffc00 - 0xff5ffcff (0x100) MX[B]
	[1] -1	0	0xff3fe000 - 0xff3fffff (0x2000) MX[B]
	[2] -1	0	0xff6fe800 - 0xff6fe8ff (0x100) MX[B]
	[3] -1	0	0xff6fb000 - 0xff6fbfff (0x1000) MX[B]
	[4] -1	0	0xff6fc000 - 0xff6fcfff (0x1000) MX[B]
	[5] -1	0	0xff6fd000 - 0xff6fdfff (0x1000) MX[B]
	[6] -1	0	0xff6fec00 - 0xff6fecff (0x100) MX[B]
	[7] -1	0	0xff6ff000 - 0xff6fffff (0x1000) MX[B]
	[8] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[9] -1	0	0xff1c0000 - 0xff1dffff (0x20000) MX[B](B)
	[10] -1	0	0xff1f0000 - 0xff1fffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[16] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xff1e0000 - 0xff1effff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff5ffc00 - 0xff5ffcff (0x100) MX[B]
	[5] -1	0	0xff3fe000 - 0xff3fffff (0x2000) MX[B]
	[6] -1	0	0xff6fe800 - 0xff6fe8ff (0x100) MX[B]
	[7] -1	0	0xff6fb000 - 0xff6fbfff (0x1000) MX[B]
	[8] -1	0	0xff6fc000 - 0xff6fcfff (0x1000) MX[B]
	[9] -1	0	0xff6fd000 - 0xff6fdfff (0x1000) MX[B]
	[10] -1	0	0xff6fec00 - 0xff6fecff (0x100) MX[B]
	[11] -1	0	0xff6ff000 - 0xff6fffff (0x1000) MX[B]
	[12] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[13] -1	0	0xff1c0000 - 0xff1dffff (0x20000) MX[B](B)
	[14] -1	0	0xff1f0000 - 0xff1fffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xff1e0000 - 0xff1effff (0x10000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 6.6.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) ATI: ATI driver (version 6.6.2) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X700 (RV410)".
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by weedos on 2007-03-13
well, you still have vesa drivers. thats why it doesnt work.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 (RV410)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
```
what you should do is: when grub loader starts, go for recovery mode (im not sure that its called exatly like i wrote :) ) you will load ubuntu without grafical interface. when its all loaded run this commands in a terminal:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

its worked for me, and i had exactly the same problem you have.
P.S. What ubuntu install cd do you have? i installed mine with ubuntu alternate installation, couse it wouldnt work other way.

---

### Post by chilin_dude on 2007-03-13
Thanks for the reply.
I used the alternate installation also as the normal version wouldn't work.
I can't do that as I dont currently have internet access as I use wireless internet and haven't installed the wireless driver for linux yet.
However  I have downloaded the ATI autoinstall 64 bit .run file and copied it to my linux partition using ltools.
I copied it to the root of the partition that contains the folders "home", "usr" etc and I've named it ati.run.
What would be the commands to get this to install from the recovery console please?

---

### Post by weedos on 2007-03-13
hm, dont know man. i'm new to this just like you. i just share my experience in solving this problem with you, couse i went through same **** like you :) i have adsl connection though, and have no problem with downloading through terminal... maybe some users with more experience would help... 
try with: 
sudo ati.run


maybe it help, i dont know is it possible, just my guess.

---

### Post by chilin_dude on 2007-03-13
Can anyone else help? I have tried sudo ati.run to no avail

---

### Post by chilin_dude on 2007-03-16
*bump*

---

