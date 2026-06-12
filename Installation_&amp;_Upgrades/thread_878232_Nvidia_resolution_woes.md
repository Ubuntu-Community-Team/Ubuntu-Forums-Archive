---
title: "Nvidia resolution woes"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by metafractal on 2008-08-02
I have read ten or more threads about this problem already but they have not helped. My problem seems to be different. Please read on.

I have a laptop with a GeForce Go video card. I did a fresh install of Hardy and tried to install the Nvidia drivers through the restricted drivers menu; this did not work and the system reverted back to 640x480 resolution. I uninstalled these drivers and then tried using envy. The screen was still in 640x480 mode but after fiddling with my xorg.conf file I was able to get it to let me change to my desired resolution (1440x900). If I run nvidia-settings as root I can save this to my xorg.conf file. However, when I  reboot, the resolution goes back to 640x480 after I log in (interestingly, the resolution is correct at the login screen). I have to go into nvidia-settings each time I boot to change back to my desired resolution.

Examining the X11 log file reveals that the nvidia drivers are being loaded  without a problem, but at the very last stage (i.e. the last line of the log file) the resolution gets set to 640x480. What's really strange is that if I edit the xorg.conf file or play around with the nvidia-settings tab to force it to boot into 1440x900, I see that it does go into 1440x900 first but then CHANGES BACK to 640x480 right at the end (as recorded by the last line of the log file).

I should also mention that something seems to be messing with my xorg.conf file - If I edit it by hand and save it, it is different the next time I log in.

Any ideas?

Thanks.

---

### Post by redraiderbum on 2008-08-02
Have you tried going to system->administration->display or something similar and change the resolution to your desired resolution.  This rarely works for me, but it's worth a shot.

If that doesn't work try editing the xorg.conf file yourself. 
 
Do this:

> sudo gedit /etc/X11/xorg.conf

Go down to the display section and you will see a listing for various 'depths' those are the depth of the colors.  You want the depth that has the highest number (it is probably at the bottom of the display section with depth of 32).  Next to this depth there will be various 'Modes' which are the possible resolutions.  If you just delete all of them except "1440x900" it will force the computer into that resolution.

---

### Post by metafractal on 2008-08-02
Yes, as I mentioned above I have tried editing the xorg.conf file myself. If I do this, then X will go into 1440x900 first and then revert back to 640x480! It goes into 640x480 even when there is no such "mode" in the xorg.conf file.

The xorg.conf file also changes after each re-boot, something is writing to it but I don't know what.

---

### Post by redraiderbum on 2008-08-02
I do remember having problems similar to this on previous version, but I have forgotten now how to fix them.  The nvidia console has always done that exact thing for me.  Do you know if the 'gefore go' are supported by the new nvidia driver or if you have to install the legacy nvidia driver.

Just for clarity you have checked the restricted drivers in the administration section to make sure you are, in fact, using the driver right?

If you install again I wouldn't install all of the nvidia tools unless you need them.  It is probably rewriting you xorg.conf file each time you reboot.  I would only install the restricted driver with none of the add on tools from nvidia.

---

### Post by metafractal on 2008-08-02
I have just tried installing the drivers directly from the nvidia website. Everything seemed to work but I still have the same problem. I'm stumped. Attached is my xorg.conf file. Here is the text of the logfile. As you can see, it goes into the right resolution and then switches back to the wrong one. 

What can I do? If you look at my xorg.conf file, you'll see that it shouldn't be able to go into 640x480 mode at all!
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux joshua-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  3 01:24:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f0 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0244 card 103c,30b7 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 103c,30b7 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 103c,30b7 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 103c,30b7 rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 103c,30b7 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 103c,30b7 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card f03c,30b7 rev f1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 103c,30b7 rev f1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 103c,30b7 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 103c,30b7 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 14e4,4311 card 103c,1374 rev 02 class 02,80,00 hdr 00
(II) PCI: 07:05:0: chip 1180,0832 card 103c,30b7 rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:05:1: chip 1180,0822 card 103c,30b7 rev 19 class 08,05,00 hdr 80
(II) PCI: 07:05:2: chip 1180,0592 card 103c,30b7 rev 0a class 08,80,00 hdr 80
(II) PCI: 07:05:3: chip 1180,0852 card 103c,30b7 rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb4000000 - 0xb5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xb6000000 - 0xb7ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:16:0), (0,7,7), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xb8000000 - 0xb80fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51 [Geforce 6150 Go] rev 162, Mem @ 0xb2000000/24, 0xc0000000/28, 0xb1000000/24
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xb0040000/18
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
(II) Active PCI resource ranges:
	[0] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[1] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[2] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[3] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[4] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[5] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[6] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[7] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[8] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[9] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[10] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[11] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[15] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[16] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[17] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[18] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[19] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[20] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[21] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[22] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[23] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[1] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[2] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[3] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[4] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[5] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[6] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[7] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[8] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[9] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[10] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[11] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[15] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[16] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[17] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[18] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[19] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[20] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[21] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[22] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[23] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
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
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[9] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[12] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[13] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[14] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[15] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[21] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[22] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[23] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[24] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[25] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[26] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[27] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[28] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[29] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.12  Thu Jul 17 18:36:30 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  173.14.12  Thu Jul 17 18:18:16 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(--) Assigning device section with no busID to primary device
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[9] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[12] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[13] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[14] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[15] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[21] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[22] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[23] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[24] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[25] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[26] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[27] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[28] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[29] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[9] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[12] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[13] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[14] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[15] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[24] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[25] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[26] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[27] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[28] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[29] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[30] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[31] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[32] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.53.15
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 6150 at PCI:0:5:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0): LPL (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[9] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[12] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[13] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[14] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[15] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[24] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[25] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[26] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[27] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[28] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[29] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[30] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[31] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[32] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "1440x900+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "640x480"

```

---

### Post by redraiderbum on 2008-08-02
Yeah I'm thinking what happened when you installed the nvidia console tools it stopped using the xorg.conf file.  I think if you uninstall them from synaptic altogether it may work.  I would uninstall all nvidia stuff and just install the driver by itself.

---

### Post by metafractal on 2008-08-03
Solved! I post this as a courtesy for all others who are having nvidia woes with hardy.

I think what was happening was that nvidia was trying to automatically determine the compatible refresh rate frequencies for my screen, did so *wrongly* and thus falsely determined that it couldn't go into 1440x900 when in fact it could.

I fixed the problem by adding
    Option         "UseEdidFreqs" "false"
under the "Screen" section of xorg.conf.

Ciao!

---

