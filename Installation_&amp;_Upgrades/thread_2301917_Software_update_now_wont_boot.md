---
title: "Software update now wont boot"
date: 2015-11-06
forum: Installation &amp; Upgrades
---

### Post by chewycwook on 2015-11-06
Hello, please pardon any mispellings as i am on my ipad.

Last night I attempted to do a software update, to get it to work i had to change the server to "main server". During the update i received an error and was asked if i would like to upload the log.  I did, this was around 6:30est yesterday if anyone has access to that.  I am using ubuntu 14.04.   The computer worked fine for the rest of the session yesterday but now when i turn it on it shows the lenovo flash, then brefly the ubuntu loading screen, then goes to what looks like a terminal asking for my username, then quickly goes to a black screen with a flashing curser in the top left.  If I hit the power button the ubuntu loading screen shows and it turns off.

I was able to get access to the grub menu and the root terminal but am unsure of what do do from there.  If there is a way to roll back recently installed packages or what i should do.

It is a lenovo z50 with an Amd prossesor and a ssd.

Again i apologise for any error and the poor formatting, i hate typing on an ipad!  Thank you all for your help.

---

### Post by Bashing-om on 2015-11-06
chewycwook; Hello;

No;
> 
 If there is a way to roll back recently installed packages ........

one fixes the problem .

To that end, in an attempt to identify the problem, can you boot an older kernel from grub's advanced menu ?

Else perhaps boot to terminal, and from terminal identify where the problem is.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-06
Thank you for your time to reply.  Older kernals exhibit the same problem.  I am thinking it may be a problem with the video driver, is there a certain log I should check?   I will start walking through the sticky at the top tonight but figured since it was not a true upgrade it may not be relevant.

---

### Post by Bashing-om on 2015-11-06
chewycwook; Yeah ...

Lot's of logs .. linux is great about informing what it is doing .
When it comes to the GUI, the more informative log is /var/log/Xorg.0.log .

As you have " hit the power button" there is that possibility that the file system was left in an inconsistent state. It is a good thing to run a file system check at this time to make sure that a corrupted file system is not at fault here.
Boot to terminal :
```

sudo touch /forcefsck
sudo shutdown -r now

```
where we set a simple file system check, and upon the next boot will be done.

To see what we have for drivers:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```

Get a look at the situation, then

[INDENT][INDENT][INDENT]decide what we are going to do
[/INDENT][/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-06
I got it to boot by removing and reinstalling fgrlx as outlined here:
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

It boots up now however i get a pop up stating: system program problem detected, cancel or report.

In the details it shows "ubuntu14.04 has experienced an internal error
excutablePath
/usr/bin/Xorg
package
xserver-xorg-core 2:1.15.1-0ubuntu2.7
problemtype
Crash
Title
Xorg crashed with SIGABRT in Cail_Cayman_SetupASIC()

There is more but reading and typing on my ipad is painfull.  Thank you for the confidence to "dig in". I feel as though i am close, in fact everything seems to work properly, however the error is disheartining.  Any idea what is causing that?


Thank you so much!

---

### Post by Bashing-om on 2015-11-06
chewycwook; Yeah ...

This might take 'root'n' as well as digging .
The xserver-xorg-core 2:1.15.1-0ubuntu2.7 is the correct version for the 3.13 series kernel.

Did you (re-)install the driver from our repository or from AMD's site ?

So let's start digging, see what we can discover:
```

lsb_release -a
uname -r
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display
cat /var/log/Xorg.0.log

``` ought to point us in some direction.

[INDENT][INDENT][INDENT]it is amazing
[INDENT][INDENT][INDENT]in here
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-06
```
Xorg.log:
[     4.577] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     4.577] X Protocol Version 11, Revision 0
[     4.577] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     4.577] Current Operating System: Linux Jason-Laptop 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64
[     4.577] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=32b04715-c08d-43ed-b2d1-b491f4aef2f0 ro nomodeset quiet splash vt.handoff=7
[     4.577] Build Date: 12 February 2015  02:49:29PM
[     4.577] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     4.577] Current version of pixman: 0.30.2
[     4.577]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.577] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.577] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  6 22:14:00 2015
[     4.577] (==) Using config file: "/etc/X11/xorg.conf"
[     4.577] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.578] (==) ServerLayout "aticonfig Layout"
[     4.578] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     4.578] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     4.578] (**) |   |-->Device "aticonfig-Device[0]-0"
[     4.578] (==) Automatically adding devices
[     4.578] (==) Automatically enabling devices
[     4.578] (==) Automatically adding GPU devices
[     4.578] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.578]     Entry deleted from font path.
[     4.578] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.578]     Entry deleted from font path.
[     4.578] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.578]     Entry deleted from font path.
[     4.578] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.578]     Entry deleted from font path.
[     4.578] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.578]     Entry deleted from font path.
[     4.578] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.578] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.578] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.578] (II) Loader magic: 0x7f5ec0ad5d40
[     4.578] (II) Module ABI versions:
[     4.578]     X.Org ANSI C Emulation: 0.4
[     4.578]     X.Org Video Driver: 15.0
[     4.578]     X.Org XInput driver : 20.0
[     4.578]     X.Org Server Extension : 8.0
[     4.580] (--) PCI:*(0:0:1:0) 1002:130a:17aa:3988 rev 0, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xf0a00000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[     4.580] Initializing built-in extension Generic Event Extension
[     4.580] Initializing built-in extension SHAPE
[     4.580] Initializing built-in extension MIT-SHM
[     4.580] Initializing built-in extension XInputExtension
[     4.580] Initializing built-in extension XTEST
[     4.580] Initializing built-in extension BIG-REQUESTS
[     4.580] Initializing built-in extension SYNC
[     4.580] Initializing built-in extension XKEYBOARD
[     4.580] Initializing built-in extension XC-MISC
[     4.580] Initializing built-in extension SECURITY
[     4.580] Initializing built-in extension XINERAMA
[     4.580] Initializing built-in extension XFIXES
[     4.580] Initializing built-in extension RENDER
[     4.580] Initializing built-in extension RANDR
[     4.580] Initializing built-in extension COMPOSITE
[     4.580] Initializing built-in extension DAMAGE
[     4.580] Initializing built-in extension MIT-SCREEN-SAVER
[     4.580] Initializing built-in extension DOUBLE-BUFFER
[     4.580] Initializing built-in extension RECORD
[     4.580] Initializing built-in extension DPMS
[     4.580] Initializing built-in extension Present
[     4.580] Initializing built-in extension DRI3
[     4.580] Initializing built-in extension X-Resource
[     4.580] Initializing built-in extension XVideo
[     4.581] Initializing built-in extension XVideo-MotionCompensation
[     4.581] Initializing built-in extension SELinux
[     4.581] Initializing built-in extension XFree86-VidModeExtension
[     4.581] Initializing built-in extension XFree86-DGA
[     4.581] Initializing built-in extension XFree86-DRI
[     4.581] Initializing built-in extension DRI2
[     4.581] (II) "glx" will be loaded by default.
[     4.581] (WW) "xmir" is not to be loaded by default. Skipping.
[     4.581] (II) LoadModule: "glx"
[     4.581] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     4.581] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     4.581]     compiled for 6.9.0, module version = 1.0.0
[     4.581] Loading extension GLX
[     4.581] (II) LoadModule: "fglrx"
[     4.582] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.610] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     4.610]     compiled for 1.4.99.906, module version = 15.20.2
[     4.610]     Module class: X.Org Video Driver
[     4.611] (II) Loading sub module "fglrxdrm"
[     4.611] (II) LoadModule: "fglrxdrm"
[     4.611] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     4.612] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     4.612]     compiled for 1.4.99.906, module version = 15.20.2
[     4.612] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[     4.612] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[     4.612] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[     4.612] (++) using VT number 7

