---
title: "xorg, dualscreen, ati problem: mouse cursor garbage"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by Kinkerl on 2006-10-07
hi

today, i updated my ati drivers. i got the installer from ati.com and everything went fine. 
after my reboot, the mouse cursor was a total mess on the secound screen. i dont realy know how to discribe it. its just a 2 x 2 cm bock of ... pixels. i think its the area where the mousecursor is drawn on.

i am using a laptop (wide screen) and a crt monitor. everything is working fine but this is driving me nuts. 

i tried other color depth...

here is my xorg.conf

bye

```
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
	load "dbe"
	load "v4l"
	
EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

				
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "NEC MultiSync FE950"
	Gamma   1.00  1.00  1.00  # created by KGamma
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        ModelName    "PANEL"
  	Gamma   1.00  1.00  1.00  # created by KGamma
EndSection

	
Section "Device"
	Identifier  	"Videocard0"
	Driver      	"fglrx"
	VendorName  	"ATI"
	BoardName   	"ATI Radeon 7500"
	BusID       	"PCI:1:0:0"
	Screen 		0
	# hilft bei problemen mit videos
	# http://forum.ubuntuusers.de/topic/34665/
	Option  "VideoOverlay"  "on"
	Option  "OpenGLOverlay"  "off"
EndSection

Section "Device"
       Identifier  	"Videocard1"
        Driver      	"fglrx"
	#Driver		"radeon"
	VendorName  	"Videocard vendor"
	BoardName   	"ATI Radeon 7500"
        BusID       	"PCI:1:0:0"
	Screen 		1
	# hilft bei problemen mit videos
	# http://forum.ubuntuusers.de/topic/34665/
	Option  "VideoOverlay"  "on"
	Option  "OpenGLOverlay"  "off"
EndSection
						
Section "Screen"
	Identifier "CRT"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier "Panel"
        Device     "Videocard1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1400x1024" 
        EndSubSection
EndSection
	
Section "ServerLayout"
	Identifier     	"Doulbe Layout"
	Screen         	"Panel"
	Screen         	"CRT" RightOf "Panel"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option	       	"Xinerama" "On"
	Option 		"ConnectedMonitors" "CRT,Panel"
EndSection		

Section "DRI"
       Mode         0666
EndSection


```

---

### Post by bowill on 2006-10-30
I had the same problem after upgrading to Edgy today. I figured out that the composite extension is enabled by default in Edgy, which breaks existing ATI configurations, since the fglrx driver won't do DRI or 3D acceleration if the composite extension is enabled.

I added this to my xorg.conf.

```

Section "Extensions"
    Option "Composite" "disable"
EndSection

```

3D acceleration and DRI both started working again, which solved the mouse problem and dramatically improved performance.

---

### Post by crunge on 2006-11-06
I have a IBM T60 with an ATI Radeon X1400.

I upgrade to Edgy today (well, wiped my root partition and reinstalled).  I installed the fglrx drivers and set up my dualhead as I usually do with aticonfig.  Only now I'm getting a block of garbled bits on my second screen when my mouse is on that screen.  I tried to disable Composite, but that doesn't work.  

I'm also getting this error --->  Xlib:  extension "XFree86-DRI" missing on display ":0.0".

I upgraded to the new ATI drivers (8.30.03) and still have the same issues.  I can attach my xorg.conf if someone wants to look at it, but it's fairly basic.

thanks.
crunge

---

### Post by dploeger on 2006-11-13
Hi there!

Are there any news about this problem? I've got the same problem after upgrading from dapper to edgy...

Thanks in advance.

Regards,
Dennis

---

### Post by Rob_H on 2006-11-14
Me too. Just configured dual-head and everything looks okay except for the mouse cursor on second screen.

For what it's worth, I have DRI disabled because it doesn't work.

---

### Post by Rob_H on 2006-11-14
Well, you can kind of work around it by enabling "software cursor" support. Add the following to your device section of xorg.conf:

```
Option "SWCursor" "yes"
```
I say "kind of" because the software cursor has problems of its own: it leaves little artifacts on the screen as you move the mouse around. But overall, I find it less distracting than the big block o' color. Argh! I wish these ATI drivers would just work as advertised!

---

### Post by NorthCoast on 2006-11-14
I believe you'll get that if the monitors are set a la "Windows Extended" style (Xinerama if I remember, turn that off).  Both screens need to run at the same exact resolution for that to work right.  If the screens are set independent it will not do that.  The thing you loose is being able to drag apps between screens but you get screens that can be very different.

I had the same thing on my ATI'd laptop until I set the screens independent.

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection

