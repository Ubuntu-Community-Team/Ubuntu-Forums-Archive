---
title: "[SOLVED] Nvidia issues w/ last 3 kernels"
date: 2008-07-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Coleop on 2008-07-18
I know that this is an Alpha release but I have pulling my hair out trying to figure out where I am missing something.  I have read all the previous post on getting the nvidia 177 kernel to work.  I have tried the device0 suggestion the dpkg-reconfigure -phigh xserver-org option w/ the driver nvidia and all others that may have been posted.  I will say that the nv driver works both w/ my original and the new xorg config.  Which luckly has been my fail-safe.  If I install the nvidia-177 driver neither of the above work.  The only way I can get xorg to work is to uninstall the nvidia-177 driver and revert back to the original nv driver.  The error I get from xorg is listed below. I would appreciate any help.  I have been through 3 kernel updates and can't seem to get nvidia to load.  Thanks!

```
(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.99.905 (1.5.0 RC 5)
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.99.905-0ubuntu4)
Current Operating System: Linux bryson-desktop 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:53 UTC 2008 i686
Build Date: 16 July 2008  03:37:29PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 18 18:50:57 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d5a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 9

(!!) More than one possible primary device found
(--) PCI: (0@3:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xdc000000/0, 0xb0000000/0, 0xdb000000/0, I/O @ 0x0000dc00/0, BIOS @ 0x????????/131072
(--) PCI: (0@6:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xdf000000/0, 0xc0000000/0, 0xde000000/0, I/O @ 0x0000ec00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.99.905, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"

(WW) Warning, couldn't open module dri2
(II) UnloadModule: "dri2"
(EE) Failed to load module "dri2" (module does not exist, 0)
Primary device is not PCI
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by psyke83 on 2008-07-18
Three things:

1. You really should post your xorg.conf.
2. Have you tried to see if the 173 driver works?
3. Please post the tail section of your dmesg log (the nvidia stuff).

It seems you have mismatched kernel modules/drivers.

---

### Post by Coleop on 2008-07-18
Thanks psyke83 for the response :) Yes I have tried the 173 drivers w/ the same response.  Here is my current xorg.conf.

```
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```




[B]This is the xorg.conf I used before upgrading to Intrepid.  It will not work w/  the 177 or 173 drivers. It will only work w/ the nv driver.
[/B]
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

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
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

	# /dev/input/event
	# for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

	# /dev/input/event
	# for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

	# /dev/input/event
	# for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Samsung 960BF"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 140.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Samsung 960BF"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
#   Option         "SLI" "True"
    Option         "AllowGLXWithComposite" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```


[B]As for posting the tail section of your dmesg log (the nvidia stuff).
[/B]
I will have to reinstall the 177 driver and terminal in to get what I think would be useful info. I will do this and post the output when it errors.   I really appreciate you help.
Thank Coleop

---

### Post by psyke83 on 2008-07-18
Try this (don't worry if it ignores packages that aren't installed)
```
$ sudo dpkg -P nvidia-glx-173 nvidia-glx-177 nvidia-glx-new nvidia-glx nvidia-glx-new-envy nvidia-glx-envy
$ sudo apt-get install nvidia-glx-177
```

Then after a reboot, check your dmesg log to see if it gives any useful output.

---

### Post by Coleop on 2008-07-18
[B]Here is what the dmesg showed after installing nvidia-177 but, before I tried your solution.  I am rebooting now after purging config files.
[/B]