[     4.612] (WW) Falling back to old probe method for fglrx
[     4.640] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     4.643] ukiDynamicMajor: found major device number 251
[     4.643] ukiDynamicMajor: found major device number 251
[     4.643] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     4.643] ukiOpenDevice: node name is /dev/ati/card0
[     4.643] ukiOpenDevice: open result is 9, (OK)
[     5.112] ukiOpenByBusid: ukiOpenMinor returns 9
[     5.112] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.117] (--) Chipset Supported AMD Graphics Processor (0x130A) found
[     5.117] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[     5.118] (II) fglrx(0): pEnt->device->identifier=0x7f5ec12b53e0
[     5.118] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[     5.118] (II) fglrx(0): FB driver is enabled
[     5.119] (II) Loading sub module "vgahw"
[     5.119] (II) LoadModule: "vgahw"
[     5.122] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     5.122] (II) Module vgahw: vendor="X.Org Foundation"
[     5.122]     compiled for 1.15.1, module version = 0.1.0
[     5.122]     ABI class: X.Org Video Driver, version 15.0
[     5.122] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     5.122] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     5.122] (==) fglrx(0): Default visual is TrueColor
[     5.122] (**) fglrx(0): Option "DPMS" "true"
[     5.123] (==) fglrx(0): RGB weight 888
[     5.123] (II) fglrx(0): Using 8 bits per RGB 
[     5.123] (==) fglrx(0): Buffer Tiling is ON
[     5.123] (II) Loading sub module "fglrxdrm"
[     5.123] (II) LoadModule: "fglrxdrm"
[     5.123] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     5.123] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     5.123]     compiled for 1.4.99.906, module version = 15.20.2
[     5.125] ukiDynamicMajor: found major device number 251
[     5.126] ukiDynamicMajor: found major device number 251
[     5.126] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     5.126] ukiOpenDevice: node name is /dev/ati/card0
[     5.126] ukiOpenDevice: open result is 11, (OK)
[     5.126] ukiOpenByBusid: ukiOpenMinor returns 11
[     5.126] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.126] (**) fglrx(0): NoAccel = NO
[     5.126] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     5.126] (--) fglrx(0): Chipset: "AMD Radeon(TM) R6 Graphics" (Chipset = 0x130a)
[     5.126] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x3988)
[     5.126] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     5.126] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     5.126] (--) fglrx(0): MMIO registers at 0xf0a00000
[     5.126] (--) fglrx(0): I/O port at 0x00003000
[     5.126] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     5.127] (II) fglrx(0): ATIF platform detected
[     5.128] (II) fglrx(0): AC Adapter is used
[     5.129] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     5.129] (II) Loading sub module "vbe"
[     5.129] (II) LoadModule: "vbe"
[     5.129] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     5.129] (II) Module vbe: vendor="X.Org Foundation"
[     5.129]     compiled for 1.15.1, module version = 1.1.0
[     5.129]     ABI class: X.Org Video Driver, version 15.0
[     5.130] (II) fglrx(0): VESA BIOS detected
[     5.130] (II) fglrx(0): VESA VBE Version 3.0
[     5.130] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     5.130] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[     5.130] (II) fglrx(0): VESA VBE OEM Software Rev: 15.40
[     5.130] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, Advanced Micro Devices, Inc.
[     5.130] (II) fglrx(0): VESA VBE OEM Product: SPECTRE
[     5.130] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     5.130] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[     5.130] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[     5.130] (II) fglrx(0): PCIE card detected
[     5.130] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     5.130] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     5.130] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x40000000)
[     5.130] (II) fglrx(0): RandR 1.2 support is enabled!
[     5.130] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     5.130] (II) Loading sub module "fb"
[     5.130] (II) LoadModule: "fb"
[     5.130] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.130] (II) Module fb: vendor="X.Org Foundation"
[     5.130]     compiled for 1.15.1, module version = 1.0.0
[     5.130]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.130] (II) fglrx(0): EDID Management option: EDID Management is enabled
[     5.130] (II) Loading sub module "ddc"
[     5.130] (II) LoadModule: "ddc"
[     5.130] (II) Module "ddc" already built-in
[     5.726] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[     5.726] (II) fglrx(0): Output DFP1 has no monitor section
[     5.726] (II) fglrx(0): Output CRT1 has no monitor section
[     5.726] (II) Loading sub module "ddc"
[     5.726] (II) LoadModule: "ddc"
[     5.726] (II) Module "ddc" already built-in
[     5.726] (WW) fglrx(0): Failed to get EDID by ACPI
[     5.727] (II) fglrx(0): Connected Display0: LVDS
[     5.727] (II) fglrx(0): Display0 EDID data ---------------------------
[     5.727] (II) fglrx(0): Manufacturer: BOE  Model: 61d  Serial#: 0
[     5.727] (II) fglrx(0): Year: 2014  Week: 1
[     5.727] (II) fglrx(0): EDID Version: 1.4
[     5.727] (II) fglrx(0): Digital Display Input
[     5.727] (II) fglrx(0): 6 bits per channel
[     5.727] (II) fglrx(0): Digital interface is DisplayPort
[     5.727] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     5.727] (II) fglrx(0): Gamma: 2.20
[     5.727] (II) fglrx(0): No DPMS capabilities specified
[     5.727] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[     5.727] (II) fglrx(0): First detailed timing is preferred mode
[     5.727] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[     5.727] (II) fglrx(0): redX: 0.585 redY: 0.347   greenX: 0.334 greenY: 0.569
[     5.727] (II) fglrx(0): blueX: 0.164 blueY: 0.117   whiteX: 0.312 whiteY: 0.339
[     5.727] (II) fglrx(0): Manufacturer's mask: 0
[     5.727] (II) fglrx(0): Supported detailed timing:
[     5.727] (II) fglrx(0): clock: 72.3 MHz   Image Size:  309 x 173 mm
[     5.727] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     5.727] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[     5.727] (II) fglrx(0):  BOE HF
[     5.727] (II) fglrx(0):  NT156WHM-N12
[     5.727] (II) fglrx(0): EDID (in hex):
[     5.727] (II) fglrx(0):     00ffffffffffff0009e51d0600000000
[     5.727] (II) fglrx(0):     011801049522137802fb0f955855912a
[     5.727] (II) fglrx(0):     1e4f5600000001010101010101010101
[     5.727] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     5.727] (II) fglrx(0):     360035ad1000001a0000000000000000
[     5.727] (II) fglrx(0):     00000000000000000000000000fe0042
[     5.727] (II) fglrx(0):     4f452048460a202020202020000000fe
[     5.727] (II) fglrx(0):     004e5431353657484d2d4e31320a00e5
[     5.727] (II) fglrx(0): End of Display0 EDID data --------------------
[     5.727] (II) fglrx(0): Dynamic Surface Resizing Enabled
[     5.728] (WW) fglrx(0): Failed to get EDID by ACPI
[     5.728] (II) fglrx(0): EDID for output LVDS
[     5.728] (II) fglrx(0): Manufacturer: BOE  Model: 61d  Serial#: 0
[     5.728] (II) fglrx(0): Year: 2014  Week: 1
[     5.728] (II) fglrx(0): EDID Version: 1.4
[     5.728] (II) fglrx(0): Digital Display Input
[     5.728] (II) fglrx(0): 6 bits per channel
[     5.728] (II) fglrx(0): Digital interface is DisplayPort
[     5.728] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     5.728] (II) fglrx(0): Gamma: 2.20
[     5.728] (II) fglrx(0): No DPMS capabilities specified
[     5.728] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[     5.728] (II) fglrx(0): First detailed timing is preferred mode
[     5.728] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[     5.728] (II) fglrx(0): redX: 0.585 redY: 0.347   greenX: 0.334 greenY: 0.569
[     5.728] (II) fglrx(0): blueX: 0.164 blueY: 0.117   whiteX: 0.312 whiteY: 0.339
[     5.728] (II) fglrx(0): Manufacturer's mask: 0
[     5.728] (II) fglrx(0): Supported detailed timing:
[     5.728] (II) fglrx(0): clock: 72.3 MHz   Image Size:  309 x 173 mm
[     5.728] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     5.728] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[     5.728] (II) fglrx(0):  BOE HF
[     5.728] (II) fglrx(0):  NT156WHM-N12
[     5.728] (II) fglrx(0): EDID (in hex):
[     5.728] (II) fglrx(0):     00ffffffffffff0009e51d0600000000
[     5.728] (II) fglrx(0):     011801049522137802fb0f955855912a
[     5.728] (II) fglrx(0):     1e4f5600000001010101010101010101
[     5.728] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     5.728] (II) fglrx(0):     360035ad1000001a0000000000000000
[     5.728] (II) fglrx(0):     00000000000000000000000000fe0042
[     5.728] (II) fglrx(0):     4f452048460a202020202020000000fe
[     5.728] (II) fglrx(0):     004e5431353657484d2d4e31320a00e5
[     5.728] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     5.728] (II) fglrx(0): Printing DDC gathered Modelines:
[     5.728] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     5.728] (II) fglrx(0): Printing probed modes for output LVDS
[     5.728] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     5.728] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz e)
[     5.728] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 777 790 +hsync -vsync (47.4 kHz e)
[     5.728] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz e)
[     5.728] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 777 790 +hsync -vsync (47.4 kHz e)
[     5.728] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 777 790 +hsync -vsync (47.4 kHz e)
[     5.728] (II) fglrx(0): EDID for output DFP1
[     5.728] (II) fglrx(0): EDID for output CRT1
[     5.728] (II) fglrx(0): Output LVDS connected
[     5.728] (II) fglrx(0): Output DFP1 disconnected
[     5.728] (II) fglrx(0): Output CRT1 disconnected
[     5.728] (II) fglrx(0): Using exact sizes for initial modes
[     5.728] (II) fglrx(0): Output LVDS using initial mode 1366x768
[     5.728] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     5.728] (II) fglrx(0): Display dimensions: (340, 190) mm
[     5.728] (II) fglrx(0): DPI set to (102, 102)
[     5.728] (II) fglrx(0): Eyefinity capable adapter detected.
[     5.728] (II) fglrx(0): Adapter AMD Radeon(TM) R6 Graphics has 4 configurable heads and 1 displays connected.
[     5.728] (==) fglrx(0):  PseudoColor visuals disabled
[     5.729] (II) Loading sub module "ramdac"
[     5.729] (II) LoadModule: "ramdac"
[     5.729] (II) Module "ramdac" already built-in
[     5.729] (==) fglrx(0): NoDRI = NO
[     5.729] (==) fglrx(0): Capabilities: 0x00000000
[     5.729] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     5.729] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     5.729] (==) fglrx(0): UseFastTLS=0
[     5.729] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[     5.729] (--) Depth 24 pixmap format is 32 bpp
[     5.729] Loading extension ATIFGLRXDRI
[     5.729] (II) fglrx(0): doing swlDriScreenInit
[     5.729] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     5.730] ukiDynamicMajor: found major device number 251
[     5.730] ukiDynamicMajor: found major device number 251
[     5.730] ukiDynamicMajor: found major device number 251
[     5.730] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     5.730] ukiOpenDevice: node name is /dev/ati/card0
[     5.730] ukiOpenDevice: open result is 12, (OK)
[     5.730] ukiOpenByBusid: ukiOpenMinor returns 12
[     5.730] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.730] (II) fglrx(0): [uki] DRM interface version 1.0
[     5.730] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[     5.730] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     5.730] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f5ec08e2000
[     5.730] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     5.730] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     5.730] (II) fglrx(0): swlDriScreenInit done
[     5.730] (II) fglrx(0): Kernel Module Version Information:
[     5.730] (II) fglrx(0):     Name: fglrx
[     5.730] (II) fglrx(0):     Version: 15.20.2
[     5.730] (II) fglrx(0):     Date: Feb 27 2015
[     5.730] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[     5.730] (II) fglrx(0): Kernel Module version matches driver.
[     5.730] (II) fglrx(0): Kernel Module Build Time Information:
[     5.730] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-67-generic
[     5.730] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[     5.730] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     5.730] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     5.730] (II) fglrx(0): [uki] register handle = 0x00004000
[     5.731] (II) fglrx(0): DRI initialization successfull
[     5.731] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x01080000
[     5.731] (==) fglrx(0): Backing store enabled
[     5.731] Loading extension FGLRXEXTENSION
[     5.731] (**) fglrx(0): DPMS enabled
[     5.731] (II) fglrx(0): Initialized in-driver Xinerama extension
[     5.731] (**) fglrx(0): Textured Video is enabled.
[     5.731] (II) LoadModule: "glesx"
[     5.731] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[     5.734] (II) Module glesx: vendor="X.Org Foundation"
[     5.734]     compiled for 1.4.99.906, module version = 1.0.0
[     5.734] Loading extension GLESX
[     5.734] (II) fglrx(0): GLESX enableFlags = 8784
[     5.735] (II) fglrx(0): GLESX is enabled
[     5.735] (II) LoadModule: "amdxmm"
[     5.735] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     5.735] (II) Module amdxmm: vendor="X.Org Foundation"
[     5.735]     compiled for 1.4.99.906, module version = 2.0.0
[     5.759] Loading extension AMDXVOPL
[     5.759] Loading extension AMDXVBA
[     5.759] (II) fglrx(0): Enable composite support successfully
[     5.759] (WW) fglrx(0): Option "VendorName" is not used
[     5.759] (WW) fglrx(0): Option "ModelName" is not used
[     5.759] (II) fglrx(0): X context handle = 0x1
[     5.759] (II) fglrx(0): [DRI] installation complete
[     5.759] (==) fglrx(0): Silken mouse enabled
[     5.760] (==) fglrx(0): Using HW cursor of display infrastructure!
[     5.760] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.760] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[     6.600]  IsrHwss_Dce80::UpdateHwPath ADDED displayPath Index -1052529536 controllerID 0
[     6.670] (--) RandR disabled
[     6.675] (II) SELinux: Disabled on system
[     6.676] ukiDynamicMajor: found major device number 251
[     6.676] ukiDynamicMajor: found major device number 251
[     6.676] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.676] ukiOpenDevice: node name is /dev/ati/card0
[     6.676] ukiOpenDevice: open result is 13, (OK)
[     6.676] ukiOpenByBusid: ukiOpenMinor returns 13
[     6.676] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     6.676] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     6.676] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     6.676] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     6.681] ukiDynamicMajor: found major device number 251
[     6.681] ukiDynamicMajor: found major device number 251
[     6.681] ukiDynamicMajor: found major device number 251
[     6.681] ukiOpenDevice: node name is /dev/ati/card0
[     6.681] ukiOpenDevice: open result is 14, (OK)
[     6.681] ukiGetBusid returned 'PCI:0:1:0'
[     6.681] ukiOpenDevice: node name is /dev/ati/card1
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card2
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card3
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card4
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card5
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card6
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card7
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card8
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card9
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.681] ukiOpenDevice: Open failed
[     6.681] ukiOpenDevice: node name is /dev/ati/card10
[     6.681] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: Open failed
[     6.682] ukiOpenDevice: node name is /dev/ati/card11
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: Open failed
[     6.682] ukiOpenDevice: node name is /dev/ati/card12
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: Open failed
[     6.682] ukiOpenDevice: node name is /dev/ati/card13
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: Open failed
[     6.682] ukiOpenDevice: node name is /dev/ati/card14
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: Open failed
[     6.682] ukiOpenDevice: node name is /dev/ati/card15
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: open result is -1, (No such device)
[     6.682] ukiOpenDevice: Open failed
[     6.682] ukiDynamicMajor: found major device number 251
[     6.682] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.682] ukiOpenDevice: node name is /dev/ati/card0
[     6.682] ukiOpenDevice: open result is 14, (OK)
[     6.682] ukiOpenByBusid: ukiOpenMinor returns 14
[     6.682] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     6.727] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     6.728] ukiDynamicMajor: found major device number 251
[     6.728] ukiDynamicMajor: found major device number 251
[     6.728] ukiDynamicMajor: found major device number 251
[     6.728] ukiOpenDevice: node name is /dev/ati/card0
[     6.728] ukiOpenDevice: open result is 15, (OK)
[     6.728] ukiGetBusid returned 'PCI:0:1:0'
[     6.728] ukiOpenDevice: node name is /dev/ati/card1
[     6.728] ukiOpenDevice: open result is -1, (No such device)
[     6.728] ukiOpenDevice: open result is -1, (No such device)
[     6.728] ukiOpenDevice: Open failed
[     6.728] ukiOpenDevice: node name is /dev/ati/card2
[     6.728] ukiOpenDevice: open result is -1, (No such device)
[     6.728] ukiOpenDevice: open result is -1, (No such device)
[     6.728] ukiOpenDevice: Open failed
[     6.728] ukiOpenDevice: node name is /dev/ati/card3
[     6.728] ukiOpenDevice: open result is -1, (No such device)
[     6.728] ukiOpenDevice: open result is -1, (No such device)
[     6.728] ukiOpenDevice: Open failed
[     6.728] ukiOpenDevice: node name is /dev/ati/card4
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card5
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card6
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card7
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card8
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card9
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card10
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card11
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card12
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card13
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card14
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiOpenDevice: node name is /dev/ati/card15
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: open result is -1, (No such device)
[     6.729] ukiOpenDevice: Open failed
[     6.729] ukiDynamicMajor: found major device number 251
[     6.729] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.729] ukiOpenDevice: node name is /dev/ati/card0
[     6.729] ukiOpenDevice: open result is 15, (OK)
[     6.729] ukiOpenByBusid: ukiOpenMinor returns 15
[     6.729] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     6.744] (II) fglrx(0): Setting screen physical size to 361 x 203
[     6.753] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.756] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     6.756] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.756] (II) LoadModule: "evdev"
[     6.756] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.757] (II) Module evdev: vendor="X.Org Foundation"
[     6.757]     compiled for 1.15.0, module version = 2.8.2
[     6.757]     Module class: X.Org XInput Driver
[     6.757]     ABI class: X.Org XInput driver, version 20.0
[     6.757] (II) Using input driver 'evdev' for 'Power Button'
[     6.757] (**) Power Button: always reports core events
[     6.757] (**) evdev: Power Button: Device: "/dev/input/event2"
[     6.757] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.757] (--) evdev: Power Button: Found keys
[     6.757] (II) evdev: Power Button: Configuring as keyboard
[     6.757] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     6.757] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.757] (**) Option "xkb_rules" "evdev"
[     6.757] (**) Option "xkb_model" "pc105"
[     6.757] (**) Option "xkb_layout" "us"
[     6.758] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     6.758] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.758] (II) Using input driver 'evdev' for 'Video Bus'
[     6.758] (**) Video Bus: always reports core events
[     6.758] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     6.758] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.758] (--) evdev: Video Bus: Found keys
[     6.758] (II) evdev: Video Bus: Configuring as keyboard
[     6.758] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event5"
[     6.758] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     6.758] (**) Option "xkb_rules" "evdev"
[     6.758] (**) Option "xkb_model" "pc105"
[     6.758] (**) Option "xkb_layout" "us"
[     6.759] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     6.759] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.759] (II) Using input driver 'evdev' for 'Power Button'
[     6.759] (**) Power Button: always reports core events
[     6.759] (**) evdev: Power Button: Device: "/dev/input/event0"
[     6.759] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.759] (--) evdev: Power Button: Found keys
[     6.759] (II) evdev: Power Button: Configuring as keyboard
[     6.759] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     6.759] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     6.759] (**) Option "xkb_rules" "evdev"
[     6.759] (**) Option "xkb_model" "pc105"
[     6.759] (**) Option "xkb_layout" "us"
[     6.759] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[     6.759] (II) No input driver specified, ignoring this device.
[     6.759] (II) This device may have been added with another device file.
[     6.760] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event6)
[     6.760] (II) No input driver specified, ignoring this device.
[     6.760] (II) This device may have been added with another device file.
[     6.760] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event9)
[     6.760] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[     6.760] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[     6.760] (**) Lenovo EasyCamera: always reports core events
[     6.760] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event9"
[     6.760] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[     6.760] (--) evdev: Lenovo EasyCamera: Found keys
[     6.760] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[     6.760] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input10/event9"
[     6.760] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 9)
[     6.760] (**) Option "xkb_rules" "evdev"
[     6.760] (**) Option "xkb_model" "pc105"
[     6.760] (**) Option "xkb_layout" "us"
[     6.760] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event8)
[     6.760] (II) No input driver specified, ignoring this device.
[     6.760] (II) This device may have been added with another device file.
[     6.761] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event7)
[     6.761] (II) No input driver specified, ignoring this device.
[     6.761] (II) This device may have been added with another device file.
[     6.761] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     6.761] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     6.761] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     6.761] (**) AT Translated Set 2 keyboard: always reports core events
[     6.761] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     6.761] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     6.761] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     6.761] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     6.761] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     6.761] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[     6.761] (**) Option "xkb_rules" "evdev"
[     6.761] (**) Option "xkb_model" "pc105"
[     6.761] (**) Option "xkb_layout" "us"
[     6.761] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[     6.761] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     6.761] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     6.761] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     6.761] (II) LoadModule: "synaptics"
[     6.762] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.762] (II) Module synaptics: vendor="X.Org Foundation"
[     6.762]     compiled for 1.15.0, module version = 1.7.4
[     6.762]     Module class: X.Org XInput Driver
[     6.762]     ABI class: X.Org XInput driver, version 20.0
[     6.762] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     6.762] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.762] (**) Option "Device" "/dev/input/event4"
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1314 - 5670 (res 44)
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1098 - 4794 (res 76)
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     6.796] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.796] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.808] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[     6.808] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[     6.808] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     6.808] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     6.808] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[     6.808] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     6.808] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     6.808] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     6.808] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     6.809] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.809] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     6.809] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     6.813] (II) fglrx(0): System Power Source: AC
[     6.816] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[     7.562] (WW) fglrx(0): Failed to get EDID by ACPI
[     7.563] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     7.563] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.563] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     7.904] (WW) fglrx(0): Failed to get EDID by ACPI
[     7.904] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     7.904] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.904] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    14.236] (WW) fglrx(0): Failed to get EDID by ACPI
[    14.236] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    14.236] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.236] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    14.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.594] (WW) fglrx(0): Failed to get EDID by ACPI
[    14.594] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    14.594] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.594] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    14.688] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.745] (WW) fglrx(0): Failed to get EDID by ACPI
[    14.745] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    14.745] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.745] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    14.840] (WW) fglrx(0): Failed to get EDID by ACPI
[    14.841] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    14.841] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.841] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    15.300] (WW) fglrx(0): Failed to get EDID by ACPI
[    15.300] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    15.301] (II) fglrx(0): Printing DDC gathered Modelines:
[    15.301] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    30.101] (WW) fglrx(0): Failed to get EDID by ACPI
[    30.101] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    30.101] (II) fglrx(0): Printing DDC gathered Modelines:
[    30.101] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
```

```
jason@Jason-Laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