```

---

### Post by Rob_H on 2006-11-14
The screens **are** independent in my case, running two separate sessions. The problem still occurs. I'm using an ATI Radeon Xpress 200M on an HP Pavilion notebook.

---

### Post by NorthCoast on 2006-11-14
So you *don't* have Xinerama on?  How about Composite Disable?
I have that plus DRI *enabled* but I have an x1400.  Not sure about your card.  Search around here for that specific card.  I'd feel better if ATI released source instead of binary only.  However it is working nicely on my Dell laptop.

---

### Post by Rob_H on 2006-11-14
> **NorthCoast said:**
> So you *don't* have Xinerama on?  How about Composite Disable?

Yes and yes. My xorg.conf looks like yours. 

There are a lot of problems with the Radeon Xpress 200M that are documented in the forums. This cursor bug is apparently another one.

---

### Post by molo on 2006-11-15
Have you confirmed that the "fglrx" module is loading?  Do "sudo lsmod | grep fglrx" in a terminal, and if you get nothing do "sudo modprobe fglrx", and then do the ctrl-alt-backspace restart of the X server.

For the record, I'm not sure if those commands above need to be sudo-ed, but it can't hurt.

---

### Post by Rob_H on 2006-11-15
Yes, the fglrx module is running. If it weren't, dual-head would not be working at all.

---

### Post by jimmyp on 2006-11-15
I've got the same problem, PLEASE help!  I have two lcd monitors, different sizes, different resolutions.  I had them working in dapper with the ati driver ok, but there was definite video slowness.  I upgraded to edgy and can't for the life of me get fglrx to work.  I followed the directions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually)
except instead of aticonfig --initial I did aticonfig --initial=dual-head

I have 2 problems:
1) the mouse cursor in my second window is a square with random garbage in it.
2) DRI isn't enabled:
$ sudo glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No

the fglrx module IS being loaded though:
$ lsmod |grep fglrx
fglrx                 413356  0 
agpgart                33456  2 fglrx,intel_agp

Please, can anyone tell me how to get this working?  I've spent so long messing with it, trying to make it work.

Here is my xorg.conf:

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "true"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection


############################################################################

the stuff below was working with the ati driver

############################################################################

Section "Screen"
	Identifier "Main Screen"
	Device     "0 ATI Technologies, Inc. Radeon R300 NG [FireGL X1]"
	Monitor    "Main DELL 2001FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "1 ATI Technologies, Inc. Radeon R300 NG [FireGL X1]"
	Monitor    "Second"
	DefaultDepth     24
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Monitor"
	Identifier   "Main DELL 2001FP"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Second"
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "0 ATI Technologies, Inc. Radeon R300 NG [FireGL X1]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "1 ATI Technologies, Inc. Radeon R300 NG [FireGL X1]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection


```

grep  'fglrx|EE|WW' Xorg.0.log :

```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x81e2c90
(II) fglrx(1): pEnt->device->identifier=0x81e2c90
(II) fglrx(0): === [atiddxPreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "FireGL X1 (R300 4E47)" (Chipset = 0x4e47)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0172)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xff8f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R300
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R300
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: a008  Serial#: 811160652
(II) fglrx(0): Year: 2003  Week: 44
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.293 greenY: 0.608
(II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
(II) fglrx(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) fglrx(0): Serial No: C06463AU0YTL
(II) fglrx(0): Monitor name: DELL 2001FP
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 160 MHz
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: CRT on secondary DAC [crt2]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: a015  Serial#: 826825037
(II) fglrx(0): Year: 2005  Week: 52
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) fglrx(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) fglrx(0): Serial No: GC8115CO1HYM
(II) fglrx(0): Monitor name: DELL E196FP
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Secondary Controller - CRT on secondary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 28 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (410, 310) mm
(--) fglrx(0): DPI set to (99, 98)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(II) fglrx(0): Xinerama extension enabled, disabling direct rendering.
(==) fglrx(0): NoDRI = YES
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(1): === [atiddxPreInit] === begin, [s]
(II) fglrx(1): PCI bus 1 card 0 func 0
(**) fglrx(1): Depth 24, (--) framebuffer bpp 32
(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(1): Default visual is TrueColor
(==) fglrx(1): RGB weight 888
(II) fglrx(1): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(1): Buffer Tiling is OFF (copy from primary)
(--) fglrx(1): Chipset: "FireGL X1 (R300 4E47)" (Chipset = 0x4e47)
(--) fglrx(1): (PciSubVendor = 0x1002, PciSubDevice = 0x0172)
(--) fglrx(1): board vendor info: original ATI graphics adapter
(--) fglrx(1): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(1): board/chipset is supported by this driver (original ATI board)
(==) fglrx(1):  PseudoColor visuals disabled
(==) fglrx(1): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(1): Center Mode is disabled 
(==) fglrx(1): TMDS coherent mode is enabled 
(II) fglrx(1): Total of 28 modes found for primary display.
(--) fglrx(1): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(1): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(1): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(1):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(1): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(1):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(1): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(1): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(1):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(1): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(1):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(1): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(1): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(1):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(1): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(1):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(1): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(1):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(1): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(1): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(1):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(1): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(1):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(1): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(1):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(1): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(1): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(1):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(1): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(1):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(1): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(1):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(1): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(1):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(1): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(1):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(1): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(1): Display dimensions: (340, 270) mm
(--) fglrx(1): DPI set to (95, 96)
(--) fglrx(1): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(1): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(1): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(1):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(1): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(1):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(1): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(1): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(1):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(1): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(1):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(1): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(1): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(1):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(1): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(1):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(1): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(1):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(1): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(1): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(1):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(1): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(1):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(1): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(1):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(1): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(1): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(1):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(1): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(1):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(1): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(1):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(1): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(1):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(1): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(1):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(1): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(1): NoAccel = NO (copy from primary screen)
(==) fglrx(1): HPV inactive
(==) fglrx(1): FSAA enabled: NO
(==) fglrx(1): FSAA Gamma enabled
(==) fglrx(1): FSAA Multisample Position is fix
(==) fglrx(1): bNoDRI = YES (copy from primary screen)
(==) fglrx(1): UseFastTLS=0
(==) fglrx(1): BlockSignalsOnLock=1
(==) fglrx(1): EnablePrivateBackZ = NO
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1600 x 6988
(WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!    *
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available    *
(WW) fglrx(1): ***********************************
(II) fglrx(1): FBADPhys: 0xf4000000 FBMappedSize: 0x04000000
(==) fglrx(1): Write-combining range (0xf4000000,0x4000000)
(II) fglrx(1): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(1): Backing store disabled
(==) fglrx(1): Silken mouse enabled
(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(1): Acceleration enabled
(II) fglrx(1): Direct rendering disabled
(==) fglrx(1): Using hardware cursor
(II) fglrx(1): Largest offscreen area available: 1280 x 7163
(EE) AIGLX: Screen 0 is not DRI capable
(EE) AIGLX: Screen 1 is not DRI capable


```