```
[    3.463984] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.745470] ata1: SATA link down (SStatus 0 SControl 0)
[    8.413454] ata2: SATA link down (SStatus 0 SControl 0)
[    8.417432] sata_nv 0000:00:10.0: version 3.5
[    8.417432] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    8.417432] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 23
[    8.417432] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    8.417432] scsi2 : sata_nv
[    8.417432] scsi3 : sata_nv
[    8.417432] ata3: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 23
[    8.417432] ata4: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 23
[    9.124450] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.132563] ata3.00: ATA-6: ST3200822AS, 3.02, max UDMA/100
[    9.132565] ata3.00: 390721968 sectors, multi 16: LBA48 
[    9.148560] ata3.00: configured for UDMA/100
[    9.481232] ata4: SATA link down (SStatus 0 SControl 300)
[    9.489216] scsi 2:0:0:0: Direct-Access     ATA      ST3200822AS      3.02 PQ: 0 ANSI: 5
[    9.489216] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    9.489216] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LSA1] -> GSI 22 (level, low) -> IRQ 22
[    9.489216] PCI: Setting latency timer of device 0000:00:11.0 to 64
[    9.489216] scsi4 : sata_nv
[    9.489216] scsi5 : sata_nv
[    9.489216] ata5: SATA max UDMA/133 cmd 0x9080 ctl 0x9000 bmdma 0x8800 irq 22
[    9.489216] ata6: SATA max UDMA/133 cmd 0x8c00 ctl 0x8880 bmdma 0x8808 irq 22
[    9.845171] ata5: SATA link down (SStatus 0 SControl 300)
[   10.184527] ata6: SATA link down (SStatus 0 SControl 300)
[   10.184514] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[   10.184514] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 21
[   10.184514] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   10.184514] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   10.184514] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   10.184514] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xdadfe000
[   10.243760] usb usb1: configuration #1 chosen from 1 choice
[   10.243785] hub 1-0:1.0: USB hub found
[   10.243793] hub 1-0:1.0: 10 ports detected
[   10.344511] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[   10.344511] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 20 (level, low) -> IRQ 20
[   10.344511] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   10.344511] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   10.344511] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   10.344511] ehci_hcd 0000:00:0b.1: debug port 1
[   10.344511] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   10.344511] ehci_hcd 0000:00:0b.1: irq 20, io mem 0xdadffc00
[   10.408606] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.408668] usb usb2: configuration #1 chosen from 1 choice
[   10.408691] hub 2-0:1.0: USB hub found
[   10.408698] hub 2-0:1.0: 10 ports detected
[   10.515602] pata_amd 0000:00:0f.0: version 0.3.10
[   10.515602] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   10.515602] scsi6 : pata_amd
[   10.515602] scsi7 : pata_amd
[   10.516479] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   10.516481] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   10.688478] ata7.00: ATA-6: WDC WD2500LB-55EDA0, 15.05R15, max UDMA/100
[   10.688478] ata7.00: 488397168 sectors, multi 16: LBA48 
[   10.688478] ata7.01: ATA-6: WDC WD2500BB-55GUC0, 08.02D08, max UDMA/100
[   10.688478] ata7.01: 488397168 sectors, multi 16: LBA48 
[   10.688478] ata7: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c6c0c0) ACPI=0x3f01f (20:20:0x15)
[   10.688478] ata7: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c6c0c0) ACPI=0x3f01f (20:20:0x15)
[   10.768852] ata7.00: configured for UDMA/100
[   10.784964] ata7.01: configured for UDMA/100
[   10.975329] ata8.00: ATAPI: DVDRW IDE 16X, VER A082, max UDMA/66
[   10.975340] ata8.01: ATAPI: IDE-DVD ROM 6116, HD24, max UDMA/66
[   10.975350] ata8: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc6c6c0c0) ACPI=0x701f (60:60:0x15)
[   10.975354] ata8: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc6c6c0c0) ACPI=0x701f (60:60:0x15)
[   10.991246] ata8.00: configured for UDMA/33
[   11.087936] ata8.01: configured for UDMA/33
[   11.092257] scsi 6:0:0:0: Direct-Access     ATA      WDC WD2500LB-55E 15.0 PQ: 0 ANSI: 5
[   11.092257] scsi 6:0:1:0: Direct-Access     ATA      WDC WD2500BB-55G 08.0 PQ: 0 ANSI: 5
[   11.092257] scsi 7:0:0:0: CD-ROM            DVDRW    IDE 16X          A082 PQ: 0 ANSI: 5
[   11.100599] scsi 7:0:1:0: CD-ROM            IDE-DVD  ROM 6116         HD24 PQ: 0 ANSI: 5
[   11.104254] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   11.104254] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   11.104254] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 23
[   11.104254] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   11.787642] forcedeth 0000:00:13.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:17:31:d8:8f:9c
[   11.787645] forcedeth 0000:00:13.0: highdma csum timirq gbit lnktim desc-v3
[   11.792219] ACPI: PCI Interrupt 0000:04:0b.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 19
[   11.842905] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ddeff800-ddefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   11.860212] Driver 'sd' needs updating - please use bus_type methods
[   11.860212] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   11.860212] sd 2:0:0:0: [sda] Write Protect is off
[   11.860212] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.860212] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.860212] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   11.860212] sd 2:0:0:0: [sda] Write Protect is off
[   11.860212] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.860213] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.860213]  sda: sda1
[   11.864211] sd 2:0:0:0: [sda] Attached SCSI disk
[   11.864211] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   11.864211] sd 6:0:0:0: [sdb] Write Protect is off
[   11.864211] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   11.864211] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.864211] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   11.864211] sd 6:0:0:0: [sdb] Write Protect is off
[   11.864211] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   11.864211] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.864211]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[   11.883002]  sdb1 sdb2 < sdb5 >
[   11.920351] sd 6:0:0:0: [sdb] Attached SCSI disk
[   11.920351] sd 6:0:1:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   11.920351] sd 6:0:1:0: [sdc] Write Protect is off
[   11.920351] sd 6:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   11.920351] sd 6:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.920351] sd 6:0:1:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   11.920351] sd 6:0:1:0: [sdc] Write Protect is off
[   11.920351] sd 6:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   11.920351] sd 6:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.920351]  sdc: sdc1
[   11.948348] sd 6:0:1:0: [sdc] Attached SCSI disk
[   11.960211] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[   11.960211] Uniform CD-ROM driver Revision: 3.20
[   11.960211] sr 7:0:0:0: Attached scsi CD-ROM sr0
[   11.962288] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   11.962314] sd 6:0:0:0: Attached scsi generic sg1 type 0
[   11.962331] sd 6:0:1:0: Attached scsi generic sg2 type 0
[   11.962368] sr 7:0:0:0: Attached scsi generic sg3 type 5
[   11.962384] sr 7:0:1:0: Attached scsi generic sg4 type 5
[   11.980149] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[   11.980149] sr 7:0:1:0: Attached scsi CD-ROM sr1
[   12.418853] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   12.497172] EXT3-fs: INFO: recovery required on readonly filesystem.
[   12.497176] EXT3-fs: write access will be enabled during recovery.
[   12.637810] usb 1-2: configuration #1 chosen from 1 choice
[   12.942743] usb 1-5: new full speed USB device using ohci_hcd and address 3
[   13.123861] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000ba9eb8]
[   13.154281] usb 1-5: configuration #1 chosen from 1 choice
[   13.443844] kjournald starting.  Commit interval 5 seconds
[   13.450320] EXT3-fs: recovery complete.
[   13.450320] EXT3-fs: mounted filesystem with ordered data mode.
[   13.488383] usb 1-6: new low speed USB device using ohci_hcd and address 4
[   13.691353] usb 1-6: configuration #1 chosen from 1 choice
[   14.028519] usb 1-9: new full speed USB device using ohci_hcd and address 5
[   14.237534] usb 1-9: configuration #1 chosen from 1 choice
[   14.237534] usbcore: registered new interface driver hiddev
[   14.241506] input: Logitech USB Receiver as /class/input/input1
[   14.241506] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-2
[   14.245506] input: Logitech USB Receiver as /class/input/input2
[   14.273562] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-2
[   14.278553] input: Logitech USB Receiver as /class/input/input3
[   14.278553] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-5
[   14.289536] input: Logitech USB Receiver as /class/input/input4
[   14.289536] input,hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:0b.0-5
[   14.289536] input: Logitech Logitech Extreme 3D Pro as /class/input/input5
[   14.289536] input,hidraw4: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D Pro] on usb-0000:00:0b.0-6
[   14.289536] usbcore: registered new interface driver usbhid
[   14.289536] usbhid: v2.6:USB HID core driver
[   22.200682] udevd version 124 started
[   22.357528] udev: renamed network interface eth1 to eth0
[   22.406740] udev: renamed network interface eth0_rename to eth1
[   23.199829] input: Power Button (FF) as /class/input/input6
[   23.250313] ACPI: Power Button (FF) [PWRF]
[   23.250404] input: Power Button (CM) as /class/input/input7
[   23.309302] ACPI: Power Button (CM) [PWRB]
[   23.891690] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.923435] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.068009] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   24.068027] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   24.393697] Linux agpgart interface v0.103
[   24.468762] usbcore: registered new interface driver libusual
[   24.634773] nvidia: module license 'NVIDIA' taints kernel.
[   24.960812] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 19
[   24.960812] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   24.960812] nvidia 0000:06:00.0: enabling device (0000 -> 0003)
[   24.960812] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 18 (level, low) -> IRQ 18
[   24.960812] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   24.960812] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.13  Tue Jun 10 16:45:17 PDT 2008
[   25.021313] Initializing USB Mass Storage driver...
[   25.024271] scsi8 : SCSI emulation for USB Mass Storage devices
[   25.026734] usbcore: registered new interface driver usb-storage
[   25.026738] USB Mass Storage support registered.
[   25.029313] usb-storage: device found at 5
[   25.029313] usb-storage: waiting for device to settle before scanning
[   25.078780] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 22
[   25.078785] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LACI] -> GSI 22 (level, low) -> IRQ 22
[   25.078802] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   25.081331] input: PC Speaker as /class/input/input8
[   25.404021] intel8x0_measure_ac97_clock: measured 54123 usecs
[   25.404024] intel8x0: clocking to 46950
[   25.527555] lp: driver loaded but no devices found
[   26.222145] EXT3 FS on sdb1, internal journal
[   27.051646] type=1505 audit(1216434642.425:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4282
[   27.051824] type=1505 audit(1216434642.425:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4282
[   27.149423] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.192893] sky2 eth1: enabling interface
```