```
```
jason@Jason-Laptop:~$ uname -r
3.13.0-67-generic


```
```
jason@Jason-Laptop:~$ sudo ubuntu-drivers devices
[sudo] password for jason: 
== /sys/devices/pci0000:00/0000:00:01.0 ==
vendor   : Advanced Micro Devices, Inc. [AMD/ATI]
modalias : pci:v00001002d0000130Asv000017AAsd00003988bc03sc00i00
driver   : xserver-xorg-video-ati - distro free builtin recommended
driver   : fglrx-updates - third-party non-free
driver   : fglrx - third-party non-free


```
```
jason@Jason-Laptop:~$ sudo ubuntu-drivers list
fglrx-updates
fglrx
```

```
jason@Jason-Laptop:~$ sudo lshw -C display
PCI (sysfs)  


```

The error did not occur on this reboot so it may have just taken a full cycle? Thank you so much for your willingness to help, it is greatly appreciated, I am sure you get many thanks but understand that I truly truly mean it.  
This had to be a separate post because ever 10 minutes or so my wifi will stop responding... One problem at a time.

---

### Post by Bashing-om on 2015-11-06
chewycwook; Uh Huh ...

> 
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=32b04715-c08d-43ed-b2d1-b491f4aef2f0 ro [color=red]nomodeset[/color] quiet splash vt.handoff=7


With the boot parameter ' nomodeset' in place kernel mode setting is disabled such that the driver can not be loaded .

Remove that option form the /etc/default/grub config file and
```

sudo update-grub

```
For the change to propagate.

Reboot to see the effect.

Does FGLRX now kick in ?

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-06
I added no modset, however the error remains...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
this is now the grub file

/etc/default/grub contains:  with no nomodset...
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

where do i type the kernal command?

What file contains BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=32b04715-c08d-43ed-b2d1-b491f4aef2f0 ro [COLOR=red]nomodeset[/COLOR] quiet splash vt.handoff=7?  i cannot find it

---

### Post by Bashing-om on 2015-11-07
chewycwook; Morning;

nomodeset boot parameter:
I had "assumed" that you had made an edit to the /etc/default/grub config file for this parameter. I see you have not, so I again assume another, that you add that nomodeset parameter at the time you boot, from the boot parameter screen (?).

So, what results when you attempt to boot normally ?
Can you boot to a terminal ( at the GUI login screen - key combo ctl+alt+F1) ? As I am not looking over your shoulder and can not see your screen, you must tell me what is happening and what you are doing.

If you are able to boot to a terminal, then we know that the problem lies within that X layer on top of the kernel. We work to find out where this fault lies.

I do need to see the log file of this fresh boot :
```

cat /var/log/Xorg.0.log

```

And also what the condition of the graphic's driver is :
```

sudo lshw -C display

```
This command takes a bit of time to complete, the system must re-check the hardware and what is loaded, takes it a bit of time .

And while we are checking, we check that "you" are authorized to access your home directory:
```

ls -al /home
ls -al .Xauthority
ls -al .ICEauthority

```

We are making good progress isolating the fault.

[INDENT][INDENT]carry on, smartly
[/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-07
Good afternoon!

The output of Cat /var/log/Xorg.0.log:
```
[     4.708] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     4.708] X Protocol Version 11, Revision 0
[     4.708] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     4.708] Current Operating System: Linux Jason-Laptop 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64
[     4.709] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=32b04715-c08d-43ed-b2d1-b491f4aef2f0 ro quiet splash vt.handoff=7
[     4.709] Build Date: 12 February 2015  02:49:29PM
[     4.709] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     4.709] Current version of pixman: 0.30.2
[     4.709]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.709] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.709] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  7 18:38:15 2015
[     4.709] (==) Using config file: "/etc/X11/xorg.conf"
[     4.709] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.709] (==) ServerLayout "aticonfig Layout"
[     4.709] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     4.709] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     4.709] (**) |   |-->Device "aticonfig-Device[0]-0"
[     4.709] (==) Automatically adding devices
[     4.709] (==) Automatically enabling devices
[     4.709] (==) Automatically adding GPU devices
[     4.709] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.709]     Entry deleted from font path.
[     4.709] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.709]     Entry deleted from font path.
[     4.709] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.709]     Entry deleted from font path.
[     4.710] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.710] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.710] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.710] (II) Loader magic: 0x7f08283bdd40
[     4.710] (II) Module ABI versions:
[     4.710]     X.Org ANSI C Emulation: 0.4
[     4.710]     X.Org Video Driver: 15.0
[     4.710]     X.Org XInput driver : 20.0
[     4.710]     X.Org Server Extension : 8.0
[     4.712] (--) PCI:*(0:0:1:0) 1002:130a:17aa:3988 rev 0, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xf0a00000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[     4.712] Initializing built-in extension Generic Event Extension
[     4.712] Initializing built-in extension SHAPE
[     4.712] Initializing built-in extension MIT-SHM
[     4.712] Initializing built-in extension XInputExtension
[     4.712] Initializing built-in extension XTEST
[     4.712] Initializing built-in extension BIG-REQUESTS
[     4.712] Initializing built-in extension SYNC
[     4.712] Initializing built-in extension XKEYBOARD
[     4.712] Initializing built-in extension XC-MISC
[     4.712] Initializing built-in extension SECURITY
[     4.712] Initializing built-in extension XINERAMA
[     4.712] Initializing built-in extension XFIXES
[     4.712] Initializing built-in extension RENDER
[     4.712] Initializing built-in extension RANDR
[     4.712] Initializing built-in extension COMPOSITE
[     4.712] Initializing built-in extension DAMAGE
[     4.712] Initializing built-in extension MIT-SCREEN-SAVER
[     4.712] Initializing built-in extension DOUBLE-BUFFER
[     4.712] Initializing built-in extension RECORD
[     4.712] Initializing built-in extension DPMS
[     4.712] Initializing built-in extension Present
[     4.713] Initializing built-in extension DRI3
[     4.713] Initializing built-in extension X-Resource
[     4.713] Initializing built-in extension XVideo
[     4.713] Initializing built-in extension XVideo-MotionCompensation
[     4.713] Initializing built-in extension SELinux
[     4.713] Initializing built-in extension XFree86-VidModeExtension
[     4.713] Initializing built-in extension XFree86-DGA
[     4.713] Initializing built-in extension XFree86-DRI
[     4.713] Initializing built-in extension DRI2
[     4.713] (II) "glx" will be loaded by default.
[     4.713] (WW) "xmir" is not to be loaded by default. Skipping.
[     4.713] (II) LoadModule: "glx"
[     4.713] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     4.713] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     4.713]     compiled for 6.9.0, module version = 1.0.0
[     4.713] Loading extension GLX
[     4.713] (II) LoadModule: "fglrx"
[     4.714] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.743] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     4.743]     compiled for 1.4.99.906, module version = 15.20.2
[     4.743]     Module class: X.Org Video Driver
[     4.743] (II) Loading sub module "fglrxdrm"
[     4.743] (II) LoadModule: "fglrxdrm"
[     4.744] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     4.745] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     4.745]     compiled for 1.4.99.906, module version = 15.20.2
[     4.745] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[     4.745] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[     4.745] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[     4.745] (++) using VT number 7

