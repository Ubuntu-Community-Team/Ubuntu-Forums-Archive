---
title: "Blank screen when trying Ubuntu on HP 15-n028us"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by naveen-rajanikantha on 2014-01-14
Pardon me, this may already been addressed but I could not find a solution.

I am trying to install Ubuntu 13.10 on HP 15-n028us, get blank screen after grub menu.
Using unetbootin i created a boot USB, disabled fast boot and secure boot. Correctly switching to boot from USB
It gets to the grub boot menu, I choose option to try Ubuntu without installing, nothing happens just blank screen - have to press power button to reboot, Could not even get the console when issuing Alt+1/2/3...8.

I have also tried downloading a fresh ubuntu binary and recreating the USB boot drive.
I have tried editing the boot options, by adding 1) nomodeset still the same problem and 2) acpi_osi=linux acpi_backlight=vendor this one atleast gives me a linux console, but cannot get the graphical interface working.

This laptop has AMD [COLOR=#000000][FONT=HPSimplified]A6-5200 with [/FONT][/COLOR][COLOR=#000000][FONT=HPSimplified]AMD Radeon HD 8400 graphics - 6GB RAM.

I would like to Dual boot with Ubuntu and Windows 8 on this laptop. 
If anybody has run into similar problem, could you kindly share the steps/commands etc.. that solved it.
Thanks for taking a look at this issue and helping me solve this problem.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-01-14
Welcome. When you get to the screen that says 'Try Ubuntu' 'Install Ubuntu' etc., hit F6. From the options menu that pops up choose 'nomodeset'. Proceed.

Just a tip: Using descriptive titles for your threads will get you a lot more action. Generic titles like this one tell us nothing about your problem.

Something like 'Blank screen when trying Ubuntu on HP 15-n028us' would have generated more attention. You can change the title by clicking 'Edit Post' then 'Go Advanced' on the first post in the thread for half an hour after posting it. ;)

---

### Post by naveen-rajanikantha on 2014-01-16
Thanks, 

I tried the it with the boot option "nomodeset"  - still I get a black screen, but I can get a console by pressing alt+f1. Poking around in the /var/log files found that lightdm failed to start. Tried to start it from the console using "sudo service lightdm start" it still fails.
I can provide the logfiles and also the core, if that would help.

I also tried the options "acpi_osi=Linux acpi_backlight=vendor nomodeset" - even with this the result is the same, only console no graphics.