---

### Post by Coleop on 2008-07-18
[B]After rebooting and following your instructions here is my Xorg.0.log file and the end of my dmesg.  Unfortunately I am still at square one.  I might should note that I never could get X to run under the 26-3 kernel but could under the 26-2 kernel but only w/ the nv driver.

Xorg.0.log[/B]
  
```
(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.99.905 (1.5.0 RC 5)
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.99.905-0ubuntu4)
Current Operating System: Linux bryson-desktop 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:53 UTC 2008 i686
Build Date: 16 July 2008  03:37:29PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 18 21:51:02 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d5a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@3:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xdc000000/0, 0xb0000000/0, 0xdb000000/0, I/O @ 0x0000dc00/0, BIOS @ 0x????????/131072
(--) PCI: (0@6:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xdf000000/0, 0xc0000000/0, 0xde000000/0, I/O @ 0x0000ec00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.99.905, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"

(WW) Warning, couldn't open module dri2
(II) UnloadModule: "dri2"
(EE) Failed to load module "dri2" (module does not exist, 0)
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

**dmesg**

[   26.518204] nvidia: module license 'NVIDIA' taints kernel.
[   26.768961] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 19
[   26.768971] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   26.769162] nvidia 0000:06:00.0: enabling device (0000 -> 0003)
[   26.769167] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 18 (level, low) -> IRQ 18
[   26.769172] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   26.769396] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.13  Tue Jun 10 16:45:17 PDT 2008
[   26.880617] input: PC Speaker as /class/input/input8
[   27.009286] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 22
[   27.009290] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LACI] -> GSI 22 (level, low) -> IRQ 22
[   27.009307] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.334692] intel8x0_measure_ac97_clock: measured 54134 usecs
[   27.334695] intel8x0: clocking to 46960
[   27.466596] lp: driver loaded but no devices found
[   28.063332] EXT3 FS on sda1, internal journal
[   29.448591] type=1505 audit(1216435835.937:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4423
[   29.448763] type=1505 audit(1216435835.937:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4423
[   29.594168] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.634753] sky2 eth1: enabling interface
```

