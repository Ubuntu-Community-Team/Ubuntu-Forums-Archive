---
title: "Upgraded to 10.10: X won't start (Intel graphics)"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by GavinP on 2010-10-12
I have just upgraded and now X won't start and remove xorg.conf etc doesn't fix it...

This is a nettop with standard Intel graphics - no NVidia chipset (inc Ion).

This machine has been upgraded through various versions so I suspect there may be an old file somewhere which is causing this.

This is what is shown in the log - any pointers appreciated:

[  1211.411] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  1211.411] X Protocol Version 11, Revision 0
[  1211.411] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  1211.411] Current Operating System: Linux small1 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[  1211.412] Kernel command line: root=UUID=3995bbc3-c299-467a-8b54-308f6fca76ac ro quiet splash vga=775 
[  1211.412] Build Date: 16 September 2010  05:39:22PM
[  1211.412] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1211.412] Current version of pixman: 0.18.4
[  1211.412] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  1211.412] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1211.413] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 12 07:21:43 2010
[  1211.413] (II) Loader magic: 0x81f8e00
[  1211.413] (II) Module ABI versions:
[  1211.413] 	X.Org ANSI C Emulation: 0.4
[  1211.413] 	X.Org Video Driver: 8.0
[  1211.413] 	X.Org XInput driver : 11.0
[  1211.414] 	X.Org Server Extension : 4.0
[  1211.415] (--) PCI:*(0:0:2:0) 8086:2772:105b:0d4d rev 2, Mem @ 0x7f900000/524288, 0xd0000000/268435456, 0x7f980000/262144, I/O @ 0x0000ec00/8
[  1211.415] (==) Using default built-in configuration (30 lines)
[  1211.415] (==) --- Start of built-in configuration ---
[  1211.415] 	Section "Device"
[  1211.415] 		Identifier	"Builtin Default intel Device 0"
[  1211.415] 		Driver	"intel"
[  1211.415] 	EndSection
[  1211.415] 	Section "Screen"
[  1211.415] 		Identifier	"Builtin Default intel Screen 0"
[  1211.415] 		Device	"Builtin Default intel Device 0"
[  1211.415] 	EndSection
[  1211.415] 	Section "Device"
[  1211.416] 		Identifier	"Builtin Default vesa Device 0"
[  1211.416] 		Driver	"vesa"
[  1211.416] 	EndSection
[  1211.416] 	Section "Screen"
[  1211.416] 		Identifier	"Builtin Default vesa Screen 0"
[  1211.416] 		Device	"Builtin Default vesa Device 0"
[  1211.416] 	EndSection
[  1211.416] 	Section "Device"
[  1211.416] 		Identifier	"Builtin Default fbdev Device 0"
[  1211.416] 		Driver	"fbdev"
[  1211.416] 	EndSection
[  1211.416] 	Section "Screen"
[  1211.416] 		Identifier	"Builtin Default fbdev Screen 0"
[  1211.416] 		Device	"Builtin Default fbdev Device 0"
[  1211.416] 	EndSection
[  1211.416] 	Section "ServerLayout"
[  1211.416] 		Identifier	"Builtin Default Layout"
[  1211.416] 		Screen	"Builtin Default intel Screen 0"
[  1211.416] 		Screen	"Builtin Default vesa Screen 0"
[  1211.416] 		Screen	"Builtin Default fbdev Screen 0"
[  1211.416] 	EndSection
[  1211.416] (==) --- End of built-in configuration ---
[  1211.416] (==) ServerLayout "Builtin Default Layout"
[  1211.416] (**) |-->Screen "Builtin Default intel Screen 0" (0)
[  1211.416] (**) |   |-->Monitor "<default monitor>"
[  1211.417] (**) |   |-->Device "Builtin Default intel Device 0"
[  1211.417] (==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
[  1211.417] (**) |-->Screen "Builtin Default vesa Screen 0" (1)
[  1211.417] (**) |   |-->Monitor "<default monitor>"
[  1211.418] (**) |   |-->Device "Builtin Default vesa Device 0"
[  1211.418] (==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
[  1211.418] (**) |-->Screen "Builtin Default fbdev Screen 0" (2)
[  1211.418] (**) |   |-->Monitor "<default monitor>"
[  1211.418] (**) |   |-->Device "Builtin Default fbdev Device 0"
[  1211.419] (==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
[  1211.419] (==) Automatically adding devices
[  1211.419] (==) Automatically enabling devices
[  1211.419] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1211.419] 	Entry deleted from font path.
[  1211.419] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1211.419] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1211.419] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1211.419] (II) Open ACPI successful (/var/run/acpid.socket)
[  1211.419] (II) LoadModule: "extmod"
[  1211.421] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1211.421] (II) Module extmod: vendor="X.Org Foundation"
[  1211.421] 	compiled for 1.9.0, module version = 1.0.0
[  1211.421] 	Module class: X.Org Server Extension
[  1211.421] 	ABI class: X.Org Server Extension, version 4.0
[  1211.421] (II) Loading extension MIT-SCREEN-SAVER
[  1211.421] (II) Loading extension XFree86-VidModeExtension
[  1211.421] (II) Loading extension XFree86-DGA
[  1211.421] (II) Loading extension DPMS
[  1211.421] (II) Loading extension XVideo
[  1211.421] (II) Loading extension XVideo-MotionCompensation
[  1211.421] (II) Loading extension X-Resource
[  1211.421] (II) LoadModule: "dbe"
[  1211.422] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1211.422] (II) Module dbe: vendor="X.Org Foundation"
[  1211.422] 	compiled for 1.9.0, module version = 1.0.0
[  1211.422] 	Module class: X.Org Server Extension
[  1211.422] 	ABI class: X.Org Server Extension, version 4.0
[  1211.422] (II) Loading extension DOUBLE-BUFFER
[  1211.422] (II) LoadModule: "glx"
[  1211.423] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1211.423] (II) Module glx: vendor="X.Org Foundation"
[  1211.423] 	compiled for 1.9.0, module version = 1.0.0
[  1211.423] 	ABI class: X.Org Server Extension, version 4.0
[  1211.423] (==) AIGLX enabled
[  1211.423] (II) Loading extension GLX
[  1211.423] (II) LoadModule: "record"
[  1211.424] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1211.424] (II) Module record: vendor="X.Org Foundation"
[  1211.424] 	compiled for 1.9.0, module version = 1.13.0
[  1211.424] 	Module class: X.Org Server Extension
[  1211.424] 	ABI class: X.Org Server Extension, version 4.0
[  1211.424] (II) Loading extension RECORD
[  1211.424] (II) LoadModule: "dri"
[  1211.425] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1211.425] (II) Module dri: vendor="X.Org Foundation"
[  1211.425] 	compiled for 1.9.0, module version = 1.0.0
[  1211.425] 	ABI class: X.Org Server Extension, version 4.0
[  1211.425] (II) Loading extension XFree86-DRI
[  1211.425] (II) LoadModule: "dri2"
[  1211.426] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1211.426] (II) Module dri2: vendor="X.Org Foundation"
[  1211.426] 	compiled for 1.9.0, module version = 1.2.0
[  1211.426] 	ABI class: X.Org Server Extension, version 4.0
[  1211.426] (II) Loading extension DRI2
[  1211.426] (II) LoadModule: "intel"
[  1211.427] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1211.427] (II) Module intel: vendor="X.Org Foundation"
[  1211.427] 	compiled for 1.9.0, module version = 2.12.0
[  1211.427] 	Module class: X.Org Video Driver
[  1211.427] 	ABI class: X.Org Video Driver, version 8.0
[  1211.428] (II) LoadModule: "vesa"
[  1211.428] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1211.429] (II) Module vesa: vendor="X.Org Foundation"
[  1211.429] 	compiled for 1.8.99.905, module version = 2.3.0
[  1211.429] 	Module class: X.Org Video Driver
[  1211.429] 	ABI class: X.Org Video Driver, version 8.0
[  1211.429] (II) LoadModule: "fbdev"
[  1211.429] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1211.430] (II) Module fbdev: vendor="X.Org Foundation"
[  1211.430] 	compiled for 1.8.99.905, module version = 0.4.2
[  1211.430] 	ABI class: X.Org Video Driver, version 8.0
[  1211.430] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[  1211.431] (II) VESA: driver for VESA chipsets: vesa
[  1211.431] (II) FBDEV: driver for framebuffer: fbdev
[  1211.431] (--) using VT number 8