---

### Post by DerPflanz on 2006-11-20
Hey all,

I had exactly the same problem with the fglrx driver and was not able to fix it with that driver. What I did was use the open source 'radeon' driver, and that works. I cannot give you any details on the performance, DRI or 3D, as I do not use or care about that in this setting (this is my work laptop and I mainly do programming of console applications).

Below, relevant parts of my xorg.conf (note: I have no clue if the 'Xinerama' setting and the second 'Device' section are needed, but as it works now, I am not going to play more with this file):

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        Screen         "head1" LeftOf "head2"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
        Option          "Xinerama" "On"
EndSection


Section "Device"
        Identifier  "head1"
        Driver      "radeon"
        Option  "MetaModes" "1280x800-1280x1024"
        Option  "MonitorLayout" "LVDS, TMDS"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "head2"
        Driver      "radeon"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

```
Bart

---

### Post by lmandrake on 2006-11-29
> **Kinkerl said:**
> after my reboot, the mouse cursor was a total mess on the secound screen. i dont realy know how to discribe it. its just a 2 x 2 cm bock of ... pixels. i think its the area where the mousecursor is drawn on.


Seems to be an a known bug; see [http://ati.cchtml.com/show_bug.cgi?id=210](http://ati.cchtml.com/show_bug.cgi?id=210)

But sadly Ati is not willing or able to fix this issue for over a year :/ This is the bad thing with proprietary drivers.

---

### Post by DerPflanz on 2006-11-30
> Seems to be an a known bug; see [http://ati.cchtml.com/show_bug.cgi?id=210](http://ati.cchtml.com/show_bug.cgi?id=210)

Not really. The bug you referred to is about having a blind spot under the primary screen. The bug here is about having a corrupted mouse pointer (both hard- and software pointers). The followup bug (#492) is about the fact that only the cursor itself cannot go there.

The bug on the ati driver bugzilla (is ATI actually reading that?) is: [http://ati.cchtml.com/show_bug.cgi?id=544]("http://ati.cchtml.com/show_bug.cgi?id=544")

Btw: my 'radeon' driver solution didn't really work. The complete computer crashed after some time.

For me, disabling Xinerama worked for having the right, not corrupted pointer. It is still not what I wanted, but better.

---

### Post by jinnk on 2006-12-06
> **Rob_H said:**
> 
```
Option "SWCursor" "yes"
```


Looks like that SWcursor has solved my problem too, but getting a lot of relics. I don't get why it worked perfectly in Dapper and broke in Edgy?

Anyhoo, here's my xorg.conf for those who couldn't get it working. Notice I'm using the Composite extension, although a lot of people mentioned it doesn't work.

Hardware is a standard Compaq NC6000 with a Mobility Radeon 9600 M10 RV350 clone.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "ServerLayout"
	Identifier	 "Xgl"

	Screen	0 "Laptop LCD Xgl"
	Screen	1 "CRT Screen Xgl" LeftOf "Laptop LCD Xgl"

	Option	"Xinerama" "On"
	InputDevice	 "Generic Keyboard"
	InputDevice	 "Configured Mouse"
EndSection

Section "Files"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
	FontPath	"/usr/lib/X11/fonts/WinXP"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	 "1"
	Option	"XVideo"	"Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver	"keyboard"
	Option	"CoreKeyboard"
	Option	"XkbRules" "xorg"
	Option	"XkbModel" "pc104"
	Option	"XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver	"mouse"
	Option	"CorePointer"
	Option	"Device" "/dev/input/mice"
	Option	"Protocol" "ImPS/2"
	Option	"Emulate3Buttons" "true"
	Option	"ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option	"DPMS"
EndSection

Section "Monitor"
	Identifier	"CRT Monitor"
	ModelName	 "P110 P1110"
	HorizSync	 30.0 - 107.0
	VertRefresh	 48.0 - 160.0
EndSection

Section "Monitor"
	Identifier	"TFT Monitor"
	ModelName	 "FlexScan L768"
	HorizSync	 24.8 - 80.0
	VertRefresh	 50.0 - 75.0
EndSection

Section "Device"
	Identifier	"ATI fglrx"
	Driver	"fglrx"
	BusID	 "PCI:1:0:0"
	Screen	0
	Option	"KernelModuleParm"	"agplock=0"
	Option	"UseFBDev"	"true"
	Option	"UseInternalAGPGART"	"yes"
	Option	"UseFastTLS"	"2"
	Option	"BlockSignalsOnLock"	"on"
	Option	"ForceGenericCPU"	 "no"
	# === disable/enable XAA/DRI ===
	Option	"no_accel"	"no"
	Option	"no_dri"	"no"
	# === TV-out Management (doesn't appear to be used, according to Xorg.0.log ===
	Option	"NoTV"	"yes"
	# === OpenGL specific profiles/settings ===
	#Option	 "Capabilities" "0x00000000"
	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	#	will be disabled automaticaloly
	Option	"OpenGLOverlay"	 "on"
	Option	"VideoOverlay"	"off"
	#Option	 "TVStandard"	"VIDEO"
	#Option	 "TVFormat"	"PAL-G"
	Option	"EnablePrivateBackZ"	"on"
	Option	"SWcursor"	"on"
EndSection

Section "Device"
# Note: When OpenGL Overlay is enabled, Video Overlay
#	will be disabled automaticaloly
	Identifier	"ATI fglrx 2"
	Driver	"fglrx"
	BusID	 "PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier "Laptop LCD Xgl"
	Device	 "ATI fglrx"
	Monitor "Generic Monitor"
	DefaultDepth	 24
	SubSection "Display"
	Virtual	 0 432
	Depth	24
	Modes	 "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "CRT Screen Xgl"
	Device	 "ATI fglrx 2"
	Monitor "CRT Monitor"
	DefaultDepth	 24
	SubSection "Display"
	Depth	24
	Modes	 "1600x1200" "1280x1024" "1024x768"
	EndSubSection
EndSection

```