**I really appreciate you help. Thanks.**

---

### Post by psyke83 on 2008-07-18
The file "libglx.so" seems to be a symlink to an older driver that was installed on your system (the 1.0.9639 driver), that seems to be your problem. Did you upgrade from Hardy?

tseliot or plun should be able to help sort it out, hopefully they'll chime in. In the meantime, you need to try and purge any old nvidia drivers from your system. Something in this thread may help you (be careful, as some of the older advice may no longer apply): [http://ubuntuforums.org/showthread.php?t=851521](http://ubuntuforums.org/showthread.php?t=851521)

---

### Post by Coleop on 2008-07-19
Yes i did upgrade from Hardy. I will wait and see if they chime in :)  At least I can get a desktop.  Speaking  of desktops when I log off say "reboot"  it goes to an xubuntu logooff after the normal logoff.  As if logging out of one account into another.   Xubuntu-default-settings used as default when I never intentionally installed it.  Had to reinstall rhythmbox, jockey  and OpenOffice.org too after last upgrade.  I haven't figured out all that is missing yet. But that is another matter. Thanks for your continued support.

---

### Post by tseliot on 2008-07-19
> **Coleop said:**
> 
```
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
```


You're using driver 9639 which is not nvidia-glx-177 and which doesn't work with the current Xserver.