[  1211.437] (WW) Falling back to old probe method for vesa
[  1211.437] (WW) Falling back to old probe method for fbdev
[  1211.437] (II) Loading sub module "fbdevhw"
[  1211.437] (II) LoadModule: "fbdevhw"
[  1211.437] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1211.438] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1211.438] 	compiled for 1.9.0, module version = 0.0.2
[  1211.438] 	ABI class: X.Org Video Driver, version 8.0
[  1211.443] (EE) intel(0): No kernel modesetting driver detected.
[  1211.443] (II) UnloadModule: "intel"
[  1211.443] (EE) Screen(s) found, but none have a usable configuration.
[  1211.443] 
Fatal server error:
[  1211.443] no screens found
[  1211.444] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  1211.444] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1211.444] 
[  1211.454]  ddxSigGiveUp: Closing log

---

### Post by James Keating on 2010-10-12
I am having the same problem, and my log file looks much like yours. Everything is upgraded, nothing is missing, and yet X won't run -- not even with old kernals that worked, not with any boot parameters that have ever worked, and not even in failsafe mode. 

For 10.04, I got the Intel 8xx blank screen problem. This is worse. I can't see what the problem is -- how DOES X pick its drivers, now that the configuration file configures nothing? -- and no one seems to have a solution. I think I'll have to re-install everything, and hope it works --the CD works, so a fresh install should (shouldn't it?). 

I was a fool to upgrade. It has been years since I had an upgrade that created only minor glitches. Each time the trouble has been worse than ever before.

---

### Post by Evil_Catbert on 2010-10-12
My Acer 3820TG had similar issues. I solved it through letting Ubuntu build a new xorg.conf.

```
cd /etc/X11/
sudo mv xorg.conf xorg.conf.HIDDEN
```

Second line removes the existing xorg.conf. Ubuntu will recreate this at next bootup.

---

### Post by GavinP on 2010-10-12
Thanks for the reply but the xorg.conf had already been removed hence why the logs show the default settings are being used to try and fail to create a new config...

---

### Post by redeyerulk on 2010-10-13
Hi I have the same problem(same log) with i3 processor with built in graphics. I'v copied xorg.conf.failsafe to xorg.conf and got it working but this is the same as running Ubuntu in low graphic mode...
Can somebody confirm if reinstalling Ubuntu 10.10 from cd will solve this problem or should I reinstall ubuntu 10.04 which in my case  worked just with minor graphics problems and with 3d acceleration?

---

### Post by James Keating on 2010-10-13
(duplicate of following post)

---

### Post by James Keating on 2010-10-13
Fixed it. Ha. That only took a day and 372 dead ends and failed attempts.

I believe I now am using the same xorg.conf as before, and that my trouble came from the upgrade creating a generic xorg.conf that didn't work. If so, then the details below may be wrong for other people, but the problem may be the same:
     >>> upgrade created a bad generic xorg.conf
and the solution may be the same:
     >>> restore the backup xorg.conf

What works for me overall is:
1. two critical lines in xorg.conf
2. one option in grub 
3. a particular kernel

1. 
I backed up /etc/X11 xorg.conf (to xorg.conf-2010.10.10) 
and copied the backup file xorg.conf~ to xorg.conf

This initially did not work because the critical lines had smart quotes instead of double quotes. Fixing those did it. (I don't know if DRI off is really necessary, but it was there before and it works now.)

The relevant lines of xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "DRI" "off"
EndSection

All the rest is generic:

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

2.
I previously only had success by booting with i915.modeset=1. I haven't actually tried removing this to see if it is still necessary, but I assume it is.

The relevant line in /etc/defaults/grub reads

GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"

save and run sudo update-grub

3.
I previously only had success with a release candidate kernel from htp://kernel.ubuntu.com/~kernel-ppa/mainline/. I had to try several before one worked (2.6.34-020634rc7). 

The newest kernel that came with the upgrade (2.6.35.22) partly worked. I got a desktop, but no cursor and no video capability. So I went back to my release candidate kernel and now everything appears to be fine.

---

### Post by GavinP on 2010-10-15
I tried the first two steps above (not tried a replacement kernel yet) but still no joy - I can't believe this got through beta testing !

How many netbooks run Ubuntu ? This is ridiculous.

Thanks

Gavin

---

### Post by seppiz on 2010-10-15
Maybe this could be a hint for the problem [https://bugzilla.kernel.org/show_bug.cgi?id=15533](https://bugzilla.kernel.org/show_bug.cgi?id=15533)

Nevertheless the mentioned workaround has fixed the problem for me: so try to add pci=nocrs to the kernel options

---

### Post by GavinP on 2010-10-16
Thanks for the suggestion but still no joy I'm afraid..

---

### Post by James Keating on 2010-10-17
The parameter pci=nocrs makes no difference in my case. My computer has an Intel 82852/82855 graphics chip.

---

### Post by aledujke on 2010-10-21
Hi all!

I have the same problem (same error log) and nomodset does not work for me either. I did not try any other kernel except the one that Ubuntu installed/offered me by default.

What's weird though is that live version boots up normally from usb stick.

I tried both to upgrade from 10.04 and to do a clean install. I also tried the latest drivers and latest xorg and had no luck with that. I finally had to do a clean install of 10.04

I tested all of this the day that 10.10 was out. Have not tried it recently.

---

### Post by joseaplaza on 2010-10-29
Hi, i have the same problem with the i5 650 integrated graphics chipset, updated to 10.10 and X didn't start. Had to go back to 10.04, where everything works like a charm.

---

### Post by iFritz on 2010-10-31
> **joseaplaza said:**
> Hi, i have the same problem with the i5 650 integrated graphics chipset, updated to 10.10 and X didn't start. Had to go back to 10.04, where everything works like a charm.

Have u tried starting with "i915.modeset=0" and Glasens intel driver?

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

---

### Post by GavinP on 2010-11-13
Yes, sorry I lost patience with this - it seems incredible that this was released with such a bug - I could understand it if this was some sort of exotic setup but a vanilla Intel Atom board..

I have gone back to 10.04 which actually works..

Thanks

Gavin

---