And here's the Xorg.0.log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux silico 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec	6 12:02:55 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Xgl"
(**) |-->Screen "Laptop LCD Xgl" (0)
(**) |	 |-->Monitor "Generic Monitor"
(**) |	 |-->Device "ATI fglrx"
(**) |-->Screen "CRT Screen Xgl" (1)
(**) |	 |-->Monitor "CRT Monitor"
(**) |	 |-->Device "ATI fglrx 2"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to:
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/usr/share/fonts/X11/TTF/,
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "On"
(**) Xinerama: enabled
(**) Extension "Composite" is enabled
(**) Extension "XVideo" is enabled
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
(II) PCI: 00:00:0: chip 8086,3340 card 103c,0890 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 103c,0890 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 103c,0890 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 103c,0890 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 103c,0890 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 103c,0890 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 103c,0890 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 103c,0890 rev 03 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e50 card 103c,0890 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:06:0: chip 1217,7223 card 4001,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:06:1: chip 1217,7223 card 4801,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:06:2: chip 1217,7110 card 103c,0890 rev 00 class 08,80,00 hdr 80
(II) PCI: 02:06:3: chip 1217,7223 card 5001,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:0e:0: chip 14e4,165e card 103c,0890 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	 0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	 0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	 0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	 0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	 0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	 0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	 0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	 0x90300000 - 0x903fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	 0x98000000 - 0x9fffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,12), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	 0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	 0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	 0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	 0x00004c00 - 0x00004cff (0x100) IX[B]
	[4] -1	0	 0x00005000 - 0x000050ff (0x100) IX[B]
	[5] -1	0	 0x00005400 - 0x000054ff (0x100) IX[B]
	[6] -1	0	 0x00005800 - 0x000058ff (0x100) IX[B]
	[7] -1	0	 0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	 0x90000000 - 0x902fffff (0x300000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	 0x50000000 - 0x56ffffff (0x7000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:6:0), (2,3,4), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	 0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	 0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	 0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (2:6:1), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	 0x00004800 - 0x000048ff (0x100) IX[B]
	[1] -1	0	 0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	 0x52000000 - 0x53ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (2:6:3), (2,9,12), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	 0x00005000 - 0x000050ff (0x100) IX[B]
	[1] -1	0	 0x00005400 - 0x000054ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	 0x54000000 - 0x55ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0x98000000/27, 0x90300000/16, I/O @ 0x2000/8
(II) Addressable bus resource ranges are
	[0] -1	0	 0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	 0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	 0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	 0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	 0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	 0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	 0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xb0000000 from 0xbfffffff to 0xafffffff
(II) Active PCI resource ranges:
	[0] -1	0	 0x90000000 - 0x9000ffff (0x10000) MX[B]
	[1] -1	0	 0x90180000 - 0x90180fff (0x1000) MX[B]
	[2] -1	0	 0xa0180000 - 0xa01800ff (0x100) MX[B]
	[3] -1	0	 0xa0100000 - 0xa01001ff (0x200) MX[B]
	[4] -1	0	 0x57000000 - 0x570003ff (0x400) MX[B]
	[5] -1	0	 0xa0000000 - 0xa00003ff (0x400) MX[B]
	[6] -1	0	 0xb0000000 - 0xafffffff (0x0) MX[B]O
	[7] -1	0	 0x90300000 - 0x9030ffff (0x10000) MX[B](B)
	[8] -1	0	 0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[9] -1	0	 0x00003800 - 0x0000387f (0x80) IX[B]
	[10] -1 0	 0x00003400 - 0x000034ff (0x100) IX[B]
	[11] -1 0	 0x00003880 - 0x000038bf (0x40) IX[B]
	[12] -1 0	 0x00003000 - 0x000030ff (0x100) IX[B]
	[13] -1 0	 0x00003c20 - 0x00003c2f (0x10) IX[B]
	[14] -1 0	 0x00003c00 - 0x00003c1f (0x20) IX[B]
	[15] -1 0	 0x000038e0 - 0x000038ff (0x20) IX[B]
	[16] -1 0	 0x000038c0 - 0x000038df (0x20) IX[B]
	[17] -1 0	 0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	 0x90000000 - 0x9000ffff (0x10000) MX[B]
	[1] -1	0	 0x90180000 - 0x90180fff (0x1000) MX[B]
	[2] -1	0	 0xa0180000 - 0xa01800ff (0x100) MX[B]
	[3] -1	0	 0xa0100000 - 0xa01001ff (0x200) MX[B]
	[4] -1	0	 0x57000000 - 0x570003ff (0x400) MX[B]
	[5] -1	0	 0xa0000000 - 0xa00003ff (0x400) MX[B]
	[6] -1	0	 0xb0000000 - 0xafffffff (0x0) MX[B]O
	[7] -1	0	 0x90300000 - 0x9030ffff (0x10000) MX[B](B)
	[8] -1	0	 0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[9] -1	0	 0x00003800 - 0x0000387f (0x80) IX[B]
	[10] -1 0	 0x00003400 - 0x000034ff (0x100) IX[B]
	[11] -1 0	 0x00003880 - 0x000038bf (0x40) IX[B]
	[12] -1 0	 0x00003000 - 0x000030ff (0x100) IX[B]
	[13] -1 0	 0x00003c20 - 0x00003c2f (0x10) IX[B]
	[14] -1 0	 0x00003c00 - 0x00003c1f (0x20) IX[B]
	[15] -1 0	 0x000038e0 - 0x000038ff (0x20) IX[B]
	[16] -1 0	 0x000038c0 - 0x000038df (0x20) IX[B]
	[17] -1 0	 0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	 0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	 0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	 0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	 0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	 0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	 0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	 0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	 0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	 0x90000000 - 0x9000ffff (0x10000) MX[B]
	[5] -1	0	 0x90180000 - 0x90180fff (0x1000) MX[B]
	[6] -1	0	 0xa0180000 - 0xa01800ff (0x100) MX[B]
	[7] -1	0	 0xa0100000 - 0xa01001ff (0x200) MX[B]
	[8] -1	0	 0x57000000 - 0x570003ff (0x400) MX[B]
	[9] -1	0	 0xa0000000 - 0xa00003ff (0x400) MX[B]
	[10] -1 0	 0xb0000000 - 0xafffffff (0x0) MX[B]O
	[11] -1 0	 0x90300000 - 0x9030ffff (0x10000) MX[B](B)
	[12] -1 0	 0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[13] -1 0	 0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1 0	 0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1 0	 0x00003800 - 0x0000387f (0x80) IX[B]
	[16] -1 0	 0x00003400 - 0x000034ff (0x100) IX[B]
	[17] -1 0	 0x00003880 - 0x000038bf (0x40) IX[B]
	[18] -1 0	 0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1 0	 0x00003c20 - 0x00003c2f (0x10) IX[B]
	[20] -1 0	 0x00003c00 - 0x00003c1f (0x20) IX[B]
	[21] -1 0	 0x000038e0 - 0x000038ff (0x20) IX[B]
	[22] -1 0	 0x000038c0 - 0x000038df (0x20) IX[B]
	[23] -1 0	 0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "keyboard"
(II) Loading /usr/lib/xorg/modules/input/keyboard_drv.so
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) ATI Radeon/FireGL: The following chipsets are supported:
<snip supported chipsets />
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1	 
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
(--) Chipset MOBILITY RADEON 9600/9700 (M10/M11 4E50) found
(--) Chipset MOBILITY RADEON 9600/9700 (M10/M11 4E50) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	 0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	 0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	 0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	 0x90000000 - 0x9000ffff (0x10000) MX[B]
	[5] -1	0	 0x90180000 - 0x90180fff (0x1000) MX[B]
	[6] -1	0	 0xa0180000 - 0xa01800ff (0x100) MX[B]
	[7] -1	0	 0xa0100000 - 0xa01001ff (0x200) MX[B]
	[8] -1	0	 0x57000000 - 0x570003ff (0x400) MX[B]
	[9] -1	0	 0xa0000000 - 0xa00003ff (0x400) MX[B]
	[10] -1 0	 0xb0000000 - 0xafffffff (0x0) MX[B]O
	[11] -1 0	 0x90300000 - 0x9030ffff (0x10000) MX[B](B)
	[12] -1 0	 0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[13] -1 0	 0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1 0	 0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1 0	 0x00003800 - 0x0000387f (0x80) IX[B]
	[16] -1 0	 0x00003400 - 0x000034ff (0x100) IX[B]
	[17] -1 0	 0x00003880 - 0x000038bf (0x40) IX[B]
	[18] -1 0	 0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1 0	 0x00003c20 - 0x00003c2f (0x10) IX[B]
	[20] -1 0	 0x00003c00 - 0x00003c1f (0x20) IX[B]
	[21] -1 0	 0x000038e0 - 0x000038ff (0x20) IX[B]
	[22] -1 0	 0x000038c0 - 0x000038df (0x20) IX[B]
	[23] -1 0	 0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e2dd8