[     4.745] (WW) Falling back to old probe method for fglrx
[     4.774] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     4.777] ukiDynamicMajor: found major device number 251
[     4.777] ukiDynamicMajor: found major device number 251
[     4.777] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     4.777] ukiOpenDevice: node name is /dev/ati/card0
[     4.777] ukiOpenDevice: open result is 9, (OK)
[     5.244] ukiOpenByBusid: ukiOpenMinor returns 9
[     5.244] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.249] (--) Chipset Supported AMD Graphics Processor (0x130A) found
[     5.249] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[     5.250] (II) fglrx(0): pEnt->device->identifier=0x7f08287f73e0
[     5.250] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[     5.251] (II) fglrx(0): FB driver is enabled
[     5.251] (II) Loading sub module "vgahw"
[     5.251] (II) LoadModule: "vgahw"
[     5.254] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     5.254] (II) Module vgahw: vendor="X.Org Foundation"
[     5.254]     compiled for 1.15.1, module version = 0.1.0
[     5.254]     ABI class: X.Org Video Driver, version 15.0
[     5.255] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     5.255] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     5.255] (==) fglrx(0): Default visual is TrueColor
[     5.255] (**) fglrx(0): Option "DPMS" "true"
[     5.255] (==) fglrx(0): RGB weight 888
[     5.255] (II) fglrx(0): Using 8 bits per RGB 
[     5.255] (==) fglrx(0): Buffer Tiling is ON
[     5.255] (II) Loading sub module "fglrxdrm"
[     5.255] (II) LoadModule: "fglrxdrm"
[     5.255] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     5.255] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     5.255]     compiled for 1.4.99.906, module version = 15.20.2
[     5.258] ukiDynamicMajor: found major device number 251
[     5.258] ukiDynamicMajor: found major device number 251
[     5.258] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     5.258] ukiOpenDevice: node name is /dev/ati/card0
[     5.258] ukiOpenDevice: open result is 11, (OK)
[     5.258] ukiOpenByBusid: ukiOpenMinor returns 11
[     5.258] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.258] (**) fglrx(0): NoAccel = NO
[     5.259] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     5.259] (--) fglrx(0): Chipset: "AMD Radeon(TM) R6 Graphics" (Chipset = 0x130a)
[     5.259] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x3988)
[     5.259] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     5.259] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     5.259] (--) fglrx(0): MMIO registers at 0xf0a00000
[     5.259] (--) fglrx(0): I/O port at 0x00003000
[     5.259] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     5.259] (II) fglrx(0): ATIF platform detected
[     5.261] (II) fglrx(0): AC Adapter is used
[     5.261] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     5.262] (II) Loading sub module "vbe"
[     5.262] (II) LoadModule: "vbe"
[     5.262] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     5.262] (II) Module vbe: vendor="X.Org Foundation"
[     5.262]     compiled for 1.15.1, module version = 1.1.0
[     5.262]     ABI class: X.Org Video Driver, version 15.0
[     5.262] (II) fglrx(0): VESA BIOS detected
[     5.262] (II) fglrx(0): VESA VBE Version 3.0
[     5.262] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     5.262] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[     5.262] (II) fglrx(0): VESA VBE OEM Software Rev: 15.40
[     5.262] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, Advanced Micro Devices, Inc.
[     5.263] (II) fglrx(0): VESA VBE OEM Product: SPECTRE
[     5.263] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     5.263] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[     5.263] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[     5.263] (II) fglrx(0): PCIE card detected
[     5.263] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     5.263] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     5.263] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x40000000)
[     5.263] (II) fglrx(0): RandR 1.2 support is enabled!
[     5.263] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     5.263] (II) Loading sub module "fb"
[     5.263] (II) LoadModule: "fb"
[     5.263] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.263] (II) Module fb: vendor="X.Org Foundation"
[     5.263]     compiled for 1.15.1, module version = 1.0.0
[     5.263]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.263] (II) fglrx(0): EDID Management option: EDID Management is enabled
[     5.263] (II) Loading sub module "ddc"
[     5.263] (II) LoadModule: "ddc"
[     5.263] (II) Module "ddc" already built-in
[     6.023] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[     6.023] (II) fglrx(0): Output DFP1 has no monitor section
[     6.023] (II) fglrx(0): Output CRT1 has no monitor section
[     6.023] (II) Loading sub module "ddc"
[     6.023] (II) LoadModule: "ddc"
[     6.023] (II) Module "ddc" already built-in
[     6.023] (WW) fglrx(0): Failed to get EDID by ACPI
[     6.023] (II) fglrx(0): Connected Display0: LVDS
[     6.023] (II) fglrx(0): Display0 EDID data ---------------------------
[     6.023] (II) fglrx(0): Manufacturer: BOE  Model: 61d  Serial#: 0
[     6.023] (II) fglrx(0): Year: 2014  Week: 1
[     6.023] (II) fglrx(0): EDID Version: 1.4
[     6.023] (II) fglrx(0): Digital Display Input
[     6.023] (II) fglrx(0): 6 bits per channel
[     6.023] (II) fglrx(0): Digital interface is DisplayPort
[     6.023] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     6.023] (II) fglrx(0): Gamma: 2.20
[     6.023] (II) fglrx(0): No DPMS capabilities specified
[     6.023] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[     6.023] (II) fglrx(0): First detailed timing is preferred mode
[     6.023] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[     6.023] (II) fglrx(0): redX: 0.585 redY: 0.347   greenX: 0.334 greenY: 0.569
[     6.023] (II) fglrx(0): blueX: 0.164 blueY: 0.117   whiteX: 0.312 whiteY: 0.339
[     6.023] (II) fglrx(0): Manufacturer's mask: 0
[     6.023] (II) fglrx(0): Supported detailed timing:
[     6.023] (II) fglrx(0): clock: 72.3 MHz   Image Size:  309 x 173 mm
[     6.023] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     6.023] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[     6.023] (II) fglrx(0):  BOE HF
[     6.023] (II) fglrx(0):  NT156WHM-N12
[     6.023] (II) fglrx(0): EDID (in hex):
[     6.023] (II) fglrx(0):     00ffffffffffff0009e51d0600000000
[     6.023] (II) fglrx(0):     011801049522137802fb0f955855912a
[     6.023] (II) fglrx(0):     1e4f5600000001010101010101010101
[     6.023] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     6.023] (II) fglrx(0):     360035ad1000001a0000000000000000
[     6.023] (II) fglrx(0):     00000000000000000000000000fe0042
[     6.023] (II) fglrx(0):     4f452048460a202020202020000000fe
[     6.023] (II) fglrx(0):     004e5431353657484d2d4e31320a00e5
[     6.023] (II) fglrx(0): End of Display0 EDID data --------------------
[     6.023] (II) fglrx(0): Dynamic Surface Resizing Enabled
[     6.024] (WW) fglrx(0): Failed to get EDID by ACPI
[     6.024] (II) fglrx(0): EDID for output LVDS
[     6.024] (II) fglrx(0): Manufacturer: BOE  Model: 61d  Serial#: 0
[     6.024] (II) fglrx(0): Year: 2014  Week: 1
[     6.024] (II) fglrx(0): EDID Version: 1.4
[     6.024] (II) fglrx(0): Digital Display Input
[     6.024] (II) fglrx(0): 6 bits per channel
[     6.024] (II) fglrx(0): Digital interface is DisplayPort
[     6.024] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     6.024] (II) fglrx(0): Gamma: 2.20
[     6.024] (II) fglrx(0): No DPMS capabilities specified
[     6.024] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[     6.024] (II) fglrx(0): First detailed timing is preferred mode
[     6.024] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[     6.024] (II) fglrx(0): redX: 0.585 redY: 0.347   greenX: 0.334 greenY: 0.569
[     6.024] (II) fglrx(0): blueX: 0.164 blueY: 0.117   whiteX: 0.312 whiteY: 0.339
[     6.024] (II) fglrx(0): Manufacturer's mask: 0
[     6.024] (II) fglrx(0): Supported detailed timing:
[     6.024] (II) fglrx(0): clock: 72.3 MHz   Image Size:  309 x 173 mm
[     6.024] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     6.024] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[     6.024] (II) fglrx(0):  BOE HF
[     6.024] (II) fglrx(0):  NT156WHM-N12
[     6.024] (II) fglrx(0): EDID (in hex):
[     6.024] (II) fglrx(0):     00ffffffffffff0009e51d0600000000
[     6.024] (II) fglrx(0):     011801049522137802fb0f955855912a
[     6.024] (II) fglrx(0):     1e4f5600000001010101010101010101
[     6.024] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     6.024] (II) fglrx(0):     360035ad1000001a0000000000000000
[     6.024] (II) fglrx(0):     00000000000000000000000000fe0042
[     6.024] (II) fglrx(0):     4f452048460a202020202020000000fe
[     6.024] (II) fglrx(0):     004e5431353657484d2d4e31320a00e5
[     6.024] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     6.024] (II) fglrx(0): Printing DDC gathered Modelines:
[     6.024] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     6.025] (II) fglrx(0): Printing probed modes for output LVDS
[     6.025] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     6.025] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.025] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.025] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.025] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.025] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.025] (II) fglrx(0): EDID for output DFP1
[     6.025] (II) fglrx(0): EDID for output CRT1
[     6.025] (II) fglrx(0): Output LVDS connected
[     6.025] (II) fglrx(0): Output DFP1 disconnected
[     6.025] (II) fglrx(0): Output CRT1 disconnected
[     6.025] (II) fglrx(0): Using exact sizes for initial modes
[     6.025] (II) fglrx(0): Output LVDS using initial mode 1366x768
[     6.025] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     6.025] (II) fglrx(0): Display dimensions: (340, 190) mm
[     6.025] (II) fglrx(0): DPI set to (102, 102)
[     6.025] (II) fglrx(0): Eyefinity capable adapter detected.
[     6.025] (II) fglrx(0): Adapter AMD Radeon(TM) R6 Graphics has 4 configurable heads and 1 displays connected.
[     6.025] (==) fglrx(0):  PseudoColor visuals disabled
[     6.025] (II) Loading sub module "ramdac"
[     6.025] (II) LoadModule: "ramdac"
[     6.025] (II) Module "ramdac" already built-in
[     6.025] (==) fglrx(0): NoDRI = NO
[     6.025] (==) fglrx(0): Capabilities: 0x00000000
[     6.025] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     6.025] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     6.025] (==) fglrx(0): UseFastTLS=0
[     6.025] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[     6.025] (--) Depth 24 pixmap format is 32 bpp
[     6.026] Loading extension ATIFGLRXDRI
[     6.026] (II) fglrx(0): doing swlDriScreenInit
[     6.026] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     6.026] ukiDynamicMajor: found major device number 251
[     6.026] ukiDynamicMajor: found major device number 251
[     6.026] ukiDynamicMajor: found major device number 251
[     6.026] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.026] ukiOpenDevice: node name is /dev/ati/card0
[     6.026] ukiOpenDevice: open result is 12, (OK)
[     6.026] ukiOpenByBusid: ukiOpenMinor returns 12
[     6.026] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     6.026] (II) fglrx(0): [uki] DRM interface version 1.0
[     6.026] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[     6.026] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     6.026] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f08281ca000
[     6.026] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     6.026] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     6.026] (II) fglrx(0): swlDriScreenInit done
[     6.026] (II) fglrx(0): Kernel Module Version Information:
[     6.026] (II) fglrx(0):     Name: fglrx
[     6.026] (II) fglrx(0):     Version: 15.20.2
[     6.026] (II) fglrx(0):     Date: Feb 27 2015
[     6.026] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[     6.026] (II) fglrx(0): Kernel Module version matches driver.
[     6.026] (II) fglrx(0): Kernel Module Build Time Information:
[     6.026] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-67-generic
[     6.026] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[     6.026] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     6.026] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     6.027] (II) fglrx(0): [uki] register handle = 0x00004000
[     6.027] (II) fglrx(0): DRI initialization successfull
[     6.027] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x01080000
[     6.027] (==) fglrx(0): Backing store enabled
[     6.027] Loading extension FGLRXEXTENSION
[     6.027] (**) fglrx(0): DPMS enabled
[     6.028] (II) fglrx(0): Initialized in-driver Xinerama extension
[     6.028] (**) fglrx(0): Textured Video is enabled.
[     6.028] (II) LoadModule: "glesx"
[     6.028] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[     6.031] (II) Module glesx: vendor="X.Org Foundation"
[     6.031]     compiled for 1.4.99.906, module version = 1.0.0
[     6.031] Loading extension GLESX
[     6.031] (II) fglrx(0): GLESX enableFlags = 8784
[     6.031] (II) fglrx(0): GLESX is enabled
[     6.031] (II) LoadModule: "amdxmm"
[     6.031] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     6.031] (II) Module amdxmm: vendor="X.Org Foundation"
[     6.031]     compiled for 1.4.99.906, module version = 2.0.0
[     6.056] Loading extension AMDXVOPL
[     6.056] Loading extension AMDXVBA
[     6.056] (II) fglrx(0): Enable composite support successfully
[     6.056] (WW) fglrx(0): Option "VendorName" is not used
[     6.056] (WW) fglrx(0): Option "ModelName" is not used
[     6.056] (II) fglrx(0): X context handle = 0x1
[     6.056] (II) fglrx(0): [DRI] installation complete
[     6.056] (==) fglrx(0): Silken mouse enabled
[     6.056] (==) fglrx(0): Using HW cursor of display infrastructure!
[     6.056] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     6.056] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[     6.905]  IsrHwss_Dce80::UpdateHwPath ADDED displayPath Index 681036928 controllerID 0
[     6.962] (--) RandR disabled
[     6.967] (II) SELinux: Disabled on system
[     6.968] ukiDynamicMajor: found major device number 251
[     6.968] ukiDynamicMajor: found major device number 251
[     6.968] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.968] ukiOpenDevice: node name is /dev/ati/card0
[     6.968] ukiOpenDevice: open result is 13, (OK)
[     6.968] ukiOpenByBusid: ukiOpenMinor returns 13
[     6.968] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     6.968] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     6.968] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     6.968] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     6.973] ukiDynamicMajor: found major device number 251
[     6.973] ukiDynamicMajor: found major device number 251
[     6.973] ukiDynamicMajor: found major device number 251
[     6.973] ukiOpenDevice: node name is /dev/ati/card0
[     6.973] ukiOpenDevice: open result is 14, (OK)
[     6.973] ukiGetBusid returned 'PCI:0:1:0'
[     6.973] ukiOpenDevice: node name is /dev/ati/card1
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: Open failed
[     6.973] ukiOpenDevice: node name is /dev/ati/card2
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: Open failed
[     6.973] ukiOpenDevice: node name is /dev/ati/card3
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: Open failed
[     6.973] ukiOpenDevice: node name is /dev/ati/card4
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: Open failed
[     6.973] ukiOpenDevice: node name is /dev/ati/card5
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: Open failed
[     6.973] ukiOpenDevice: node name is /dev/ati/card6
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: Open failed
[     6.973] ukiOpenDevice: node name is /dev/ati/card7
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.973] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card8
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card9
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card10
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card11
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card12
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card13
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card14
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiOpenDevice: node name is /dev/ati/card15
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: open result is -1, (No such device)
[     6.974] ukiOpenDevice: Open failed
[     6.974] ukiDynamicMajor: found major device number 251
[     6.974] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.974] ukiOpenDevice: node name is /dev/ati/card0
[     6.974] ukiOpenDevice: open result is 14, (OK)
[     6.974] ukiOpenByBusid: ukiOpenMinor returns 14
[     6.974] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     7.019] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     7.020] ukiDynamicMajor: found major device number 251
[     7.020] ukiDynamicMajor: found major device number 251
[     7.020] ukiDynamicMajor: found major device number 251
[     7.020] ukiOpenDevice: node name is /dev/ati/card0
[     7.020] ukiOpenDevice: open result is 15, (OK)
[     7.020] ukiGetBusid returned 'PCI:0:1:0'
[     7.020] ukiOpenDevice: node name is /dev/ati/card1
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card2
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card3
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card4
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card5
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card6
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card7
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card8
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.020] ukiOpenDevice: Open failed
[     7.020] ukiOpenDevice: node name is /dev/ati/card9
[     7.020] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiOpenDevice: node name is /dev/ati/card10
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiOpenDevice: node name is /dev/ati/card11
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiOpenDevice: node name is /dev/ati/card12
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiOpenDevice: node name is /dev/ati/card13
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiOpenDevice: node name is /dev/ati/card14
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiOpenDevice: node name is /dev/ati/card15
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: open result is -1, (No such device)
[     7.021] ukiOpenDevice: Open failed
[     7.021] ukiDynamicMajor: found major device number 251
[     7.021] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     7.021] ukiOpenDevice: node name is /dev/ati/card0
[     7.021] ukiOpenDevice: open result is 15, (OK)
[     7.021] ukiOpenByBusid: ukiOpenMinor returns 15
[     7.021] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     7.036] (II) fglrx(0): Setting screen physical size to 361 x 203
[     7.044] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.047] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     7.047] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.047] (II) LoadModule: "evdev"
[     7.048] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.049] (II) Module evdev: vendor="X.Org Foundation"
[     7.049]     compiled for 1.15.0, module version = 2.8.2
[     7.049]     Module class: X.Org XInput Driver
[     7.049]     ABI class: X.Org XInput driver, version 20.0
[     7.049] (II) Using input driver 'evdev' for 'Power Button'
[     7.049] (**) Power Button: always reports core events
[     7.049] (**) evdev: Power Button: Device: "/dev/input/event2"
[     7.049] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.049] (--) evdev: Power Button: Found keys
[     7.049] (II) evdev: Power Button: Configuring as keyboard
[     7.049] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     7.049] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     7.049] (**) Option "xkb_rules" "evdev"
[     7.049] (**) Option "xkb_model" "pc105"
[     7.049] (**) Option "xkb_layout" "us"
[     7.050] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     7.050] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     7.050] (II) Using input driver 'evdev' for 'Video Bus'
[     7.050] (**) Video Bus: always reports core events
[     7.050] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     7.050] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     7.050] (--) evdev: Video Bus: Found keys
[     7.050] (II) evdev: Video Bus: Configuring as keyboard
[     7.050] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event5"
[     7.050] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     7.050] (**) Option "xkb_rules" "evdev"
[     7.050] (**) Option "xkb_model" "pc105"
[     7.050] (**) Option "xkb_layout" "us"
[     7.051] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.051] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.051] (II) Using input driver 'evdev' for 'Power Button'
[     7.051] (**) Power Button: always reports core events
[     7.051] (**) evdev: Power Button: Device: "/dev/input/event0"
[     7.051] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.051] (--) evdev: Power Button: Found keys
[     7.051] (II) evdev: Power Button: Configuring as keyboard
[     7.051] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     7.051] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     7.051] (**) Option "xkb_rules" "evdev"
[     7.051] (**) Option "xkb_model" "pc105"
[     7.051] (**) Option "xkb_layout" "us"
[     7.051] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[     7.051] (II) No input driver specified, ignoring this device.
[     7.051] (II) This device may have been added with another device file.
[     7.051] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event6)
[     7.051] (II) No input driver specified, ignoring this device.
[     7.051] (II) This device may have been added with another device file.
[     7.052] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event9)
[     7.052] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[     7.052] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[     7.052] (**) Lenovo EasyCamera: always reports core events
[     7.052] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event9"
[     7.052] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[     7.052] (--) evdev: Lenovo EasyCamera: Found keys
[     7.052] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[     7.052] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input10/event9"
[     7.052] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 9)
[     7.052] (**) Option "xkb_rules" "evdev"
[     7.052] (**) Option "xkb_model" "pc105"
[     7.052] (**) Option "xkb_layout" "us"
[     7.052] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event8)
[     7.052] (II) No input driver specified, ignoring this device.
[     7.053] (II) This device may have been added with another device file.
[     7.053] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event7)
[     7.053] (II) No input driver specified, ignoring this device.
[     7.053] (II) This device may have been added with another device file.
[     7.053] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     7.053] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.053] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     7.053] (**) AT Translated Set 2 keyboard: always reports core events
[     7.053] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     7.053] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     7.053] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     7.053] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     7.053] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     7.053] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[     7.053] (**) Option "xkb_rules" "evdev"
[     7.053] (**) Option "xkb_model" "pc105"
[     7.053] (**) Option "xkb_layout" "us"
[     7.054] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[     7.054] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     7.054] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     7.054] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     7.054] (II) LoadModule: "synaptics"
[     7.054] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     7.054] (II) Module synaptics: vendor="X.Org Foundation"
[     7.054]     compiled for 1.15.0, module version = 1.7.4
[     7.054]     Module class: X.Org XInput Driver
[     7.054]     ABI class: X.Org XInput driver, version 20.0
[     7.054] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     7.054] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     7.054] (**) Option "Device" "/dev/input/event4"
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1314 - 5670 (res 44)
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1098 - 4794 (res 76)
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     7.084] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     7.084] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     7.112] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[     7.112] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[     7.112] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     7.112] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     7.112] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[     7.113] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     7.113] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     7.113] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     7.113] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     7.113] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     7.113] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     7.113] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     7.118] (II) fglrx(0): System Power Source: AC
[     7.121] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[     7.762] (WW) fglrx(0): Failed to get EDID by ACPI
[     7.762] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     7.762] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.762] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     8.143] (WW) fglrx(0): Failed to get EDID by ACPI
[     8.143] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     8.143] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.143] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    10.532] (II) AIGLX: Suspending AIGLX clients for VT switch
[    10.532] (II) fglrx(0): Backup framebuffer data.
[    10.552] (II) fglrx(0): Backup complete.
```

The output of sudo lshw -C display:
```
  *-display
       description: VGA compatible controller
       product: Kaveri
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:82 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0a00000-f0a3ffff memory:f0a60000-f0a7ffff
```

The output of ls -al /home:
```
total 12
drwxr-xr-x  3 root  root  4096 Dec 26  2014 .
drwxr-xr-x 24 root  root  4096 Nov  7 18:39 ..
drwxr-xr-x 45 jason jason 4096 Nov  7 00:45 jason
```

All of the above were done after hitting ctrl+alt+F1 in the terminal.  ls -al .Xauthority and .ICEauthority both stated that there was no such file.  Now that I am logged in as usual they return
ls -al .Xauthority:
```
-rw------- 1 jason jason 57 Nov  7 18:44 .Xauthority