Can you post the output of this command?
```
sudo aptitude search nvidia
```

---

### Post by Coleop on 2008-07-19
**Sorry took me so long to get back.  Here is the output you requested.**

```
p   nvidia-173-kernel-source                                            - NVIDIA binary kernel module source                                           
i   nvidia-173-modaliases                                               - Modaliases for the NVIDIA binary X.Org driver                                
p   nvidia-177-kernel-source                                            - NVIDIA binary kernel module source                                           
i   nvidia-177-modaliases                                               - Modaliases for the NVIDIA binary X.Org driver                                
p   nvidia-71-kernel-source                                             - NVIDIA binary kernel module source                                           
i   nvidia-71-modaliases                                                - Modaliases for the NVIDIA binary X.Org driver                                
p   nvidia-96-kernel-source                                             - NVIDIA binary kernel module source                                           
i   nvidia-96-modaliases                                                - Modaliases for the NVIDIA binary X.Org driver                                
p   nvidia-cg-toolkit                                                   - NVIDIA Cg Toolkit Installer                                                  
v   nvidia-glx                                                          -                                                                              
p   nvidia-glx-173                                                      - NVIDIA binary Xorg driver                                                    
p   nvidia-glx-173-dev                                                  - NVIDIA binary Xorg driver development files                                  
c   nvidia-glx-177                                                      - NVIDIA binary Xorg driver                                                    
p   nvidia-glx-177-dev                                                  - NVIDIA binary Xorg driver development files                                  
p   nvidia-glx-71                                                       - NVIDIA binary Xorg driver                                                    
p   nvidia-glx-71-dev                                                   - NVIDIA binary Xorg driver development files                                  
p   nvidia-glx-96                                                       - NVIDIA binary Xorg driver                                                    
p   nvidia-glx-96-dev                                                   - NVIDIA binary Xorg driver development files                                  
v   nvidia-glx-dev                                                      -                                                                              
p   nvidia-glx-dev-envy                                                 - NVIDIA binary XFree86 4.x/X.Org driver development files                     
p   nvidia-glx-envy                                                     - NVIDIA binary XFree86 4.x/X.Org driver                                       
p   nvidia-glx-legacy-dev-envy                                          - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files            
p   nvidia-glx-legacy-envy                                              - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver                              
p   nvidia-glx-new-dev-envy                                             - NVIDIA binary XFree86 4.x/X.Org 'new' driver development files               
p   nvidia-glx-new-envy                                                 - NVIDIA binary XFree86 4.x/X.Org 'new' driver                                 
v   nvidia-kernel-1.0.7184                                              -                                                                              
v   nvidia-kernel-1.0.7185                                              -                                                                              
v   nvidia-kernel-1.0.8774                                              -                                                                              
v   nvidia-kernel-1.0.9631                                              -                                                                              
v   nvidia-kernel-1.0.9639                                              -                                                                              
v   nvidia-kernel-1.0.9755                                              -                                                                              
v   nvidia-kernel-100.14.11                                             -                                                                              
v   nvidia-kernel-100.14.19                                             -                                                                              
v   nvidia-kernel-169.12                                                -                                                                              
v   nvidia-kernel-71.86.04                                              -                                                                              
v   nvidia-kernel-96.43.05                                              -                                                                              
i   nvidia-kernel-common                                                - NVIDIA binary kernel module common files                                     
v   nvidia-kernel-source                                                -                                                                              
p   nvidia-kernel-source-envy                                           - NVIDIA binary kernel module source                                           
p   nvidia-legacy-kernel-source-envy                                    - NVIDIA binary 'legacy' kernel module source                                  
p   nvidia-new-kernel-source-envy                                       - NVIDIA binary 'new' kernel module source                                     
idA nvidia-settings                                                     - Tool of configuring the NVIDIA graphics driver                               
p   nvidia-xconfig
```