(II) fglrx(1): pEnt->device->identifier=0x81e2dd8
(II) resource ranges after probing:
	[0] -1	0	 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	 0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	 0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	 0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	 0x90000000 - 0x9000ffff (0x10000) MX[B]
	[5] -1	0	 0x90180000 - 0x90180fff (0x1000) MX[B]
	[6] -1	0	 0xa0180000 - 0xa01800ff (0x100) MX[B]
	[7] -1	0	 0xa0100000 - 0xa01001ff (0x200) MX[B]
	[8] -1	0	 0x57000000 - 0x570003ff (0x400) MX[B]
	[9] -1	0	 0xa0000000 - 0xa00003ff (0x400) MX[B]
	[10] -1 0	 0xb0000000 - 0xafffffff (0x0) MX[B]O
	[11] -1 0	 0x90300000 - 0x9030ffff (0x10000) MX[B](B)
	[12] -1 0	 0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[13] 0	0	 0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	 0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	 0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1 0	 0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1 0	 0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1 0	 0x00003800 - 0x0000387f (0x80) IX[B]
	[19] -1 0	 0x00003400 - 0x000034ff (0x100) IX[B]
	[20] -1 0	 0x00003880 - 0x000038bf (0x40) IX[B]
	[21] -1 0	 0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1 0	 0x00003c20 - 0x00003c2f (0x10) IX[B]
	[23] -1 0	 0x00003c00 - 0x00003c1f (0x20) IX[B]
	[24] -1 0	 0x000038e0 - 0x000038ff (0x20) IX[B]
	[25] -1 0	 0x000038c0 - 0x000038df (0x20) IX[B]
	[26] -1 0	 0x00002000 - 0x000020ff (0x100) IX[B](B)
	[27] 0	0	 0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	 0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "SWcursor" "on"