```

ls -al .ICEauthority:
```
-rw------- 1 jason jason 41386 Nov  7 18:44 .ICEauthority

```

When I hit ctrl+alt+f1 no errors at all displayed it dropped to a terminal asking for my username, which i assume was to be expected.
   
I feel it is worth noting that from the boot parameter screen to get ubuntu to install originally I did have to add nomodset to get the gui to load.  I am not sure where exactly it was entered and hopefully I didn't mess anything up!   I really need to take notes on what and why I do what I do...

Thank you.

---

### Post by Bashing-om on 2015-11-07
chewycwook; Well ..

"you" do have authorization to access your home -
A driver did build - 
the - possibly  broken - driver did load -

There are some things in the log file I do not understand, and perhaps should be  of concern,
however, let us try and initialize the driver :
```

sudo amdconfig --initial

```
see now what results after a reboot.

can you boot to the GUI now ?
--------------
And no harm in "nomodeset" in some cases it is needed . but once the proper graphic's driver is located and installed that parameter should be reverted. We did that. Now let's get booted to the GUI with the proprietary driver .

[INDENT][INDENT]it might happen
[/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-07
I can boot to GUI but an error displays still "System program problem detected" I hit cancel 3 times (3 separate errors?) and it disappears and everything SEEMS to be working okay.  I think something must be off to cause those errors to pop.  I wonder what it could be, it gives an option to upload the crash report, do you know where I would go to access said report?

---

### Post by Bashing-om on 2015-11-07
chewycwook; Well ... well...

Maybe the reports are nothing.
look in the /var/crash/ directory .

After looking, and you deem there is no fault worth your attention:
[http://howtoubuntu.org/how-to-disable-stop-uninstall-apport-error-reporting-in-ubuntu](http://howtoubuntu.org/how-to-disable-stop-uninstall-apport-error-reporting-in-ubuntu)
[http://www.binarytides.com/ubuntu-fix-system-program-problem-error/](http://www.binarytides.com/ubuntu-fix-system-program-problem-error/)

disable apport, as it serves no useful purpose after  release of the version .

[INDENT][INDENT]maybe now yes !
[/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-07
Ok I suppose I should just disable the message and call it good, there are 3 files which I guess explains the "hitting cancel 3 times"  I am not really sure what I am looking for but this seems like it may be useful if you could take a look, its just part of one of the files:
```
Title: ubuntu-drivers crashed with OSError in command_devices(): [Errno 5] Input/output error
UbuntuDriversDebug:
 === log messages from detection ===
 DEBUG:root:_get_db_name: output
 ID_PCI_CLASS_FROM_DATABASE=Display controller
 ID_PCI_INTERFACE_FROM_DATABASE=VGA controller
 ID_PCI_SUBCLASS_FROM_DATABASE=VGA compatible controller
 ID_VENDOR_FROM_DATABASE=Advanced Micro Devices, Inc. [AMD/ATI]
 
 
 DEBUG:root:_get_db_name(/sys/devices/pci0000:00/0000:00:01.0, pci:v00001002d0000130Asv000017AAsd00003988bc03sc00i00): vendor "Advanced Micro Devices, Inc. [AMD/ATI]", model "None"
 DEBUG:root:_get_db_name: output
 ID_PCI_CLASS_FROM_DATABASE=Display controller
 ID_PCI_INTERFACE_FROM_DATABASE=VGA controller
 ID_PCI_SUBCLASS_FROM_DATABASE=VGA compatible controller
 ID_VENDOR_FROM_DATABASE=Advanced Micro Devices, Inc. [AMD/ATI]
 
