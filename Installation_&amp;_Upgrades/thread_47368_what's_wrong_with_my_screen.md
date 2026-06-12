---
title: "what's wrong with my screen ?"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by squid_aja on 2005-07-08
trying to install ubuntu to : 
Unisys Aquanta DL
Pentium 166 Ram : 64 M Hardisk : 6G
but i can't starting "startx" , why ????

this is my /var/log/Xorg.0.log :

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux bamboo01 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i586
Build Date: 05 April 2005
Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 2 09:55:09 1999
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Generic Monitor"
(**) | |-->Device "Cirrus Logic GD 5436 [Alpine]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
Entry deleted from font path.
(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.2
X.Org Video Driver: 0.7
X.Org XInput driver : 0.4
X.Org Server Extension : 0.2
X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) Addressable bus resource ranges are
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[B]
[1] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
[0] -1 0 0xffe00000 - 0xffffffff (0x200000) MX[B](B)
[1] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
[2] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
[3] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
[4] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
[5] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
[6] -1 0 0x00000000 - 0x000000ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
[0] -1 0 0xffe00000 - 0xffffffff (0x200000) MX[B](B)
[1] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
[2] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
[3] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
[4] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
[5] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
[6] -1 0 0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
[0] -1 0 0xffe00000 - 0xffffffff (0x200000) MX[B](B)
[1] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
[2] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
[3] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
[4] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
[5] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
[6] -1 0 0x00000000 - 0x000000ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.2
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 6.8.2, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.13.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.2
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.1.0
ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "cirrus"
(II) Loading /usr/X11R6/lib/modules/drivers/cirrus_drv.o
(II) Module cirrus: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.4
(II) CIRRUS: driver for Cirrus chipsets: CLGD5430, CLGD5434-4, CLGD5434-8,
CLGD5436, CLGD5446, CLGD5480, CL-GD5462, CL-GD5464, CL-GD5464BD,
CL-GD5465, CL-GD7548
(II) Primary Device is: ISA
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
at [http://wiki.X.Org](http://wiki.X.Org)
for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by kuleali on 2005-07-08
try: 

dpkg-reconfigure xserver-xorg

---

### Post by mingus on 2005-07-08
Notice at the end of the log that it is looking for a device on the ISA bus . . . if memory serves, ISA devices may not be detected by the kernel, and if so the driver module needs to be added to /etc/modules file to instruct the kernel to load it.

There is also a cirrus framebuffer driver.  You might try adding this kernel argument to your boot line at the grub menu:
kernel . . . . . . video=cirrusfb

---

### Post by squid_aja on 2005-07-08
[QUOTE=mingus]Notice at the end of the log that it is looking for a device on the ISA bus . . . if memory serves, ISA devices may not be detected by the kernel, and if so the driver module needs to be added to /etc/modules file to instruct the kernel to load it.

There is also a cirrus framebuffer driver.  You might try adding this kernel argument to your boot line at the grub menu:
kernel . . . . . . video=cirrusfb[/QUOTE]
 mingus, how shoul i do that thing ? can u more specified ? sorry i'm a newbie :)

---

### Post by mingus on 2005-07-08
The first thing you should try is the suggestion above, if you haven't done so already:  
$sudo dpkg-reconfigure xserver-xorg
when you get to default depth choose 16 or 15.  Also a lower screen resolution (only for now).  This will rebuild the xorg config file, and will test whether the problem is config related or not being able to find the driver.

The second suggestion is when you boot to replace the default vesa framebuffer with the cirrus framebuffer driver.  At the boot menu highlight the default menu line (the first) and press 'e'; you will be taken to another screen which will show all the lines in that menu choice.  Highlight the kernel line and press 'e' again.  This will display the line, space to the end and add "video=cirrusfb" then hit enter.  Type 'b' and hit enter to boot.  The kernel may pass to the xserver what it needs.

If neither of the above work, and before trying to add modules for the kernel to boot, instead post back the results of doing:
$lspci
$lsmod
be sure to capture the entire list

---

### Post by squid_aja on 2005-07-08
[QUOTE=mingus]The first thing you should try is the suggestion above, if you haven't done so already:  
$sudo dpkg-reconfigure xserver-xorg
when you get to default depth choose 16 or 15.  Also a lower screen resolution (only for now).  This will rebuild the xorg config file, and will test whether the problem is config related or not being able to find the driver.

The second suggestion is when you boot to replace the default vesa framebuffer with the cirrus framebuffer driver.  At the boot menu highlight the default menu line (the first) and press 'e'; you will be taken to another screen which will show all the lines in that menu choice.  Highlight the kernel line and press 'e' again.  This will display the line, space to the end and add "video=cirrusfb" then hit enter.  Type 'b' and hit enter to boot.  The kernel may pass to the xserver what it needs.

If neither of the above work, and before trying to add modules for the kernel to boot, instead post back the results of doing:
$lspci
$lsmod
be sure to capture the entire list[/QUOTE]
 both way doesn't work at all, here is my lspci & lsmod

0000:00:00.0 ffff: ALi Corporation M1511 [Aladdin] (rev ff)
0000:00:02.0 ffff: ALi Corporation M1513 [Aladdin] (rev ff)
0000:00:03.0 ffff: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0646 (rev ff)
0000:00:04.0 ffff: Cirrus Logic GD 5436 [Alpine] (rev ff)
0000:00:0f.0 ffff: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev ff)



Module                  Size  Used by
proc_intf               4100  0 
freq_table              4100  0 
cpufreq_userspace       4572  0 
cpufreq_ondemand        6172  0 
cpufreq_powersave       1920  0 
uhci_hcd               30224  0 
ohci_hcd               19848  0 
ehci_hcd               29444  0 
usbcore               107384  3 uhci_hcd,ohci_hcd,ehci_hcd
e100                   32384  0 
mii                     4736  1 e100
ali_agp                 6784  0 
agpgart                31784  1 ali_agp
floppy                 54864  0 
pcspkr                  3816  0 
rtc                    12216  0 
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
tsdev                   7488  0 
psmouse                19336  0 
evdev                   9088  0 
mousedev               11160  0 
parport_pc             34372  1 
lp                     10792  0 
parport                33480  2 parport_pc,lp
ide_cd                 38532  0 
cdrom                  36508  1 ide_cd
ext3                  120968  1 
jbd                    54168  1 ext3
ide_generic             1664  0 
ide_disk               18176  3 
cmd64x                 11292  1 
ide_core              118988  4 ide_cd,ide_generic,ide_disk,cmd64x
unix                   26164  166 
processor              22708  0 
fbcon                  34048  0 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by mingus on 2005-07-08
Once again please boot with the added kernel argument video=cirrusfb as you did above (be sure it is at the end of the line).  *Immediately* get in a terminal and do:
$dmesg
and post that back here.  Also do lsmod again and post that back here.  And take note whether the screen display looks different.

Looks like the problem is definitely that the needed video driver is not getting loaded. But before we add a module, let's see if the cirrus framebuffer is getting passed through.

---