(**) fglrx(0): Option "KernelModuleParm" "agplock=0"
(**) fglrx(0): Option "OpenGLOverlay" "on"
(**) fglrx(0): Option "VideoOverlay" "off"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
(**) fglrx(0): Option "UseFastTLS" "2"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "EnablePrivateBackZ" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON 9600/9700 (M10/M11 4E50)" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x0890)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0x98000000
(--) fglrx(0): MMIO registers at 0x90300000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 32704 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600	 
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P10 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.28.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 32768 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: CPQ	Model: 1321	Serial#: 1094006326
(II) fglrx(0): Year: 1999	Week: 27
(II) fglrx(0): EDID Version: 1.1
(II) fglrx(0): Analog Display Input,	Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:	Separate	Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40	vert.: 30
(II) fglrx(0): Gamma: 2.50
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.625 redY: 0.340	 greenX: 0.280 greenY: 0.595
(II) fglrx(0): blueX: 0.155 blueY: 0.070	 whiteX: 0.281 whiteY: 0.311
(II) fglrx(0): Supported VESA Video Modes:
<snip supported VESA modes />
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1800	vsize 1440	refresh: 60	vid: 32962
<snip supported future video modes />
(II) fglrx(0): Ranges: V min: 48	V max: 160 Hz, H min: 30	H max: 107 kHz,
(II) fglrx(0): Serial No: 927GC25KA566
(II) fglrx(0): Monitor name:	P110
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: LCD on internal LVDS
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LCD	Model: ea01	Serial#: 16843009
(II) fglrx(0): Year: 2004	Week: 13
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 29	vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.600 redY: 0.335	 greenX: 0.300 greenY: 0.540
(II) fglrx(0): blueX: 0.150 blueY: 0.135	 whiteX: 0.315 whiteY: 0.330
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1024	vsize 768	refresh: 60	vid: 16481
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 65.0 MHz	 Image Size:	287 x 215 mm
(II) fglrx(0): h_active: 1024	h_sync: 1056	h_sync_end 1192 h_blank_end 1344 h_border: 0
(II) fglrx(0): v_active: 768	v_sync: 770	v_sync_end 772 v_blanking: 806 v_border: 0
(II) fglrx(0):	TMDISPLAY
(II) fglrx(0):	LTD141EA0V
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.	3 power states available:
(II) fglrx(0):	 1. 250/196MHz @ 60Hz [enable load balancing]
(II) fglrx(0):	 2. 105/105MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):	 3. 149/105MHz @ 60Hz [enable sleep, thermal diode mode]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):	PseudoColor visuals disabled
(**) fglrx(0): OpenGL Overlay enabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 0)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"	 65.00	1024 1056 1192 1344	768 770 772 806
(**) fglrx(0):	Default mode "848x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
<snip modes/>
(--) fglrx(0): Display dimensions: (290, 210) mm
(--) fglrx(0): DPI set to (89, 92)
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"	 65.00	1024 1056 1192 1344	768 770 772 806
(**) fglrx(0):	Default mode "848x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
<snip modes/>
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(II) fglrx(0): Xinerama extension enabled, disabling direct rendering.
(**) fglrx(0): NoDRI = YES
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x00000258
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: yes
(**) fglrx(0): KernelModuleParm: "agplock=0"
(**) fglrx(0): UseFastTLS=2
(**) fglrx(0): BlockSignalsOnLock=1
(**) fglrx(0): EnablePrivateBackZ = YES
(II) fglrx(1): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules/libvgahw.so
(II) fglrx(1): PCI bus 1 card 0 func 0
(**) fglrx(1): Depth 24, (--) framebuffer bpp 32
(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(1): Default visual is TrueColor
(==) fglrx(1): RGB weight 888
(II) fglrx(1): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(1): Buffer Tiling is OFF (copy from primary)
(--) fglrx(1): Chipset: "MOBILITY RADEON 9600/9700 (M10/M11 4E50)" (Chipset = 0x4e50)
(--) fglrx(1): (PciSubVendor = 0x103c, PciSubDevice = 0x0890)
(--) fglrx(1): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(1): VideoRAM: 16384 kByte, Type: DDR SGRAM / SDRAM
(WW) fglrx(1): board is an unknown third party board, chipset is supported
(==) fglrx(1):	PseudoColor visuals disabled
(**) fglrx(1): OpenGL Overlay on 2nd Screen not implemented
(==) fglrx(1): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(1): Center Mode is disabled 
(==) fglrx(1): TMDS coherent mode is enabled 
(II) fglrx(1): Total of 52 modes found for primary display.
(--) fglrx(1): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(1): *Mode "1600x1200": 229.5 MHz (scaled from 0.0 MHz), 106.2 kHz, 85.0 Hzz
<snip modes/>
(--) fglrx(1): Display dimensions: (400, 300) mm
(--) fglrx(1): DPI set to (101, 101)
(--) fglrx(1): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(1): *Mode "1600x1200": 229.5 MHz (scaled from 0.0 MHz), 106.2 kHz, 85.0 Hz
<snip modes/>
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(==) fglrx(1): NoAccel = NO (copy from primary screen)
(==) fglrx(1): HPV inactive
(==) fglrx(1): FSAA enabled: NO
(==) fglrx(1): FSAA Gamma enabled
(==) fglrx(1): FSAA Multisample Position is fix
(==) fglrx(1): bNoDRI = YES (copy from primary screen)
(**) fglrx(1): UseFastTLS=2
(**) fglrx(1): BlockSignalsOnLock=1
(**) fglrx(1): EnablePrivateBackZ = YES
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?	Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	 0	 0x90300000 - 0x9030ffff (0x10000) MX[B]
	[1] 0	 0	 0x98000000 - 0x9fffffff (0x8000000) MX[B]
	[2] 0	 0	 0x90300000 - 0x9030ffff (0x10000) MX[B]
	[3] 0	 0	 0x98000000 - 0x9fffffff (0x8000000) MX[B]
	[4] -1	0	 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	 0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	 0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	 0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	 0x90000000 - 0x9000ffff (0x10000) MX[B]
	[9] -1	0	 0x90180000 - 0x90180fff (0x1000) MX[B]
	[10] -1 0	 0xa0180000 - 0xa01800ff (0x100) MX[B]
	[11] -1 0	 0xa0100000 - 0xa01001ff (0x200) MX[B]
	[12] -1 0	 0x57000000 - 0x570003ff (0x400) MX[B]
	[13] -1 0	 0xa0000000 - 0xa00003ff (0x400) MX[B]
	[14] -1 0	 0xb0000000 - 0xafffffff (0x0) MX[B]O
	[15] -1 0	 0x90300000 - 0x9030ffff (0x10000) MX[B](B)
	[16] -1 0	 0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[17] 0	0	 0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	 0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	 0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	 0x00002000 - 0x000020ff (0x100) IX[B]
	[21] 0	0	 0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1 0	 0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1 0	 0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1 0	 0x00003800 - 0x0000387f (0x80) IX[B]
	[25] -1 0	 0x00003400 - 0x000034ff (0x100) IX[B]
	[26] -1 0	 0x00003880 - 0x000038bf (0x40) IX[B]
	[27] -1 0	 0x00003000 - 0x000030ff (0x100) IX[B]
	[28] -1 0	 0x00003c20 - 0x00003c2f (0x10) IX[B]
	[29] -1 0	 0x00003c00 - 0x00003c1f (0x20) IX[B]
	[30] -1 0	 0x000038e0 - 0x000038ff (0x20) IX[B]
	[31] -1 0	 0x000038c0 - 0x000038df (0x20) IX[B]
	[32] -1 0	 0x00002000 - 0x000020ff (0x100) IX[B](B)
	[33] 0	0	 0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	 0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!	*
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available	*
(WW) fglrx(0): ***********************************
(II) fglrx(0): FBADPhys: 0x98000000 FBMappedSize: 0x01000000
(==) fglrx(0): Write-combining range (0x98000000,0x1000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,4096)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(WW) fglrx(0): Option "NoTV" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
	32 128x128 slots
	20 256x256 slots
	6 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(**) fglrx(0): Using software cursor
(II) fglrx(0): Largest offscreen area available: 1024 x 3328
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!	*
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available	*
(WW) fglrx(1): ***********************************
(II) fglrx(1): FBADPhys: 0x99000000 FBMappedSize: 0x01000000
(==) fglrx(1): Write-combining range (0x99000000,0x1000000)
(II) fglrx(1): FBMM initialized for area (0,0)-(1600,2621)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(1): Backing store disabled
(==) fglrx(1): Silken mouse enabled
(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
	32 128x128 slots
	9 256x256 slots
	4 512x512 slots
(II) fglrx(1): Acceleration enabled
(II) fglrx(1): Direct rendering disabled
(**) fglrx(1): Using software cursor
(II) fglrx(1): Largest offscreen area available: 1600 x 1421
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(EE) AIGLX: Screen 1 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
	xkb_keycodes	 { include "xfree86+aliases(qwerty)" };
	xkb_types	{ include "complete" };
	xkb_compatibility	{ include "complete" };
	xkb_symbols	{ include "pc(pc104)+us" };
	xkb_geometry	 { include "pc(pc104)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

---

### Post by jinnk on 2006-12-06
Just disabled the fglrx module and enabled the radeon driver (open source).  It's noticably faster & doesn't appear to have any strange behaviour.  If you have this mouse problem I would say forget about the fglrx for now.

---

### Post by kEinstein on 2006-12-15
Hi there,

'EddM' made a complete reset of xorg.conf - also using the latest driver from ATI's homepage and SOLVED the issue!?
However, it didn't work for me. 
Probably, you might want to give it a try - click [here]("http://ubuntuforums.org/showthread.php?t=314162")!

In short:
> I used 'fglrx' drivers from ATI's official homepage (v.8.32.5) to enhance additional capability (e.g. mode switching via FN + F7)
> did
```
$ aticonfig --initial=dual-head --screen-layout=right
``` 
> xorg.conf: made some adjustment - but basically, it looked fine
> primary monitor works fine, except for the mouse (a [bar of garbage]("http://www.ubuntuforums.org/showthread.php?t=284750") below the cursor)
> secondary monitor works fine, except for the mouse (the entire cursor is a box of shredded graphics)

Primary monitor: internal @1400x1050
Secondary monitor: external @1680x1050


EDIT #1:
no xinerama used in my case

EDIT #2:
the problem arises regardless of screen resolution of my external monitor (tested 1920x1200, 1600x1200, 1680x1050, 1400x1050)

---

### Post by kEinstein on 2006-12-15
Found some additional information on [ThinkWiki.org]("http://ThinkWiki.org"). The issue is quite well known and 2 further possible solutions are quoted there:
You can browse to the original entry by clicking [here]("http://thinkwiki.org/wiki/Problems_with_fglrx#Line_Appears_Below_Mouse_Cursor").

1) Method No.1 is a workaround: disable the DGA extension in your Xorg or Xfree86 config by adding the following lines in your 'module section'
```
Load "extmod"
```

with

```

SubSection  "extmod"
Option  "omit XFree86-DGA"
EndSubSection
```


2) The second method requires patching fglrx together with your kernel. Refer to [this page]("http://thinkwiki.org/wiki/Problems_with_fglrx#fglrx_8.32.5") directly to obtain further details.


Well, it's quite late and I prefer going to bed for today, starting a final attempt with implementing these findings tomorrow.
In fact, the dodgy appearence of my mouse is so annoying that I temporarily switched back to Ubuntu's 'ati' driver (which still works perfectly by simply substituting the 'fglrx' entries in xorg.conf).

---

### Post by kEinstein on 2006-12-16
Update. 

Method 1: doesn't work for me

Method 2: didn't work for me either. If you know exactly what you are about to do, this might work for you. I used [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") - if you are using Edgy click [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").

Last 2 hours:
> messed around with kernel patches
> built my own deb packages
> installed them
> reconfigured Xorg
> restarted
> screwed X in combination with applying kernel patches
> restoring backups didn't work
> ...
> cried out loud
> ...

Current status:
> upgrading to Edgy

---

### Post by kEinstein on 2006-12-16
DID IT!!! No corrupted mouse cursor on dual-head incl. 3D support.
After upgrading to Edgy, I switched to fglrx - as before. Again, setting up dual-head support worked smoothly with my X300 and Xorg.

I decided to postpone the issue with a corrputed mouse cursor, at least I wanted 3D support properly installed on my new Edgy:
Found the [following thread]("http://ubuntuforums.org/showthread.php?t=273934") about a successful installation of fglrx on Edgy.

The core part of the story:
As suggested in the thread, I added fglrx to /etc/modules in a separate line:
```
$ sudo gedit /etc/modules
```

After establishing a link for DRI ...
```
$ sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```
... and restarting X, there it was:
**a CRYSTAL CLEAR mouse cursor on BOTH screens** using dual-head, 'fglrx' and ATI's proprietary 3D acceleration.

[CENTER]*"Das also ist des Pudels wahrer Kern!"*
[SIZE="1"](from Goethe's Faust)[/SIZE][/CENTER]

Give it a try and post your results! I hope this helps...

---

### Post by I_want_to_write on 2006-12-31
Right, lots of trial and error and it finally worked (i'll make sure my next computer doesnt have ati display)... I dont know what I did right or wrong... I think it was disabling the composite that got it working, or it could be a combination of lots of things. 

I have another challenge to you :twisted: 

I have the dual-head working but if i enable xinerama mode, the mouse goes "square shaped" again. 

Any ideas on xinerama? 

I like having two individual screens but drag and drop from one monitor to the other would be nice too... 

PS: how do you get glxgears to display the results?

PS2: glxgears -printfps

PS3: WOW, dri made big difference. glxgears gives me 3 times the performance I used to get without it..

---

### Post by PseudoRandom on 2006-12-31
Like kEinstein above, [**this thread**]("http://ubuntuforums.org/showthread.php?t=273934") solved my problem with the cursor, but it was a different part of the solution that worked. 

My short version is this: if you install a new binary driver from ATI, make sure you put the DISABLED_MODULES="fglrx" line into /etc/default/linux-restricted-modules-common; if you don't, then X and the kernel load incompatible modules, the cursor will be teh broked, and you'll see warnings in your /var/log/Xorg.0.log ('grep WW /var/log/Xorg.0.log' is helpful). 

(You could also remove the restricted-modules packages, but when I tried that it broke my WLAN ... and that's a whole 'nother story.)

---

### Post by kEinstein on 2007-01-03
> **I_want_to_write said:**
> 
[...]
I have the dual-head working but if i enable xinerama mode, the mouse goes "square shaped" again. 

Any ideas on xinerama? 

I like having two individual screens but drag and drop from one monitor to the other would be nice too... 
[...]

Xinerama... I recognized the same problem, however I have a few suggestions at hand :D 

1) You might want to use BigDesktop instead of Xinerama!? It gives you additional 3D support and has less issues than the latter. See [here for a quick, yet detailed, guide.]("http://www.ubuntuforums.org/showthread.php?t=301941")

2) Have you tried to specify the HorizSync and VertRefresh Rates in your xorg.conf for both display? I came across [a suggestion]("http://www.ubuntuforums.org/showthread.php?t=227902&highlight=xinerama+cursor") that this might solve the issue (admittedly, it didn't work for me - but I'm trying to capture ALL possibilities mentioned throughout different threads)

3) Use 'ati' or 'radeon' drivers (again no 3D support, known draw-backs)  and switch to MergedFB, [see here.]("http://www.ubuntuforums.org/showthread.php?p=1773710")