```

My thinking is if there was an error and something crashed, but it is still working forget it.  If its not broke, right?  I just wanted your opinion.  Thank you again for all of your time.

---

### Post by Bashing-om on 2015-11-07
chewycwook; Hey ...

Yes and no ..those errors are in relation to the display controller, and as I advised, there are instances in the log file that I do not understand.
A conflict in PCI assignment ?? : " [Errno 5] Input/output error " <- that is not good .

Will not hurt my feelings one bit if we find out what these conditions are.
Maybe change the proprietary graphics driver; see then if that effects a change ?

Did you run " sudo amdconfig --initial " and reboot ?

if so, and you would like to pursue this - move'n on up the learning curve - then post back a new log file.
```

cat /var/log/Xorg.0.log

```
and as well let's see if the display manager has anything to say in this matter:
```

cat .xsession-errors

```

[INDENT][INDENT]just because
[INDENT][INDENT][INDENT]inquiring minds do want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-07
cat /var/log/Xorg.0.log:
```
[     4.857] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     4.857] X Protocol Version 11, Revision 0
[     4.857] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     4.857] Current Operating System: Linux Jason-Laptop 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64
[     4.857] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=32b04715-c08d-43ed-b2d1-b491f4aef2f0 ro quiet splash vt.handoff=7
[     4.857] Build Date: 12 February 2015  02:49:29PM
[     4.857] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     4.857] Current version of pixman: 0.30.2
[     4.857]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.857] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.857] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  7 21:36:09 2015
[     4.857] (==) Using config file: "/etc/X11/xorg.conf"
[     4.857] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.858] (==) ServerLayout "aticonfig Layout"
[     4.858] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     4.858] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     4.858] (**) |   |-->Device "aticonfig-Device[0]-0"
[     4.858] (==) Automatically adding devices
[     4.858] (==) Automatically enabling devices
[     4.858] (==) Automatically adding GPU devices
[     4.858] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.858]     Entry deleted from font path.
[     4.858] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.858]     Entry deleted from font path.
[     4.858] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.858]     Entry deleted from font path.
[     4.858] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.858]     Entry deleted from font path.
[     4.858] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.858]     Entry deleted from font path.
[     4.858] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.858] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.858] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.858] (II) Loader magic: 0x7f05bf09dd40
[     4.858] (II) Module ABI versions:
[     4.858]     X.Org ANSI C Emulation: 0.4
[     4.858]     X.Org Video Driver: 15.0
[     4.858]     X.Org XInput driver : 20.0
[     4.858]     X.Org Server Extension : 8.0
[     4.861] (--) PCI:*(0:0:1:0) 1002:130a:17aa:3988 rev 0, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xf0a00000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[     4.861] Initializing built-in extension Generic Event Extension
[     4.861] Initializing built-in extension SHAPE
[     4.861] Initializing built-in extension MIT-SHM
[     4.861] Initializing built-in extension XInputExtension
[     4.861] Initializing built-in extension XTEST
[     4.861] Initializing built-in extension BIG-REQUESTS
[     4.861] Initializing built-in extension SYNC
[     4.861] Initializing built-in extension XKEYBOARD
[     4.861] Initializing built-in extension XC-MISC
[     4.861] Initializing built-in extension SECURITY
[     4.861] Initializing built-in extension XINERAMA
[     4.861] Initializing built-in extension XFIXES
[     4.861] Initializing built-in extension RENDER
[     4.861] Initializing built-in extension RANDR
[     4.861] Initializing built-in extension COMPOSITE
[     4.861] Initializing built-in extension DAMAGE
[     4.861] Initializing built-in extension MIT-SCREEN-SAVER
[     4.861] Initializing built-in extension DOUBLE-BUFFER
[     4.861] Initializing built-in extension RECORD
[     4.861] Initializing built-in extension DPMS
[     4.861] Initializing built-in extension Present
[     4.861] Initializing built-in extension DRI3
[     4.861] Initializing built-in extension X-Resource
[     4.861] Initializing built-in extension XVideo
[     4.861] Initializing built-in extension XVideo-MotionCompensation
[     4.861] Initializing built-in extension SELinux
[     4.861] Initializing built-in extension XFree86-VidModeExtension
[     4.861] Initializing built-in extension XFree86-DGA
[     4.861] Initializing built-in extension XFree86-DRI
[     4.861] Initializing built-in extension DRI2
[     4.861] (II) "glx" will be loaded by default.
[     4.861] (WW) "xmir" is not to be loaded by default. Skipping.
[     4.861] (II) LoadModule: "glx"
[     4.861] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     4.862] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     4.862]     compiled for 6.9.0, module version = 1.0.0
[     4.862] Loading extension GLX
[     4.862] (II) LoadModule: "fglrx"
[     4.862] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.895] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     4.895]     compiled for 1.4.99.906, module version = 15.20.2
[     4.895]     Module class: X.Org Video Driver
[     4.896] (II) Loading sub module "fglrxdrm"
[     4.896] (II) LoadModule: "fglrxdrm"
[     4.896] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     4.898] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     4.898]     compiled for 1.4.99.906, module version = 15.20.2
[     4.898] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[     4.898] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[     4.898] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[     4.898] (++) using VT number 7

