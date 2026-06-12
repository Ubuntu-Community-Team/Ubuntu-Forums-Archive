---
title: "Quick fix sort of for nouveau with 2.6.30-1-generic"
date: 2009-04-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-04-30
quick bodge to get nouveau 0.0.11+git20090404 running with 2.6.30-1-generic for the moment with gives me 
/var/lib/dkms/nouveau/0.0.11+git20090404/build/linux-core/drm_os_linux.h:36: error: conflicting types for &#8216;irqreturn_t'

edit "/usr/src/nouveau-0.0.11+git20090404/linux-core/drm_os_linux.h"
and comment out line: 36 
**typedef void irqreturn_t; **
to
**//typedef void irqreturn_t; **
( it conflicts with kernel header)

for bug drm_sysfs.c:172: error: &#8216;struct device&#8217; has no member named &#8216;bus_id&#8217; also edit "/usr/src/nouveau-0.0.11+git20090404/linux-core/drm_sysfs.c"
and change line 172: from

**snprintf(minor->kdev.bus_id, BUS_ID_SIZE, minor_str, minor->index);**

to
[B]
snprintf(dev_name(&minor->kdev), BUS_ID_SIZE, minor_str, minor->index);[/B]

if anyone is still (like me) using the older nvidia 180.44 from the repo you can bodge that by commenting out all the lines containing 'owner' in "/usr/src/nvidia-180.44/nv.c"

---

### Post by Toe on 2009-05-01
Thank you :)
Now I can finally use nouveau on 2.6.30.

---

### Post by dinxter on 2009-05-01
i was a bit lazy before :) 
with a clean nouveau-kernel-source from karmic (rather than a 'fixed' one), 

- add the patch file in the attached archive to "/usr/src/nouveau-0.0.11+git20090404/patches/"

- add the line,
"PATCH[0]="karmic-2.6.30-1-generic.patch"
to the file,
"/usr/src/nouveau-0.0.11+git20090404/dkms.conf"

---

### Post by Toe on 2009-05-01
Could your modifications be the cause of very slow 2D performance with the 2.6.30-kernel?

---

### Post by dinxter on 2009-05-01
no, they're just minor compatibility changes for the new kernel to get nouveau working while waiting for the updates. it runs fine here and at proper speed, maybe your x log will tell you more. window manager compositing turned on will cause a lot of slowdown so you might want to double check that

---

### Post by Toe on 2009-05-01
Compositing is turned off. The 2.6.28 Jaunty kernels work fine, whereas 2D performance is slow on Karmic's 2.6.30 ones. Videos are unwatchable.

Here's a snippet from the system log that might be relevant
```
May  2 00:28:17 AK1500 kernel: [   39.616692] EXT3 FS on sda1, internal journal
May  2 00:28:17 AK1500 kernel: [   39.616704] EXT3-fs: mounted filesystem with writeback data mode.
May  2 00:28:17 AK1500 kernel: [   41.203912] microcode: CPU0 updated from revision 0x7 to 0x12, date = 2002-07-16 
May  2 00:28:17 AK1500 kernel: [   46.976847] [drm] Initialized drm 1.1.0 20060810
May  2 00:28:17 AK1500 kernel: [   47.012969] pci 0000:01:00.0: BAR 1: can't reserve mem region [0xd0000000-0xdfffffff]
May  2 00:28:17 AK1500 kernel: [   47.013389] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
May  2 00:28:17 AK1500 kernel: [   47.013406] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
May  2 00:28:17 AK1500 kernel: [   47.013627] *pde = 00000000 
May  2 00:28:17 AK1500 kernel: [   47.013645] Modules linked in: nouveau(+) drm video output microcode w83627hf hwmon_vid snd_usb_audio snd_usb_lib snd_hwdep snd_ens1371 gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm psmouse serio_raw snd_seq_dummy snd_seq_oss pcspkr snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq gspca_zc3xx gspca_main snd_timer snd_seq_device videodev iTCO_wdt iTCO_vendor_support v4l1_compat snd soundcore snd_page_alloc intel_agp shpchp agpgart aic7xxx scsi_transport_spi via_rhine mii usb_storage raid10 raid456 raid6_pq async_xor async_memcpy async_tx xor raid1 raid0 multipath linear vesafb fbcon tileblit font bitblit softcursor
May  2 00:28:17 AK1500 kernel: [   47.013744] 
May  2 00:28:17 AK1500 kernel: [   47.013752] Pid: 3968, comm: modprobe Not tainted (2.6.30-2-generic #3-Ubuntu)  
May  2 00:28:17 AK1500 kernel: [   47.013759] EIP: 0060:[<c02e3f31>] EFLAGS: 00213202 CPU: 0
May  2 00:28:17 AK1500 kernel: [   47.013766] EIP is at vsnprintf+0x331/0x430
May  2 00:28:17 AK1500 kernel: [   47.013771] EAX: 00000004 EBX: 00000000 ECX: 00000001 EDX: 00000014
May  2 00:28:17 AK1500 kernel: [   47.013776] ESI: f8bc3cd5 EDI: 00000000 EBP: f652be70 ESP: f652be18
May  2 00:28:17 AK1500 kernel: [   47.013782]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May  2 00:28:17 AK1500 kernel: [   47.013796]  c0210534 00000001 f6bc6a20 00000009 f698db00 f652be9c f8bb6c79 f652be4c
May  2 00:28:17 AK1500 kernel: [   47.014181] ---[ end trace cfaef7bf3cf32117 ]---
May  2 00:28:17 AK1500 kernel: [   47.787480] microcode: CPU0 updated from revision 0x12 to 0x12, date = 2002-07-16 
```

