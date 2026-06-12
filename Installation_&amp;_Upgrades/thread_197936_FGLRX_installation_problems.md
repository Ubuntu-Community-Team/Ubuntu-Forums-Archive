---
title: "FGLRX installation problems"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by pachequin on 2006-06-16
Hi everyone I'm a little bit frustrated, I tried to install the fglrx driver on my laptop with an ATI 9000 Mobility card but I still have this errors:

>fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

>glxinfo
name of display: :0.0
display: :0 screen: 0
direct rendering: No

>dmesg | grep fglrx
[17179590.924000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[17179590.924000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179628.176000] [fglrx:firegl_init_mask_ram] *ERROR* maskram_type not detected
[17179628.176000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179628.176000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179628.176000] [fglrx] AGP detected, AgpState = 0x1f00021b (hardware caps of chipset)
[17179628.176000] [fglrx] AGP enabled, AgpCommand = 0x1f000312 (selected caps)
[17179628.188000] [fglrx] total GART = 33554432
[17179628.188000] [fglrx] free GART = 17559552
[17179628.188000] [fglrx] max single GART = 17559552
[17179628.188000] [fglrx] total LFB = 58814464
[17179628.188000] [fglrx] free LFB = 50622464
[17179628.188000] [fglrx] max single LFB = 50622464
[17179628.188000] [fglrx] total Inv = 0
[17179628.188000] [fglrx] free Inv = 0
[17179628.188000] [fglrx] max single Inv = 0
[17179628.188000] [fglrx] total TIM = 0

>lsmod | grep fglrx
fglrx 391756 8
agpgart 36784 2 fglrx,ati_agp

&&&&&&&&&&&&&&&&&&
I had some errors eon /var/log/Xorg.0.log
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports
drmOpenDevice: node name is /dev/dri/card1 < --- REPEATED 254 TIMES
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)

%%%%%%%%%%%%%%%%%%

and after:
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
Screen to screen bit blits
Solid filled rectangles
8x8 mono pattern filled rectangles
Solid Lines
Dashed Lines
Offscreen Pixmaps
Setting up tile and stipple cache:
30 128x128 slots
(II) fglrx(0): Acceleration enabled <----- ???????
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled <------ ??????
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 410

I attach my xorg.conf file I hope that someone help me, thank you in advance.

---

### Post by rfrey74 on 2006-06-16
I did this on Ubuntu 5.10, but after upgrading to 6.06, this configuration worked just fine.  Hopefully, it will help you.

ATI FGLRX 3D Acceleration on Ubuntu 5.10

$ sudo apt-get install linux-686  #this is if you have a AMD processor
$ sudo apt-get install xorg-driver-fglrx

The next line appends fglrx to the end of the /etc/modules file.
$ echo fglrx | sudo tee -a /etc/modules
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg-<date>.conf
$ sudo gedit /etc/X11/xorg.conf

Scroll to the "Device" section
Change the value of the Driver key from "ati" to "fglrx"
Add the following options at the end of the section
Option	"VideoOverlay"		"on"
Option	"OpenGLOverlay"	"off"

$ sudo shutdown -r now

---