[     4.898] (WW) Falling back to old probe method for fglrx
[     4.929] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     4.933] ukiDynamicMajor: found major device number 251
[     4.933] ukiDynamicMajor: found major device number 251
[     4.933] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     4.933] ukiOpenDevice: node name is /dev/ati/card0
[     4.933] ukiOpenDevice: open result is 9, (OK)
[     5.428] ukiOpenByBusid: ukiOpenMinor returns 9
[     5.428] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.433] (--) Chipset Supported AMD Graphics Processor (0x130A) found
[     5.433] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[     5.434] (II) fglrx(0): pEnt->device->identifier=0x7f05bff733e0
[     5.434] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[     5.434] (II) fglrx(0): FB driver is enabled
[     5.435] (II) Loading sub module "vgahw"
[     5.435] (II) LoadModule: "vgahw"
[     5.438] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     5.438] (II) Module vgahw: vendor="X.Org Foundation"
[     5.438]     compiled for 1.15.1, module version = 0.1.0
[     5.438]     ABI class: X.Org Video Driver, version 15.0
[     5.439] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     5.439] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     5.439] (==) fglrx(0): Default visual is TrueColor
[     5.439] (**) fglrx(0): Option "DPMS" "true"
[     5.439] (==) fglrx(0): RGB weight 888
[     5.439] (II) fglrx(0): Using 8 bits per RGB 
[     5.439] (==) fglrx(0): Buffer Tiling is ON
[     5.439] (II) Loading sub module "fglrxdrm"
[     5.439] (II) LoadModule: "fglrxdrm"
[     5.439] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     5.439] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     5.439]     compiled for 1.4.99.906, module version = 15.20.2
[     5.442] ukiDynamicMajor: found major device number 251
[     5.442] ukiDynamicMajor: found major device number 251
[     5.442] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     5.442] ukiOpenDevice: node name is /dev/ati/card0
[     5.442] ukiOpenDevice: open result is 11, (OK)
[     5.442] ukiOpenByBusid: ukiOpenMinor returns 11
[     5.442] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     5.442] (**) fglrx(0): NoAccel = NO
[     5.442] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     5.442] (--) fglrx(0): Chipset: "AMD Radeon(TM) R6 Graphics" (Chipset = 0x130a)
[     5.442] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x3988)
[     5.442] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     5.442] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     5.442] (--) fglrx(0): MMIO registers at 0xf0a00000
[     5.443] (--) fglrx(0): I/O port at 0x00003000
[     5.443] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     5.443] (II) fglrx(0): ATIF platform detected
[     5.444] (II) fglrx(0): AC Adapter is used
[     5.445] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     5.445] (II) Loading sub module "vbe"
[     5.445] (II) LoadModule: "vbe"
[     5.445] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     5.446] (II) Module vbe: vendor="X.Org Foundation"
[     5.446]     compiled for 1.15.1, module version = 1.1.0
[     5.446]     ABI class: X.Org Video Driver, version 15.0
[     5.446] (II) fglrx(0): VESA BIOS detected
[     5.446] (II) fglrx(0): VESA VBE Version 3.0
[     5.446] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     5.446] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[     5.446] (II) fglrx(0): VESA VBE OEM Software Rev: 15.40
[     5.446] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, Advanced Micro Devices, Inc.
[     5.446] (II) fglrx(0): VESA VBE OEM Product: SPECTRE
[     5.446] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     5.446] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[     5.446] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[     5.446] (II) fglrx(0): PCIE card detected
[     5.446] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     5.446] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     5.446] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x40000000)
[     5.446] (II) fglrx(0): RandR 1.2 support is enabled!
[     5.446] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     5.446] (II) Loading sub module "fb"
[     5.446] (II) LoadModule: "fb"
[     5.446] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.447] (II) Module fb: vendor="X.Org Foundation"
[     5.447]     compiled for 1.15.1, module version = 1.0.0
[     5.447]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.447] (II) fglrx(0): EDID Management option: EDID Management is enabled
[     5.447] (II) Loading sub module "ddc"
[     5.447] (II) LoadModule: "ddc"
[     5.447] (II) Module "ddc" already built-in
[     6.131] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[     6.131] (II) fglrx(0): Output DFP1 has no monitor section
[     6.131] (II) fglrx(0): Output CRT1 has no monitor section
[     6.131] (II) Loading sub module "ddc"
[     6.131] (II) LoadModule: "ddc"
[     6.131] (II) Module "ddc" already built-in
[     6.131] (WW) fglrx(0): Failed to get EDID by ACPI
[     6.131] (II) fglrx(0): Connected Display0: LVDS
[     6.131] (II) fglrx(0): Display0 EDID data ---------------------------
[     6.131] (II) fglrx(0): Manufacturer: BOE  Model: 61d  Serial#: 0
[     6.131] (II) fglrx(0): Year: 2014  Week: 1
[     6.131] (II) fglrx(0): EDID Version: 1.4
[     6.131] (II) fglrx(0): Digital Display Input
[     6.131] (II) fglrx(0): 6 bits per channel
[     6.131] (II) fglrx(0): Digital interface is DisplayPort
[     6.131] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     6.131] (II) fglrx(0): Gamma: 2.20
[     6.131] (II) fglrx(0): No DPMS capabilities specified
[     6.131] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[     6.131] (II) fglrx(0): First detailed timing is preferred mode
[     6.131] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[     6.131] (II) fglrx(0): redX: 0.585 redY: 0.347   greenX: 0.334 greenY: 0.569
[     6.132] (II) fglrx(0): blueX: 0.164 blueY: 0.117   whiteX: 0.312 whiteY: 0.339
[     6.132] (II) fglrx(0): Manufacturer's mask: 0
[     6.132] (II) fglrx(0): Supported detailed timing:
[     6.132] (II) fglrx(0): clock: 72.3 MHz   Image Size:  309 x 173 mm
[     6.132] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     6.132] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[     6.132] (II) fglrx(0):  BOE HF
[     6.132] (II) fglrx(0):  NT156WHM-N12
[     6.132] (II) fglrx(0): EDID (in hex):
[     6.132] (II) fglrx(0):     00ffffffffffff0009e51d0600000000
[     6.132] (II) fglrx(0):     011801049522137802fb0f955855912a
[     6.132] (II) fglrx(0):     1e4f5600000001010101010101010101
[     6.132] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     6.132] (II) fglrx(0):     360035ad1000001a0000000000000000
[     6.132] (II) fglrx(0):     00000000000000000000000000fe0042
[     6.132] (II) fglrx(0):     4f452048460a202020202020000000fe
[     6.132] (II) fglrx(0):     004e5431353657484d2d4e31320a00e5
[     6.132] (II) fglrx(0): End of Display0 EDID data --------------------
[     6.132] (II) fglrx(0): Dynamic Surface Resizing Enabled
[     6.132] (WW) fglrx(0): Failed to get EDID by ACPI
[     6.132] (II) fglrx(0): EDID for output LVDS
[     6.132] (II) fglrx(0): Manufacturer: BOE  Model: 61d  Serial#: 0
[     6.132] (II) fglrx(0): Year: 2014  Week: 1
[     6.132] (II) fglrx(0): EDID Version: 1.4
[     6.132] (II) fglrx(0): Digital Display Input
[     6.132] (II) fglrx(0): 6 bits per channel
[     6.132] (II) fglrx(0): Digital interface is DisplayPort
[     6.132] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     6.132] (II) fglrx(0): Gamma: 2.20
[     6.132] (II) fglrx(0): No DPMS capabilities specified
[     6.132] (II) fglrx(0): Supported color encodings: RGB 4:4:4 
[     6.132] (II) fglrx(0): First detailed timing is preferred mode
[     6.132] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[     6.132] (II) fglrx(0): redX: 0.585 redY: 0.347   greenX: 0.334 greenY: 0.569
[     6.133] (II) fglrx(0): blueX: 0.164 blueY: 0.117   whiteX: 0.312 whiteY: 0.339
[     6.133] (II) fglrx(0): Manufacturer's mask: 0
[     6.133] (II) fglrx(0): Supported detailed timing:
[     6.133] (II) fglrx(0): clock: 72.3 MHz   Image Size:  309 x 173 mm
[     6.133] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     6.133] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[     6.133] (II) fglrx(0):  BOE HF
[     6.133] (II) fglrx(0):  NT156WHM-N12
[     6.133] (II) fglrx(0): EDID (in hex):
[     6.133] (II) fglrx(0):     00ffffffffffff0009e51d0600000000
[     6.133] (II) fglrx(0):     011801049522137802fb0f955855912a
[     6.133] (II) fglrx(0):     1e4f5600000001010101010101010101
[     6.133] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     6.133] (II) fglrx(0):     360035ad1000001a0000000000000000
[     6.133] (II) fglrx(0):     00000000000000000000000000fe0042
[     6.133] (II) fglrx(0):     4f452048460a202020202020000000fe
[     6.133] (II) fglrx(0):     004e5431353657484d2d4e31320a00e5
[     6.133] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     6.133] (II) fglrx(0): Printing DDC gathered Modelines:
[     6.133] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     6.133] (II) fglrx(0): Printing probed modes for output LVDS
[     6.133] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     6.133] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.133] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.133] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.133] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.133] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 777 790 +hsync -vsync (47.4 kHz e)
[     6.133] (II) fglrx(0): EDID for output DFP1
[     6.133] (II) fglrx(0): EDID for output CRT1
[     6.133] (II) fglrx(0): Output LVDS connected
[     6.133] (II) fglrx(0): Output DFP1 disconnected
[     6.133] (II) fglrx(0): Output CRT1 disconnected
[     6.133] (II) fglrx(0): Using exact sizes for initial modes
[     6.133] (II) fglrx(0): Output LVDS using initial mode 1366x768
[     6.133] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     6.133] (II) fglrx(0): Display dimensions: (340, 190) mm
[     6.133] (II) fglrx(0): DPI set to (102, 102)
[     6.133] (II) fglrx(0): Eyefinity capable adapter detected.
[     6.133] (II) fglrx(0): Adapter AMD Radeon(TM) R6 Graphics has 4 configurable heads and 1 displays connected.
[     6.133] (==) fglrx(0):  PseudoColor visuals disabled
[     6.133] (II) Loading sub module "ramdac"
[     6.133] (II) LoadModule: "ramdac"
[     6.133] (II) Module "ramdac" already built-in
[     6.133] (==) fglrx(0): NoDRI = NO
[     6.133] (==) fglrx(0): Capabilities: 0x00000000
[     6.133] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     6.133] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     6.133] (==) fglrx(0): UseFastTLS=0
[     6.133] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[     6.133] (--) Depth 24 pixmap format is 32 bpp
[     6.134] Loading extension ATIFGLRXDRI
[     6.134] (II) fglrx(0): doing swlDriScreenInit
[     6.134] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     6.134] ukiDynamicMajor: found major device number 251
[     6.134] ukiDynamicMajor: found major device number 251
[     6.134] ukiDynamicMajor: found major device number 251
[     6.134] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     6.134] ukiOpenDevice: node name is /dev/ati/card0
[     6.134] ukiOpenDevice: open result is 12, (OK)
[     6.134] ukiOpenByBusid: ukiOpenMinor returns 12
[     6.134] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     6.134] (II) fglrx(0): [uki] DRM interface version 1.0
[     6.134] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[     6.134] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     6.134] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f05beeaa000
[     6.134] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     6.135] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     6.135] (II) fglrx(0): swlDriScreenInit done
[     6.135] (II) fglrx(0): Kernel Module Version Information:
[     6.135] (II) fglrx(0):     Name: fglrx
[     6.135] (II) fglrx(0):     Version: 15.20.2
[     6.135] (II) fglrx(0):     Date: Feb 27 2015
[     6.135] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[     6.135] (II) fglrx(0): Kernel Module version matches driver.
[     6.135] (II) fglrx(0): Kernel Module Build Time Information:
[     6.135] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-67-generic
[     6.135] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[     6.135] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     6.135] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     6.135] (II) fglrx(0): [uki] register handle = 0x00004000
[     6.135] (II) fglrx(0): DRI initialization successfull
[     6.135] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x01080000
[     6.136] (==) fglrx(0): Backing store enabled
[     6.136] Loading extension FGLRXEXTENSION
[     6.136] (**) fglrx(0): DPMS enabled
[     6.136] (II) fglrx(0): Initialized in-driver Xinerama extension
[     6.136] (**) fglrx(0): Textured Video is enabled.
[     6.136] (II) LoadModule: "glesx"
[     6.136] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[     6.139] (II) Module glesx: vendor="X.Org Foundation"
[     6.139]     compiled for 1.4.99.906, module version = 1.0.0
[     6.139] Loading extension GLESX
[     6.139] (II) fglrx(0): GLESX enableFlags = 8784
[     6.139] (II) fglrx(0): GLESX is enabled
[     6.139] (II) LoadModule: "amdxmm"
[     6.139] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     6.140] (II) Module amdxmm: vendor="X.Org Foundation"
[     6.140]     compiled for 1.4.99.906, module version = 2.0.0
[     6.164] Loading extension AMDXVOPL
[     6.164] Loading extension AMDXVBA
[     6.164] (II) fglrx(0): Enable composite support successfully
[     6.164] (WW) fglrx(0): Option "VendorName" is not used
[     6.164] (WW) fglrx(0): Option "ModelName" is not used
[     6.164] (II) fglrx(0): X context handle = 0x1
[     6.164] (II) fglrx(0): [DRI] installation complete
[     6.164] (==) fglrx(0): Silken mouse enabled
[     6.164] (==) fglrx(0): Using HW cursor of display infrastructure!
[     6.164] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     6.164] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[     7.007]  IsrHwss_Dce80::UpdateHwPath ADDED displayPath Index -1072716992 controllerID 0
[     7.073] (--) RandR disabled
[     7.079] (II) SELinux: Disabled on system
[     7.080] ukiDynamicMajor: found major device number 251
[     7.080] ukiDynamicMajor: found major device number 251
[     7.080] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     7.080] ukiOpenDevice: node name is /dev/ati/card0
[     7.080] ukiOpenDevice: open result is 13, (OK)
[     7.080] ukiOpenByBusid: ukiOpenMinor returns 13
[     7.080] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     7.080] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     7.080] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     7.080] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     7.085] ukiDynamicMajor: found major device number 251
[     7.085] ukiDynamicMajor: found major device number 251
[     7.085] ukiDynamicMajor: found major device number 251
[     7.085] ukiOpenDevice: node name is /dev/ati/card0
[     7.085] ukiOpenDevice: open result is 14, (OK)
[     7.085] ukiGetBusid returned 'PCI:0:1:0'
[     7.085] ukiOpenDevice: node name is /dev/ati/card1
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card2
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card3
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card4
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card5
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card6
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card7
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card8
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card9
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card10
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card11
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.085] ukiOpenDevice: node name is /dev/ati/card12
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: open result is -1, (No such device)
[     7.085] ukiOpenDevice: Open failed
[     7.086] ukiOpenDevice: node name is /dev/ati/card13
[     7.086] ukiOpenDevice: open result is -1, (No such device)
[     7.086] ukiOpenDevice: open result is -1, (No such device)
[     7.086] ukiOpenDevice: Open failed
[     7.086] ukiOpenDevice: node name is /dev/ati/card14
[     7.086] ukiOpenDevice: open result is -1, (No such device)
[     7.086] ukiOpenDevice: open result is -1, (No such device)
[     7.086] ukiOpenDevice: Open failed
[     7.086] ukiOpenDevice: node name is /dev/ati/card15
[     7.086] ukiOpenDevice: open result is -1, (No such device)
[     7.086] ukiOpenDevice: open result is -1, (No such device)
[     7.086] ukiOpenDevice: Open failed
[     7.086] ukiDynamicMajor: found major device number 251
[     7.086] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     7.086] ukiOpenDevice: node name is /dev/ati/card0
[     7.086] ukiOpenDevice: open result is 14, (OK)
[     7.086] ukiOpenByBusid: ukiOpenMinor returns 14
[     7.086] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     7.132] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     7.133] ukiDynamicMajor: found major device number 251
[     7.133] ukiDynamicMajor: found major device number 251
[     7.133] ukiDynamicMajor: found major device number 251
[     7.133] ukiOpenDevice: node name is /dev/ati/card0
[     7.133] ukiOpenDevice: open result is 15, (OK)
[     7.133] ukiGetBusid returned 'PCI:0:1:0'
[     7.133] ukiOpenDevice: node name is /dev/ati/card1
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card2
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card3
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card4
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card5
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card6
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card7
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card8
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card9
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card10
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card11
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card12
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card13
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card14
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiOpenDevice: node name is /dev/ati/card15
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: open result is -1, (No such device)
[     7.134] ukiOpenDevice: Open failed
[     7.134] ukiDynamicMajor: found major device number 251
[     7.134] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[     7.134] ukiOpenDevice: node name is /dev/ati/card0
[     7.135] ukiOpenDevice: open result is 15, (OK)
[     7.135] ukiOpenByBusid: ukiOpenMinor returns 15
[     7.135] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[     7.149] (II) fglrx(0): Setting screen physical size to 361 x 203
[     7.157] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.161] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     7.161] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.161] (II) LoadModule: "evdev"
[     7.161] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.162] (II) Module evdev: vendor="X.Org Foundation"
[     7.162]     compiled for 1.15.0, module version = 2.8.2
[     7.162]     Module class: X.Org XInput Driver
[     7.162]     ABI class: X.Org XInput driver, version 20.0
[     7.162] (II) Using input driver 'evdev' for 'Power Button'
[     7.162] (**) Power Button: always reports core events
[     7.162] (**) evdev: Power Button: Device: "/dev/input/event2"
[     7.162] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.162] (--) evdev: Power Button: Found keys
[     7.162] (II) evdev: Power Button: Configuring as keyboard
[     7.162] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     7.162] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     7.162] (**) Option "xkb_rules" "evdev"
[     7.162] (**) Option "xkb_model" "pc105"
[     7.162] (**) Option "xkb_layout" "us"
[     7.163] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     7.163] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     7.163] (II) Using input driver 'evdev' for 'Video Bus'
[     7.163] (**) Video Bus: always reports core events
[     7.163] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     7.163] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     7.163] (--) evdev: Video Bus: Found keys
[     7.163] (II) evdev: Video Bus: Configuring as keyboard
[     7.163] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event5"
[     7.163] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     7.163] (**) Option "xkb_rules" "evdev"
[     7.163] (**) Option "xkb_model" "pc105"
[     7.163] (**) Option "xkb_layout" "us"
[     7.163] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.163] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.163] (II) Using input driver 'evdev' for 'Power Button'
[     7.163] (**) Power Button: always reports core events
[     7.163] (**) evdev: Power Button: Device: "/dev/input/event0"
[     7.163] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.163] (--) evdev: Power Button: Found keys
[     7.163] (II) evdev: Power Button: Configuring as keyboard
[     7.163] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     7.164] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     7.164] (**) Option "xkb_rules" "evdev"
[     7.164] (**) Option "xkb_model" "pc105"
[     7.164] (**) Option "xkb_layout" "us"
[     7.164] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[     7.164] (II) No input driver specified, ignoring this device.
[     7.164] (II) This device may have been added with another device file.
[     7.164] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event6)
[     7.164] (II) No input driver specified, ignoring this device.
[     7.164] (II) This device may have been added with another device file.
[     7.165] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event7)
[     7.165] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[     7.165] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[     7.165] (**) Lenovo EasyCamera: always reports core events
[     7.165] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event7"
[     7.165] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[     7.165] (--) evdev: Lenovo EasyCamera: Found keys
[     7.165] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[     7.165] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input8/event7"
[     7.165] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 9)
[     7.165] (**) Option "xkb_rules" "evdev"
[     7.165] (**) Option "xkb_model" "pc105"
[     7.165] (**) Option "xkb_layout" "us"
[     7.165] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event8)
[     7.165] (II) No input driver specified, ignoring this device.
[     7.165] (II) This device may have been added with another device file.
[     7.165] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event9)
[     7.165] (II) No input driver specified, ignoring this device.
[     7.165] (II) This device may have been added with another device file.
[     7.166] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     7.166] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.166] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     7.166] (**) AT Translated Set 2 keyboard: always reports core events
[     7.166] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     7.166] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     7.166] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     7.166] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     7.166] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     7.166] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[     7.166] (**) Option "xkb_rules" "evdev"
[     7.166] (**) Option "xkb_model" "pc105"
[     7.166] (**) Option "xkb_layout" "us"
[     7.166] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[     7.166] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     7.166] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     7.166] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     7.166] (II) LoadModule: "synaptics"
[     7.166] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     7.167] (II) Module synaptics: vendor="X.Org Foundation"
[     7.167]     compiled for 1.15.0, module version = 1.7.4
[     7.167]     Module class: X.Org XInput Driver
[     7.167]     ABI class: X.Org XInput driver, version 20.0
[     7.167] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     7.167] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     7.167] (**) Option "Device" "/dev/input/event4"
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1314 - 5670 (res 44)
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1098 - 4794 (res 76)
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     7.184] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     7.184] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     7.196] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[     7.196] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[     7.196] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     7.196] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     7.196] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[     7.197] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     7.197] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     7.197] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     7.197] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     7.197] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     7.197] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     7.197] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     7.202] (II) fglrx(0): System Power Source: AC
[     7.206] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[     7.930] (WW) fglrx(0): Failed to get EDID by ACPI
[     7.930] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     7.930] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.930] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[     8.390] (WW) fglrx(0): Failed to get EDID by ACPI
[     8.391] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[     8.391] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.391] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    13.388] (WW) fglrx(0): Failed to get EDID by ACPI
[    13.388] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    13.388] (II) fglrx(0): Printing DDC gathered Modelines:
[    13.388] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    13.715] (WW) fglrx(0): Failed to get EDID by ACPI
[    13.715] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    13.715] (II) fglrx(0): Printing DDC gathered Modelines:
[    13.715] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    13.748] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.794] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.829] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.860] (WW) fglrx(0): Failed to get EDID by ACPI
[    13.860] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    13.860] (II) fglrx(0): Printing DDC gathered Modelines:
[    13.860] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    13.963] (WW) fglrx(0): Failed to get EDID by ACPI
[    13.963] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    13.963] (II) fglrx(0): Printing DDC gathered Modelines:
[    13.963] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    14.586] (WW) fglrx(0): Failed to get EDID by ACPI
[    14.586] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    14.586] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.586] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    29.240] (WW) fglrx(0): Failed to get EDID by ACPI
[    29.240] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    29.240] (II) fglrx(0): Printing DDC gathered Modelines:
[    29.240] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
[    42.106] (WW) fglrx(0): Failed to get EDID by ACPI
[    42.106] (II) fglrx(0): EDID vendor "BOE", prod id 1565
[    42.106] (II) fglrx(0): Printing DDC gathered Modelines:
[    42.106] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 777 790 +hsync -vsync (47.4 kHz eP)
```

I'm always up to learn something new.  I tried the sudo ... --initial, it had the same output as non root.  I also started poking around in the AMD catalyst control center.
I did not have the error on this boot so maybe the running the initial as root or changing the settings overode something.  It may just be wishfull thinking.
 ```