This laptop has a AMD A6-5200 which has [COLOR=#000000][FONT=HPSimplified]AMD Radeon HD 8400.

Still looking for a solution,
thanks,[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-01-16
Could you provide the error message that explains why lightdm failed to start?

You could try reinstalling it when you hit alt+ctrl+F!. 

```
sudo apt-get install lightdm
```

---

### Post by naveen-rajanikantha on 2014-01-23
It took a while to get back to work on this problem, 
Attached is the /var/log/ Xorg.0.log file with nomodeset Could't figure out how to attach a file, so pasting it inline.

Thanks for your help.
-naveen
------------------------------------------------------------
```
[    26.437] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    26.437] X Protocol Version 11, Revision 0
[    26.437] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    26.437] Current Operating System: Linux ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    26.437] Kernel command line: BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper nomodeset quiet splash --
[    26.437] Build Date: 15 October 2013  09:23:37AM
[    26.437] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.437] Current version of pixman: 0.30.2
[    26.437] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    26.437] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.437] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 23 20:56:29 2014
[    26.438] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.438] (==) No Layout section.  Using the first Screen section.
[    26.438] (==) No screen section available. Using defaults.
[    26.438] (**) |-->Screen "Default Screen Section" (0)
[    26.438] (**) |   |-->Monitor "<default monitor>"
[    26.439] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.439] (==) Automatically adding devices
[    26.439] (==) Automatically enabling devices
[    26.439] (==) Automatically adding GPU devices
[    26.439] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.439] 	Entry deleted from font path.
[    26.439] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.439] 	Entry deleted from font path.
[    26.439] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.439] 	Entry deleted from font path.
[    26.439] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.439] 	Entry deleted from font path.
[    26.439] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.439] 	Entry deleted from font path.
[    26.439] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    26.439] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.439] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.439] (II) Loader magic: 0x7fb202f4ad20
[    26.439] (II) Module ABI versions:
[    26.439] 	X.Org ANSI C Emulation: 0.4
[    26.439] 	X.Org Video Driver: 14.1
[    26.439] 	X.Org XInput driver : 19.1
[    26.439] 	X.Org Server Extension : 7.0
[    26.439] (II) xfree86: Adding drm device (/dev/dri/card0)
[    26.442] (--) PCI:*(0:0:1:0) 1002:9830:103c:216f rev 0, Mem @ 0xe0000000/268435456, 0xf0800000/8388608, 0xf0300000/262144, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    26.442] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.442] Initializing built-in extension Generic Event Extension
[    26.442] Initializing built-in extension SHAPE
[    26.442] Initializing built-in extension MIT-SHM
[    26.442] Initializing built-in extension XInputExtension
[    26.442] Initializing built-in extension XTEST
[    26.442] Initializing built-in extension BIG-REQUESTS
[    26.442] Initializing built-in extension SYNC
[    26.442] Initializing built-in extension XKEYBOARD
[    26.442] Initializing built-in extension XC-MISC
[    26.442] Initializing built-in extension SECURITY
[    26.442] Initializing built-in extension XINERAMA
[    26.442] Initializing built-in extension XFIXES
[    26.442] Initializing built-in extension RENDER
[    26.442] Initializing built-in extension RANDR
[    26.442] Initializing built-in extension COMPOSITE
[    26.442] Initializing built-in extension DAMAGE
[    26.442] Initializing built-in extension MIT-SCREEN-SAVER
[    26.442] Initializing built-in extension DOUBLE-BUFFER
[    26.442] Initializing built-in extension RECORD
[    26.442] Initializing built-in extension DPMS
[    26.442] Initializing built-in extension X-Resource
[    26.442] Initializing built-in extension XVideo
[    26.442] Initializing built-in extension XVideo-MotionCompensation
[    26.442] Initializing built-in extension SELinux
[    26.442] Initializing built-in extension XFree86-VidModeExtension
[    26.442] Initializing built-in extension XFree86-DGA
[    26.442] Initializing built-in extension XFree86-DRI
[    26.442] Initializing built-in extension DRI2
[    26.442] (II) "glx" will be loaded by default.
[    26.442] (WW) "xmir" is not to be loaded by default. Skipping.
[    26.442] (II) LoadModule: "dri2"
[    26.442] (II) Module "dri2" already built-in
[    26.442] (II) LoadModule: "glamoregl"
[    26.443] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    26.445] (II) Module glamoregl: vendor="X.Org Foundation"
[    26.445] 	compiled for 1.14.2.901, module version = 0.5.1
[    26.445] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.445] (II) LoadModule: "glx"
[    26.446] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.446] (II) Module glx: vendor="X.Org Foundation"
[    26.446] 	compiled for 1.14.3, module version = 1.0.0
[    26.446] 	ABI class: X.Org Server Extension, version 7.0
[    26.446] (==) AIGLX enabled
[    26.446] Loading extension GLX
[    26.446] (==) Matched fglrx as autoconfigured driver 0
[    26.446] (==) Matched ati as autoconfigured driver 1
[    26.446] (==) Matched fglrx as autoconfigured driver 2
[    26.446] (==) Matched ati as autoconfigured driver 3
[    26.446] (==) Matched vesa as autoconfigured driver 4
[    26.446] (==) Matched modesetting as autoconfigured driver 5
[    26.446] (==) Matched fbdev as autoconfigured driver 6
[    26.446] (==) Assigned the driver to the xf86ConfigLayout
[    26.446] (II) LoadModule: "fglrx"
[    26.447] (WW) Warning, couldn't open module fglrx
[    26.447] (II) UnloadModule: "fglrx"
[    26.447] (II) Unloading fglrx
[    26.447] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    26.447] (II) LoadModule: "ati"
[    26.447] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    26.447] (II) Module ati: vendor="X.Org Foundation"
[    26.447] 	compiled for 1.14.3, module version = 7.2.0
[    26.447] 	Module class: X.Org Video Driver
[    26.447] 	ABI class: X.Org Video Driver, version 14.1
[    26.447] (II) LoadModule: "radeon"
[    26.447] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    26.448] (II) Module radeon: vendor="X.Org Foundation"
[    26.448] 	compiled for 1.14.3, module version = 7.2.0
[    26.448] 	Module class: X.Org Video Driver
[    26.448] 	ABI class: X.Org Video Driver, version 14.1
[    26.448] (II) LoadModule: "vesa"
[    26.448] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.448] (II) Module vesa: vendor="X.Org Foundation"
[    26.448] 	compiled for 1.14.1, module version = 2.3.2
[    26.448] 	Module class: X.Org Video Driver
[    26.448] 	ABI class: X.Org Video Driver, version 14.1
[    26.448] (II) LoadModule: "modesetting"
[    26.449] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.449] (II) Module modesetting: vendor="X.Org Foundation"
[    26.449] 	compiled for 1.14.1, module version = 0.8.0
[    26.449] 	Module class: X.Org Video Driver
[    26.449] 	ABI class: X.Org Video Driver, version 14.1
[    26.449] (II) LoadModule: "fbdev"
[    26.449] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.449] (II) Module fbdev: vendor="X.Org Foundation"
[    26.449] 	compiled for 1.14.1, module version = 0.4.3
[    26.449] 	Module class: X.Org Video Driver
[    26.449] 	ABI class: X.Org Video Driver, version 14.1
[    26.449] (==) Matched fglrx as autoconfigured driver 0
[    26.449] (==) Matched ati as autoconfigured driver 1
[    26.449] (==) Matched fglrx as autoconfigured driver 2
[    26.449] (==) Matched ati as autoconfigured driver 3
[    26.449] (==) Matched vesa as autoconfigured driver 4
[    26.449] (==) Matched modesetting as autoconfigured driver 5
[    26.449] (==) Matched fbdev as autoconfigured driver 6
[    26.449] (==) Assigned the driver to the xf86ConfigLayout
[    26.449] (II) LoadModule: "fglrx"
[    26.450] (WW) Warning, couldn't open module fglrx
[    26.450] (II) UnloadModule: "fglrx"
[    26.450] (II) Unloading fglrx
[    26.450] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    26.450] (II) LoadModule: "ati"
[    26.450] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    26.450] (II) Module ati: vendor="X.Org Foundation"
[    26.450] 	compiled for 1.14.3, module version = 7.2.0
[    26.450] 	Module class: X.Org Video Driver
[    26.450] 	ABI class: X.Org Video Driver, version 14.1
[    26.450] (II) LoadModule: "vesa"
[    26.450] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.450] (II) Module vesa: vendor="X.Org Foundation"
[    26.450] 	compiled for 1.14.1, module version = 2.3.2
[    26.450] 	Module class: X.Org Video Driver
[    26.450] 	ABI class: X.Org Video Driver, version 14.1
[    26.450] (II) UnloadModule: "vesa"
[    26.450] (II) Unloading vesa
[    26.450] (II) Failed to load module "vesa" (already loaded, 0)
[    26.450] (II) LoadModule: "modesetting"
[    26.451] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.451] (II) Module modesetting: vendor="X.Org Foundation"
[    26.451] 	compiled for 1.14.1, module version = 0.8.0
[    26.451] 	Module class: X.Org Video Driver
[    26.451] 	ABI class: X.Org Video Driver, version 14.1
[    26.451] (II) UnloadModule: "modesetting"
[    26.451] (II) Unloading modesetting
[    26.451] (II) Failed to load module "modesetting" (already loaded, 0)
[    26.451] (II) LoadModule: "fbdev"
[    26.451] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.451] (II) Module fbdev: vendor="X.Org Foundation"
[    26.451] 	compiled for 1.14.1, module version = 0.4.3
[    26.451] 	Module class: X.Org Video Driver
[    26.451] 	ABI class: X.Org Video Driver, version 14.1
[    26.451] (II) UnloadModule: "fbdev"
[    26.451] (II) Unloading fbdev
[    26.451] (II) Failed to load module "fbdev" (already loaded, 0)
[    26.451] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
	HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI
[    26.454] (II) VESA: driver for VESA chipsets: vesa
[    26.454] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.454] (II) FBDEV: driver for framebuffer: fbdev
[    26.454] (++) using VT number 7


[    26.460] (II) [KMS] drm report modesetting isn't supported.
[    26.460] (II) [KMS] drm report modesetting isn't supported.
[    26.460] (II) [KMS] drm report modesetting isn't supported.
[    26.460] (II) [KMS] drm report modesetting isn't supported.
[    26.460] (II) [KMS] drm report modesetting isn't supported.
[    26.460] (WW) Falling back to old probe method for modesetting
[    26.460] (WW) Falling back to old probe method for fbdev
[    26.460] (II) Loading sub module "fbdevhw"
[    26.460] (II) LoadModule: "fbdevhw"
[    26.461] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.461] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.461] 	compiled for 1.14.3, module version = 0.0.2
[    26.461] 	ABI class: X.Org Video Driver, version 14.1
[    26.461] (EE) Screen 0 deleted because of no matching config section.
[    26.461] (II) UnloadModule: "radeon"
[    26.461] (EE) Screen 0 deleted because of no matching config section.
[    26.461] (II) UnloadModule: "radeon"
[    26.461] (EE) Screen 0 deleted because of no matching config section.
[    26.461] (II) UnloadModule: "radeon"
[    26.461] (EE) Screen 0 deleted because of no matching config section.
[    26.461] (II) UnloadModule: "radeon"
[    26.461] (II) Loading sub module "vbe"
[    26.461] (II) LoadModule: "vbe"
[    26.461] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    26.461] (II) Module vbe: vendor="X.Org Foundation"
[    26.461] 	compiled for 1.14.3, module version = 1.1.0
[    26.461] 	ABI class: X.Org Video Driver, version 14.1
[    26.461] (II) Loading sub module "int10"
[    26.461] (II) LoadModule: "int10"
[    26.462] (II) Loading /usr/lib/xorg/modules/libint10.so
[    26.462] (II) Module int10: vendor="X.Org Foundation"
[    26.462] 	compiled for 1.14.3, module version = 1.0.0
[    26.462] 	ABI class: X.Org Video Driver, version 14.1
[    26.462] (II) VESA(0): initializing int10
[    26.463] (EE) VESA(0): Cannot read V_BIOS (3) Input/output error
[    26.463] (II) UnloadModule: "vesa"
[    26.463] (II) UnloadSubModule: "int10"
[    26.463] (II) Unloading int10
[    26.463] (II) UnloadSubModule: "vbe"
[    26.463] (II) Unloading vbe
[    26.463] (II) UnloadModule: "radeon"
[    26.463] (EE) Screen(s) found, but none have a usable configuration.
[    26.463] (EE) 
Fatal server error:
[    26.463] (EE) no screens found(EE) 
[    26.463] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    26.463] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    26.463] (EE) 
[    26.468] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by Bucky Ball on 2014-01-24
All fine. Just put the code between [code] tags. I have done the last post for you. To attach a file, 'Adv. Reply' or edit post, click 'Go Advanced' and use the paper clip icon. ;)

---

### Post by slooksterpsv on 2014-01-24
Same issue here, the only thing I can think of is that it can't find any kernel modules for the HD 8400 so it's failing. Installing FGLRX or AMD's driver should work in theory, but until it can be tested, it's a no go so far. I have yet to find a distro that supports the HD 8400 - may try the alpha of 14.04 see how it runs.

---

### Post by naveen-rajanikantha on 2014-01-27
Searching around, looks like 
AMD HD8400 graphics card needs a AMD proprietary "Catalyst" Driver.
This catalyst driver supports [COLOR=#000000][FONT=inherit]Ubuntu 12.04.2 and 13.04 ( [/FONT][/COLOR]http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx)

I guess, I will try Ubuntu 13.04.

Or else wait till AMD ports this driver to later kernels.

Thanks
-naveen

---

### Post by Bucky Ball on 2014-01-27
13.04 is a bad choice as it is out of support as of yesterday. Try 12.04, directly upgradeable to the next LTS 14.04 when it is released in April.

---

### Post by slooksterpsv on 2014-01-28
Here's a fix for you, it's worked for me till I can get the right drivers installed. Get to a terminal prompt and type in:

```

sudo Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

```

Restart after that

---

### Post by naveen-rajanikantha on 2014-02-15
Great, that fix works.
I now have Ubuntu installed and running on my laptop.
Thanks for your help.

---

