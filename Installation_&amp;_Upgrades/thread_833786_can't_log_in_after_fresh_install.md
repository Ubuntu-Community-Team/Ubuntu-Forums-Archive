---
title: "can't log in after fresh install"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by crashhipp on 2008-06-18
I just installed 8.04 on this 
emachines t6524
AMD Athlon 64
2.20 Ghz
200 mhz fsb
512 mb l2 chache,
200 GB ATA Hard Drive
ATI Radeon xpress 200

the install went fine but, when i type the username and password screen it fails to log in every time and just returns to the user name. 
I checked the CAPS lock. 
Reinstalled to ensure I didn't fat finger the username/password. 

I want to start experiencing linux but i'm stuck.

I'm a total rookie.

---

### Post by PmDematagoda on 2008-06-19
Post the outputs of:-
```
cat ~/.xsession-errors
```
and
```
cat /var/log/Xorg.0.log
```

---

### Post by crashhipp on 2008-06-19
ah - could you please tell me how to get the logs you are asking about

---

### Post by Sef on 2008-06-19
> ah - could you please tell me how to get the logs you are asking about

Applications > Accessories > Terminal

then type or copy and paste the codes from post #2:

```
cat ~/.xsession-errors
```

then type or copy and paste again:

```
cat /var/log/Xorg.0.log
```

Copy and paste each code here.

---

### Post by crashhipp on 2008-06-19
yes but there is no Applications > Accessories > Terminal at the screen I'm at during the log on process. it just gives me 
restart
hibernate
shut down

and a couple other options

---

### Post by PmDematagoda on 2008-06-19
Once you reach the login screen, try and login through GNOME Fail-Safe by selecting that option in Options>Sessions in the login screen.

---

### Post by crashhipp on 2008-06-19
Im on a screen that only has options in the lower left 
Select Language
Select Session
Remote Login Via XCMCP...

Restart
Shut down
etc...

---

### Post by crashhipp on 2008-06-19
cat ~/.xsession-errors

mhipp@ubuntu-emachines:~$ cat ~/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/ubuntu-emachines:/tmp/.ICE-unix/6087
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
seahorse nautilus module initialized
Initializing nautilus-share extension
Detected PCI ID for VGA: 01:05.0 0300: 1002:5954 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority

** (nautilus:6225): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6225): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6225): WARNING **: Can not get _NET_WORKAREA

** (nautilus:6225): WARNING **: Can not determine workarea, guessing at layout
starting HAL detection for ac adaptors...11
evolution-alarm-notify-Message: Setting timeout for 54153 1213920000 1213865847
evolution-alarm-notify-Message:  Thu Jun 19 18:00:00 2008

evolution-alarm-notify-Message:  Thu Jun 19 02:57:27 2008

none found
Throttle level is 0

** (nautilus:6225): WARNING **: Unable to add monitor: Not supported
XIO:  fatal IO error 0 (Success) on X server ":0.0"
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 12 requests (12 known processed) with 0 events remaining.
      after 1585 requests (1578 known processed) with 1 events remaining.

---

### Post by crashhipp on 2008-06-19
cat /var/log/Xorg.0.log

best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 22
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x3fff3800 is: 0x3fff3800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x41ff4000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x41ff4000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1026)
(II) RADEON(0): Using hardware cursor 1 (scanline 1030)
(II) RADEON(0): Largest offscreen area available: 1024 x 7157
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 304 x 228
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: EMA  Model: 61c  Serial#: 3797
(II) RADEON(0): Year: 2005  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
(II) RADEON(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Monitor name: e15t4
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) RADEON(0): Serial No: 35B 50V 03797
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0015a11c06d50e0000
(II) RADEON(0): 	2d0f0103081e1789ea71d6a256499624
(II) RADEON(0): 	134f54afce0001010101010101010101
(II) RADEON(0): 	010101010101c31e0020410020301060
(II) RADEON(0): 	130030e410000018000000fc00653135
(II) RADEON(0): 	74340a20202020202020000000fd0038
(II) RADEON(0): 	4c1e3c08000a202020202020000000ff
(II) RADEON(0): 	003335422035305620303337393700d1
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: EMA  Model: 61c  Serial#: 3797
(II) RADEON(0): Year: 2005  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
(II) RADEON(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Monitor name: e15t4
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) RADEON(0): Serial No: 35B 50V 03797
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0015a11c06d50e0000
(II) RADEON(0): 	2d0f0103081e1789ea71d6a256499624
(II) RADEON(0): 	134f54afce0001010101010101010101
(II) RADEON(0): 	010101010101c31e0020410020301060
(II) RADEON(0): 	130030e410000018000000fc00653135
(II) RADEON(0): 	74340a20202020202020000000fd0038
(II) RADEON(0): 	4c1e3c08000a202020202020000000ff
(II) RADEON(0): 	003335422035305620303337393700d1
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: EMA  Model: 61c  Serial#: 3797
(II) RADEON(0): Year: 2005  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
(II) RADEON(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Monitor name: e15t4
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) RADEON(0): Serial No: 35B 50V 03797
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0015a11c06d50e0000
(II) RADEON(0): 	2d0f0103081e1789ea71d6a256499624
(II) RADEON(0): 	134f54afce0001010101010101010101
(II) RADEON(0): 	010101010101c31e0020410020301060
(II) RADEON(0): 	130030e410000018000000fc00653135
(II) RADEON(0): 	74340a20202020202020000000fd0038
(II) RADEON(0): 	4c1e3c08000a202020202020000000ff
(II) RADEON(0): 	003335422035305620303337393700d1
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: EMA  Model: 61c  Serial#: 3797
(II) RADEON(0): Year: 2005  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
(II) RADEON(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Monitor name: e15t4
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) RADEON(0): Serial No: 35B 50V 03797
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0015a11c06d50e0000
(II) RADEON(0): 	2d0f0103081e1789ea71d6a256499624
(II) RADEON(0): 	134f54afce0001010101010101010101
(II) RADEON(0): 	010101010101c31e0020410020301060
(II) RADEON(0): 	130030e410000018000000fc00653135
(II) RADEON(0): 	74340a20202020202020000000fd0038
(II) RADEON(0): 	4c1e3c08000a202020202020000000ff
(II) RADEON(0): 	003335422035305620303337393700d1
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): EDID vendor "EMA", prod id 1564
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: EMA  Model: 61c  Serial#: 3797
(II) RADEON(0): Year: 2005  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
(II) RADEON(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Monitor name: e15t4
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) RADEON(0): Serial No: 35B 50V 03797
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0015a11c06d50e0000
(II) RADEON(0): 	2d0f0103081e1789ea71d6a256499624
(II) RADEON(0): 	134f54afce0001010101010101010101
(II) RADEON(0): 	010101010101c31e0020410020301060
(II) RADEON(0): 	130030e410000018000000fc00653135
(II) RADEON(0): 	74340a20202020202020000000fd0038
(II) RADEON(0): 	4c1e3c08000a202020202020000000ff
(II) RADEON(0): 	003335422035305620303337393700d1
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "EMA", prod id 1564

---

### Post by PmDematagoda on 2008-06-19
> **crashhipp said:**
> Im on a screen that only has options in the lower left 
Select Language
Select Session
Remote Login Via XCMCP...

Restart
Shut down
etc...
It's select session, and there doesn't seem to be anything wrong with the X-Server directly, it seems to be more a GNOME problem, so try and login through fail-safe.

---

### Post by crashhipp on 2008-06-19
are you suggesting that I log into failsafe  mode each time?

I created a new user name and password with in failsafe mode and those credentials failed upon log on too. 

Any thing else I should try? Hardware issues?

---