---

### Post by tseliot on 2008-07-20
it might be a broken symlink. Post the output of this command:
```
ls -l /usr/lib/xorg/modules/extensions/libglx.so*
```

---

### Post by Coleop on 2008-07-20
Here is the response I received.

-rw-r--r-- 1 root root 338464 2008-07-16 10:52 /usr/lib/xorg/modules/extensions/libglx.so
-rw-r--r-- 1 root root 503350 2007-01-08 20:25 /usr/lib/xorg/modules/extensions/libglx.so.169.12

---

### Post by tseliot on 2008-07-21
> **Coleop said:**
> Here is the response I received.

-rw-r--r-- 1 root root 338464 2008-07-16 10:52 /usr/lib/xorg/modules/extensions/libglx.so
-rw-r--r-- 1 root root 503350 2007-01-08 20:25 /usr/lib/xorg/modules/extensions/libglx.so.169.12

This doesn't look good. Type:
```
sudo mv /usr/lib/xorg/modules/extensions/libglx.so $HOME/
```
```
sudo mv /usr/lib/xorg/modules/extensions/libglx.so.169.12 $HOME/
```

then:
```
sudo apt-get install --reinstall nvidia-glx-177
```

---

### Post by psyke83 on 2008-07-21
> **tseliot said:**
> This doesn't look good. Type:
```
sudo mv /usr/lib/xorg/modules/extensions/libglx.so $HOME/
```
```
sudo mv /usr/lib/xorg/modules/extensions/libglx.so.169.12 $HOME/
```

then:
```
sudo apt-get install --reinstall nvidia-glx-177
```

If the libglx.so file was not a symlink, it would suggest that at some point he used the nvidia manual installer, right? Then there may be excess "cruft" elsewhere that could cause conflicts. Perhaps he should download the nvidia tarball and run the uninstaller first, and then install your package?

---

### Post by tseliot on 2008-07-21
> **psyke83 said:**
> If the libglx.so file was not a symlink, it would suggest that at some point he used the nvidia manual installer, right? Then there may be excess "cruft" elsewhere that could cause conflicts. Perhaps he should download the nvidia tarball and run the uninstaller first, and then install your package?

right

---

### Post by Coleop on 2008-07-21
I moved the files and also ran the Nvidia tarball uninstall.  But when I tried to install the nvidia-177 drivers I received these errors.

bryson@bryson-desktop:~$ sudo apt-get install --reinstall nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-177-kernel-source
The following NEW packages will be installed:
  nvidia-177-kernel-source nvidia-glx-177
0 upgraded, 2 newly installed, 0 to remove and 59 not upgraded.
Need to get 0B/10.8MB of archives.
After this operation, 32.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package nvidia-177-kernel-source.
(Reading database ... 160545 files and directories currently installed.)
Unpacking nvidia-177-kernel-source (from .../nvidia-177-kernel-source_177.13-0ubuntu7_i386.deb) ...
Selecting previously deselected package nvidia-glx-177.
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.13-0ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-177_177.13-0ubuntu7_i386.deb (--unpack):
 trying to overwrite `/usr/lib/xorg/modules/extensions/libglx.so', which is also in package xserver-xorg-core
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-177_177.13-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tseliot on 2008-07-25
Try this:
```
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa 
```

---

### Post by Bachstelze on 2008-07-25
Also please apste the output of

```
dpkg -S /usr/lib/xorg/modules/extensions/libglx.so
```

There is normally a diversion that prevents the overwriting :

```
firas@nobue ~ % dpkg -S /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 from: /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 to: /usr/lib/nvidia/libglx.so.xserver-xorg-core
xserver-xorg-core, nvidia-glx-177: /usr/lib/xorg/modules/extensions/libglx.so