Here's the complete Xorg.log. In it Nouveau seems to complain about an error opening the drm, falling back to NoAccel mode.
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux AK1500 2.6.30-2-generic #3-Ubuntu SMP Fri May 1 01:38:05 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May  2 00:28:24 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xe8000000/16777216, 0xd0000000/268435456, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers//nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.0.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU driver Date:   Fri Apr 3 12:22:04 2009 +1000
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(--) NOUVEAU(0): Chipset: "NVIDIA NV34"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU(0): Initializing int10
(II) NOUVEAU(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card0
(EE) [drm] drmOpen failed.
(EE) NOUVEAU(0): [drm] error opening the drm
(!!) NOUVEAU(0): Failing back to NoAccel mode
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NOUVEAU(0): Randr1.2 support enabled
(==) NOUVEAU(0): Using HW cursor
(--) NOUVEAU(0): Linear framebuffer at 0xD0000000
(--) NOUVEAU(0): MMIO registers at 0xE8000000
(II) NOUVEAU(0): Initial CRTC_OWNER is 4
(II) NOUVEAU(0): Attempting to load BIOS image from PROM
(II) NOUVEAU(0): ... appears to be valid
(II) NOUVEAU(0): BMP BIOS found
(II) NOUVEAU(0): BMP version 5.38
(II) NOUVEAU(0): Bios version 04.34.20.54
(II) NOUVEAU(0): Found Display Configuration Block version 2.2
(!!) NOUVEAU(0): Raw DCB entry 0: 01000300 000088b8
(!!) NOUVEAU(0): Raw DCB entry 1: 02010310 000088b8
(!!) NOUVEAU(0): Raw DCB entry 2: 01010312 00000000
(!!) NOUVEAU(0): Raw DCB entry 3: 02020321 00000003
(II) NOUVEAU(0): Loading NV17 power sequencing microcode
(--) NOUVEAU(0): Parsing VBIOS init table 0 at offset 0x790A
(--) NOUVEAU(0): Parsing VBIOS init table 1 at offset 0x7AF3
(--) NOUVEAU(0): Parsing VBIOS init table 2 at offset 0x7D14
(--) NOUVEAU(0): Parsing VBIOS init table 3 at offset 0x7E9A
(--) NOUVEAU(0): Parsing VBIOS init table 4 at offset 0x7EB7
(--) NOUVEAU(0): Parsing VBIOS init table 5 at offset 0x7ED4
(--) NOUVEAU(0): Parsing VBIOS init table 6 at offset 0x7F9F
(II) NOUVEAU(0): Output VGA-0 using monitor section Configured Monitor
(II) NOUVEAU(0): I2C bus "VGA-0" initialized.
(II) NOUVEAU(0): Output DVI-I-0 has no monitor section
(II) NOUVEAU(0): I2C bus "DVI-I-0" initialized.
(II) NOUVEAU(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): I2C device "DVI-I-0:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "DVI-I-0:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
(II) NOUVEAU(0): Output VGA-0 connected
(II) NOUVEAU(0): Output DVI-I-0 connected
(II) NOUVEAU(0): Using exact sizes for initial modes
(II) NOUVEAU(0): Output VGA-0 using initial mode 1280x1024
(II) NOUVEAU(0): Output DVI-I-0 using initial mode 1280x1024
(--) NOUVEAU(0): VideoRAM: 262144 kBytes
(==) NOUVEAU(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NOUVEAU(0): Virtual size is 2560x1024 (pitch 2560)
(**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.5 Hz (I)
(II) NOUVEAU(0): Modeline "1024x768"x43.5   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 35.5 MHz (scaled from 0.0 MHz), 39.4 kHz, 87.8 Hz
(II) NOUVEAU(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NOUVEAU(0): Display dimensions: (310, 230) mm
(**) NOUVEAU(0): DPI set to (209, 113)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): NVEnterVT is called.
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 0)
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): vpll: n 20 m 1 log2p 2
(II) NOUVEAU(0): nv_output_mode_set called for encoder 0
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 0)
(II) NOUVEAU(0): Output VGA-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): vpll: n 70 m 3 log2p 2
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 1 using output B
(II) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 1 x 257
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) AT Translated Set 2 keyboard: xkb_layout: "de"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
(II) NOUVEAU(0): NVLeaveVT is called.
(II) NOUVEAU(0): Restoring encoders
(II) NOUVEAU(0): 0xE1C6: Parsing digital output script table
(II) NOUVEAU(0): Restoring crtcs
(II) NOUVEAU(0): Restoring CRTC_OWNER to 4.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NOUVEAU(0): NVEnterVT is called.
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 0)
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline ""x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline ""x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): vpll: n 20 m 1 log2p 2
(II) NOUVEAU(0): nv_output_mode_set called for encoder 0
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 0)
(II) NOUVEAU(0): Output VGA-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline ""x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline ""x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): vpll: n 70 m 3 log2p 2
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 1 using output B
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) ImPS/2 Generic Wheel Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "(null)"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): vpll: n 70 m 3 log2p 2
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 1 using output B
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): EDID vendor "EIZ", prod id 4100
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) NOUVEAU(0): EDID vendor "DEL", prod id 20480
```

---

### Post by dinxter on 2009-05-01
looks like drm fails on 2.6.30 which wont help speed. you might want to go back to 2.6.28-11 if its noticably slow. drm works with the patched or unpatched nouveau in 2.6.28-11 so i'm guessing its likely xorg/mesa/nouveau updates that are required to work with the new kernel, early days, many more X updates to come no doubt :)

---

### Post by Toe on 2009-05-02
Good thing I always keep old kernels around :)
Well, it shouldn't be too long before updated packages show up.

Thanks for your help!

---

### Post by dinxter on 2009-05-02
no worries, always good to have one or two old kernels knocking around for safety's sake!

---

### Post by RAOF on 2009-05-03
The actual solution for this is to pull a couple of commits from the 2.6.30 drm tree into patches for nouveau-kernel-source.  I've (kinda) done that locally.  When I get time, it'll be fixed in Karmic.

---

### Post by dinxter on 2009-05-03
good stuff, i'm never that comfy with bodging :). its the first month or so in a couple of years i've had nouveau working on my card, it makes me very happy to see it coming along nicely

---

### Post by int on 2009-05-04
nvidia-graphics-drivers-180 (180.44-0ubuntu2) karmic; urgency=low

 * debian.binary/patches/nvidia-x86_64-180.44-2.6.30-rc2.patch:
   - Add patch from
     [http://pavlinux.ru/nv/nvidia-x86_64-180.44-2.6.30-rc2.patch](http://pavlinux.ru/nv/nvidia-x86_64-180.44-2.6.30-rc2.patch)
     to enable compiling against 2.6.30.
 * debian/dkms.conf.in:
   - Apply RT patch on 2.6.30
   - Apply 2.6.30 compilation patch on 2.6.30.
 * debian/control:
   - Update description for libvdpau (LP: #369049)

Date: Mon, 04 May 2009 12:00:43 -0500
Changed-By: Mario Limonciello <mario_limonciello@xxxxxxx>
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@xxxxx>
Signed-By: Mario Limonciello <superm1@xxxxxxxx>
[https://launchpad.net/ubuntu/karmic/+source/nvidia-graphics-drivers-180/180.44-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/nvidia-graphics-drivers-180/180.44-0ubuntu2)

---