jason@Jason-Laptop:~$ cat .xsession-errors
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: indicator-bluetooth main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped


```
.xsession-errors did not exist at the beginning of typing this.  Apparently my bluetooth has issues, I don't use it so that doesnt bother me.
Fingers crossed nothing stands out!

---

### Post by Bashing-om on 2015-11-07
chewycwook; K;

Late for me here. My mind is getting cloudy and forced think'n .

I pick this back up in my AM . See what we can see and work out.

Buy hey, ya got to admit  ........
[INDENT][INDENT][INDENT]look'n better
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-08
chewycwook; OK;

Reasons why I think:
> 
 4.861] (--) PCI:*(0:0:1:0) 1002:130a:17aa:3988  <- hardware found and identified
4.862] (II) LoadModule: "fglrx" <- so far so good
 4.896] (II) LoadModule: "fglrxdrm" >- yepper, still look'n good
4.896] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so <- still happy happy
4.898] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32 <- no problem yet !
4.933] ukiOpenByBusid: Searching for BusID PCI:0:1:0 <- OK !
5.428] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0 <- yeah yeah

5.433] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found <- Uh OH 

5.434] (II) fglrx(0): pEnt->device->identifier=0x7f05bff733e0 <- what have we here ?

 5.439] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so <- yepper, driver a-build'n

5.442] ukiDynamicMajor: found major device number 251 <- From OEM building ??
5.442] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0 <- so far again so good
5.442] (--) fglrx(0): Chipset: "AMD Radeon(TM) R6 Graphics" (Chipset = 0x130a)


6.131] (WW) fglrx(0): Failed to get EDID by ACPI <- Ouch ???

6.133] (II) fglrx(0): Adapter AMD Radeon(TM) R6 Graphics has 4 configurable heads and 1 displays connected. <- Oh Yeah ?


6.134] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0 <- Great
6.134] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0" <- Uh huh .. look'n good
 6.135] (II) fglrx(0):     Version: 15.20.2 <- driver built
  6.135] (II) fglrx(0): Kernel Module version matches driver. <- verified !
7.080] ukiOpenByBusid: ukiOpenMinor returns 13 <- all look'n good 


 7.080] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     7.080] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     7.080] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     7.085] <----------- Uh Oh ... What are these ? what have we here ? UnGood

7.085] ukiOpenDevice: node name is /dev/ati/card1 <- Good deal

7.085] ukiOpenDevice: open result is -1, (No such device) <- Bad Deal ??

---------- what is the system looking for ???? card 1 through card 15 -------------------

7.086] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0 <- system happy with Bus ID PCI:0:1:0  for display port

7.132] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0 <- yepper, look'n good

13.860] (WW) fglrx(0): Failed to get EDID by ACPI <- system adjusts and makes up the modlines ?>




So the driver builds and loads .. but unable to find some files / And other cards not identified ( cards 1 -15 ) .

Let's look and see what conflicts we may have and what is installed:
```

dpkg -l  linux-headers-generic 
dkms status
ls -al /usr/share/ati/
ls -al /usr/X11R6/lib64/modules/dri
dpkg -l | grep fglrx
cat /etc/X11/xorg.conf

```

Could be all is well as is .. 
[INDENT][INDENT]won't hurt to look and think
[/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-08
I sure hope I'm not keeping you from anything important, feel free to abandon me at any time!

dpg -l linux-headers-generic:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                             Architecture Description
+++-=====================================================-===================================================-============-===============================================================================
ii  linux-headers-generic                                 3.13.0.67.73                                        amd64        Generic Linux kernel headers
```

dkms status:
```
fglrx-core, 15.200, 3.13.0-67-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-43-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-44-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-45-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-46-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-48-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-52-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-67-generic, x86_64: installed
rtlwifi-new, 0.5~trusty, 3.13.0-52-generic, x86_64: installed
rtlwifi-new, 0.5~trusty, 3.13.0-67-generic, x86_64: installed
virtualbox, 4.3.10, 3.13.0-52-generic, x86_64: installed
virtualbox, 4.3.10, 3.13.0-67-generic, x86_64: installed
```
Do I have 7 copies of ndiswrapper installed?

ls -al /usr/share/ati:
```
total 40
drwxr-xr-x   4 root root  4096 Nov  6 19:32 .
drwxr-xr-x 328 root root 12288 Nov  6 19:32 ..
drwxr-xr-x   2 root root  4096 Nov  6 19:32 amdcccle
-rw-r--r--   1 root root   630 Mar  6  2015 fglrx-install.log
drwxr-xr-x   2 root root  4096 Nov  6 19:32 lib64
-rw-r--r--   1 root root 10732 Mar  6  2015 LICENSE.TXT
```

```
jason@Jason-Laptop:~/Desktop$ ls -al /usr/X11R6/lib64/modules/dri/
ls: cannot access /usr/X11R6/lib64/modules/dri/: No such file or directory
jason@Jason-Laptop:~/Desktop$ 

```

dpg -l | grep fglrx
```
ii  fglrx                                                 2:15.200-0ubuntu0.5                                 amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                        2:15.200-0ubuntu0.5                                 amd64        Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-core                                            2:15.200-0ubuntu0.5                                 amd64        Minimal video driver for the AMD graphics accelerators
```


cat /etc/X11/xorg.conf:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

There was no error again on this boot, maybe, hopefully it has corrected itself... mostly.  Edit:  with your help mostly of course!

---

### Post by Bashing-om on 2015-11-08
chewycwook; Hey !

as to:
> 
I sure hope I'm not keeping you from anything important, 

This is what is important to me.

and:
> 
feel free to abandon me at any time!

not going to happen. Sometimes I do have to pause for the cause of consideration of what to do .

---------------------
> 
Do I have 7 copies of ndiswrapper installed?

7 [color=red]versions[/color] installed. Why even one version ??

> 
There was no error again on this boot, maybe, hopefully it has corrected itself... 


Hey it could be ... all the outputs look to the good .
What driver is loaded that the system is using ?
```

sudo lshw -C display

```

Reboot again and see if you have good GUI.

[INDENT][INDENT][INDENT]good things do happen[/INDENT][/INDENT][/INDENT]

---

### Post by chewycwook on 2015-11-08
```
jason@Jason-Laptop:~/Desktop$ sudo lshw -C display
[sudo] password for jason: 
  *-display               
       description: VGA compatible controller
       product: Kaveri
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:82 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0a00000-f0a3ffff memory:f0a60000-f0a7ffff


```

As far as ndiswrapper, the very first laptop I used I had to use it to make the Wifi work back in 2004 or so, got used to the process so I continued with it it wifi doesn't work out of the box.  I suppose for how long I have been using ubuntu I should no more about it but I don't really look under the hood - I have learned from this endeavour though!  Reboot to come, fingers crossed.

after reboot no errors sudo lshw -C display output is identical, I guess I can call this solved.  My wifi does act up and require me to reconnect sometimes, if you know a better way to work it than ndiswrapper and are willing to tackle a separate issue I would be happy to start a new thread.

Much appreciated for taking the time to walk me through this.

---

### Post by Bashing-om on 2015-11-09
chewycwook; Welllll ...

Pleased the graphics driver has worked out ... More power to us !

Yeah open a new thread on the WIFI issue. ndiswrapper is real old school a lot has been done with the WIFI drivers. That crutch "should" no longer be required. However, WIFI is not an area of expertise with me. Others can advise much better.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