```

Try completely removing the nvidia package and then reinstalling it :

```
sudo apt-ger emove --purge nvidia-glx-177
sudo apt-get install nvidia-glx-177
```

---

### Post by Bachstelze on 2008-07-25
Also please apste the output of

```
dpkg -S /usr/lib/xorg/modules/extensions/libglx.so
```

There is normally a diversion that prevents the overwriting :

```
firas@nobue ~ % dpkg -S /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 from: /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 to: /usr/lib/nvidia/libglx.so.xserver-xorg-core
xserver-xorg-core, nvidia-glx-177: /usr/lib/xorg/modules/extensions/libglx.so

```

Try completely removing the nvidia package and then reinstalling it :

```
sudo apt-ger emove --purge nvidia-glx-177
sudo apt-get install nvidia-glx-177
```

---

### Post by Kevbert on 2008-07-25
Hi I've just installed the -4 kernel from scratch (as an update from 2 to 3 crashed my system). I have a nVidia Geoforce 7600GS which is using the 173 restricted driver (ticked) but the other two are also marked as being in use.  I was ready to raise a bug report as the download was staying at 0% (for over 10 mins).  So the servers are slow but it eventually installed.  I also have the unsupported-updates (intrepid backports) activated.

---

### Post by Coleop on 2008-07-25
> **tseliot said:**
> Try this:
```
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa 
```

**I tried this and received this error.**

Package libgl1-mesa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgl1-mesa has no installation candidate

**If I try sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa* I get this error**

 sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libgl1-mesa-swx11-dbg for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swx11-dev for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swrast-dbg for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swx11-dbg instead of libgl1-mesa-swrast-dbg
Note, selecting libgl1-mesa-swrast-dev for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swx11-dev instead of libgl1-mesa-swrast-dev
Note, selecting libgl1-mesa-swx11 for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-glide3 for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swx11-i686 for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-glx-dbg for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-dri-dbg for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-dri-dev for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-dev instead of libgl1-mesa-dri-dev
Note, selecting libgl1-mesa-dev for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-dri for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-glx for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swrast for regex 'libgl1-mesa*'
Note, selecting libgl1-mesa-swx11 instead of libgl1-mesa-swrast
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Conflicts: libgl-dev
  libgl1-mesa-glx: Conflicts: libgl1
  libgl1-mesa-swx11: Conflicts: libgl1
  libgl1-mesa-swx11-dev: Conflicts: libgl-dev
E: Broken packages

---

### Post by Coleop on 2008-07-25
> **HymnToLife said:**
> Also please apste the output of

```
dpkg -S /usr/lib/xorg/modules/extensions/libglx.so
```

There is normally a diversion that prevents the overwriting :

```
firas@nobue ~ % dpkg -S /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 from: /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 to: /usr/lib/nvidia/libglx.so.xserver-xorg-core
xserver-xorg-core, nvidia-glx-177: /usr/lib/xorg/modules/extensions/libglx.so