4) Do the same thing I'm going to do: be patient. I'm sorry, no further ideas & suggestions this time. 

For a list of driver-specific features see [Ziox Guide on Dual-Head capabilites.]("http://ubuntuforums.org/showthread.php?t=221174&highlight=xinerama")

---

### Post by nyab on 2007-03-09
I had the same problem on my desktop with an ATI 9600 no xinerama.
I followed all the advices posted here with no luck.

After some head scratching it appeared that I didn't have the restricted modules installed in the first place.
So if still have troubles with the annoying squary mouse, try this:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed

It won't hurt anyways as you are supposed to have those with fglrx

---

### Post by sirwalken on 2007-08-08
hi i also have a ati tv wonder that i installed, 
and since i get a blurry square, or i cant see what i'm doing
 until i rotate the model, or zoom around a little.
( i work in 3d )the tv wonder sucks so if i uninstall it and reinstall nividea...?
(that probably won't work, i already uninstalled it and it begged me for 
the "pleases insert ati t.v. wonder remote disk wonder wonder" 
every four minutes until i hunted the hidden process down like a dog.)
that should be a capital offense! 
there should be youtube videos of  "this guy created a very annoying computer bug"
and the video should be a guy strung up by his nuts!
i'm going to give the tv wonder to an enemy i have :)
graaagghhh! 
here you can see the square bit, i selected the head area and moved the dragon,
but it retains the area under the "first click".
i found an ati page that gives the solutions hopefully, but its from 2002...
[http://www.xlr8yourmac.com/Graphics/ati_oct_2002_driver_update.html]("http://www.xlr8yourmac.com/Graphics/ati_oct_2002_driver_update.html")
maybe i was a little harsh. i'm going to try and uninstall again,
 it cant be **that** wormed into my graphics system,
 its just a t.v. tuner for christs sake!
my t.v. tuner is running my videogames now?
(edit: i uninstalled the thing and everythings working sweet again! 
ahhhhhhhh. i was pretty worried there for a bit.

---