```

Try completely removing the nvidia package and then reinstalling it :

```
sudo apt-ger emove --purge nvidia-glx-177
sudo apt-get install nvidia-glx-177
```


**Here is the output of the dpkg instructions above:**

xserver-xorg-core: /usr/lib/xorg/modules/extensions/libglx.so

---

### Post by Bachstelze on 2008-07-26
Then try to do what I said, completely deinstall nvidia-glx-177 and then reinstall it.

---

### Post by Coleop on 2008-07-26
Uninstalling and reinstalling will not fix my issue I bet I have done it a hundred times. I am missing something some where or don't have something installed right.  I have been working on this for weeks.  I do appreciate everyones responses and have tried all of them.  Unfortunately I still can't get the drivers to load.   One thing that is new is the drivers now show up in Hardware Drivers.

---

### Post by Coleop on 2008-07-26
**When I reinstall and type dpkg -S /usr/lib/xorg/modules/extensions/libglx.so  The response is:**


diversion by nvidia-glx-177 from: /usr/lib/xorg/modules/extensions/libglx.so
diversion by nvidia-glx-177 to: /usr/lib/nvidia/libglx.so.xserver-xorg-core
xserver-xorg-core, nvidia-glx-177: /usr/lib/xorg/modules/extensions/libglx.so


[B]But when I reboot X will not load and it drops into login.  If I try to startx it errors out with the same errors that I started this thread with.

Here is the output into the Xorg.0.log file when the nvidia 177 driver is installed.[/B]

WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.99.905 (1.5.0 RC 5)
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.99.905-0ubuntu4)
Current Operating System: Linux bryson-desktop 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:53 UTC 2008 i686
Build Date: 16 July 2008  03:37:29PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 26 17:33:39 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d5a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@3:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xdc000000/0, 0xb0000000/0, 0xdb000000/0, I/O @ 0x0000dc00/0, BIOS @ 0x????????/131072
(--) PCI: (0@6:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xdf000000/0, 0xc0000000/0, 0xde000000/0, I/O @ 0x0000ec00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.99.905, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"

(WW) Warning, couldn't open module dri2
(II) UnloadModule: "dri2"
(EE) Failed to load module "dri2" (module does not exist, 0)
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

**I have two graphic cards installed in this computer in SLI mode maybe that is the problem.  I will remove one and see if the new way that xorg configs the computer might be the problem.**

---

### Post by Coleop on 2008-07-26
**By pulling the second Nvidia card out of my computer I was able to boot w/ the nvidia-177 driver :) But when I try to load glxgears I get the following:  **

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

**If I go to Nvidia settings and go to OpenGL/GLX information it shows** Fail to query the GLX server vendor.

[B]I appreciate all your help. Any information to get Gl working would be appreciated.  I am assuming that xorg was conflicting w/ the 2 cards.  I will leave the other one out of the machine.


I am not sure if this helps but here is the output from glxinfo:[/B]

 glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

**Here is the output of Xorg.0.log.  It appears that the drivers correct but the glx module is wrong.  I am not sure what I need to fix this reinstalling the driver hasn't helped.**

(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.99.905 (1.5.0 RC 5)
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.99.905-0ubuntu4)
Current Operating System: Linux bryson-desktop 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:53 UTC 2008 i686
Build Date: 16 July 2008  03:37:29PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 27 18:01:15 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Samsung 960BF"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d5a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@3:0:0) nVidia Corporation G71 [GeForce 7900 GS] rev 161, Mem @ 0xde000000/0, 0xc0000000/0, 0xdd000000/0, I/O @ 0x0000ec00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.99.905, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"

(WW) Warning, couldn't open module dri2
(II) UnloadModule: "dri2"
(EE) Failed to load module "dri2" (module does not exist, 0)
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.0-2 $
(II) NVIDIA dlloader X Driver  177.13  Tue Jun 10 16:49:34 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "True"
(**) NVIDIA(0): Option "TripleBuffer" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
[B](EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 177.13; GLX module
(EE) NVIDIA(0):     version: 1.0-9639.  Please try reinstalling the NVIDIA
(EE) NVIDIA(0):     driver.[/B]
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GS (G71) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.14.09
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GS at PCI:3:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(II) NVIDIA(0): Setting mode "1280x1024_75"

---

### Post by Coleop on 2008-07-28
I managed to solve my issue.  What I had to do was delete the old libglx.so file and create a new sym-link to the libglx.so.177-13 module.  Where I was having my trouble was that it was located in the /usr/lib/xorg/modules/extensions directory not the /usr/lib/xorg/modules/ directory.  I really appreciated all the help.  I am learning as I go and have learned some new things thru out this proccess. The link that I used to figure how to do this is [http://ubuntuforums.org/archive/index.php/t-403164.html](http://ubuntuforums.org/archive/index.php/t-403164.html)  Thanks.

---

### Post by varuzza on 2008-08-25
I had the same problem with two Nvdia 8600 in SLI. The problem was resolved putting the BusID in the Devicce setion.

Section "Device"
   Identifier  "Device0"
   Driver      "nvidia"
   VendorName  "NVIDIA"
   BusID       "PCI:XX:YY:Z"
EndSection

Where XX, YY and Z are the numbers that you obtain with lspci.

---

