---
title: "[64 bit] Graphic problems"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by Nucleolus on 2013-04-28
Hello. Yesterday I upgraded my Ubuntu 12.10 to Ubuntu 13.04 in order to improve the performance, but after the installation the graphics did not go well. I have just put an USB with Ubuntu 13.04 in live mode to see if is a problem with upgrading but I see the same in live mode. Look the image[ATTACH=CONFIG]241897[/ATTACH]

How could I solve this weird problem?

---

### Post by Nucleolus on 2013-04-28
Anyone know what happen?

---

### Post by sammiev on 2013-04-28
Have you ran a update yet? If so select Additional Drivers and see if there is any Propriteary Drivers.

---

### Post by gamblor01 on 2013-04-28
What type of video card do you have?  If you don't know you can always get it from lspci output:

```

lspci | grep VGA

```


More than likely it's just an incompatible driver.  Hopefully it wasn't something more serious like the actual video card failing, but if it happened on the upgrade then it's likely software related.  Either that or was a giant coincidence.

Let's find out what type of graphics card you have and we'll go from there.

---

### Post by Nucleolus on 2013-04-29
Sorry for answering so late. I have ATI Radeon x1200 and with Ubuntu 12.10 the graphics gone well, but very very laggy

---

### Post by gamblor01 on 2013-04-30
Wow that is a really old card.  It looks like ATI has placed it into legacy support -- so your card does not support the latest driver that they offer.  I don't know if you can go into software sources and install it (fglrx driver) from the "additional drivers" tab or not.  If not, it looks like you need to get it from here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)


They have instructions on there but basically you will need to make it executable, run it as root (don't reboot if it prompts you at the end of install), and then run aticonfig as root (which should setup xorg.conf).  Something like this:

```

$ chmod +x ati-driver-installer-9-3-x86.x86_64.run
$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
$ sudo aticonfig --initial

```

---

### Post by Cheesemill on 2013-04-30
> **gamblor01 said:**
> Wow that is a really old card.  It looks like ATI has placed it into  legacy support -- so your card does not support the latest driver that  they offer.  I don't know if you can go into software sources and  install it (fglrx driver) from the "additional drivers" tab or not. If not, it looks like you need to get it from here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)


They have instructions on there but basically you will need to make it executable, run it as root (don't reboot if it prompts you at the end of install), and then run aticonfig as root (which should setup xorg.conf).  Something like this:

```

$ chmod +x ati-driver-installer-9-3-x86.x86_64.run
$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
$ sudo aticonfig --initial

```

Don't do this, it won't work. ATI don't provide graphics drivers for your card that will work with the latest versions of Ubuntu. The only graphics driver that is available for your card is the one that comes built into Ubuntu, you are already using it.

Try updating your installed system, it may be an issue that has already been fixed. If this doesn't work then another possibility is that you have a corrupt installation media, did you check the MD5SUM of your downloaded iso file?

---

### Post by Nucleolus on 2013-05-02
> **gamblor01 said:**
> What type of video card do you have?  If you don't know you can always get it from lspci output:

```

lspci | grep VGA

```


More than likely it's just an incompatible driver.  Hopefully it wasn't something more serious like the actual video card failing, but if it happened on the upgrade then it's likely software related.  Either that or was a giant coincidence.

Let's find out what type of graphics card you have and we'll go from there.

```
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon Xpress 1200/1250/1270]


```

> **Cheesemill said:**
> Don't do this, it won't work. ATI don't provide graphics drivers for your card that will work with the latest versions of Ubuntu. The only graphics driver that is available for your card is the one that comes built into Ubuntu, you are already using it.

Try updating your installed system, it may be an issue that has already been fixed. If this doesn't work then another possibility is that you have a corrupt installation media, did you check the MD5SUM of your downloaded iso file?

I have all the updates but I still seeing this "graphics" Uhm... this video card is in my laptop, buyed in 2008 it is not too old! :( I has 3GB of ram ^^

---

### Post by Cheesemill on 2013-05-02
> **Nucleolus said:**
> Uhm... this video card is in my laptop, buyed in 2008 it is not too old! :( I has 3GB of ram ^^

Don't tell me, tell AMD. They're the ones who decided to stop supporting your graphics card :)

Have you checked the integrity of your installation media like I suggested?

---

### Post by MAFoElffen on 2013-05-03
> **Cheesemill said:**
> Have you checked the integrity of your installation media like I suggested?
The OP said in post #1 that he did an online release upgrade from 12.10 to 13.04.

To the OP (Original Poster)-
Details... So are you running the open source frglx as a driver or no installed extra driver at all? (using xorg's radeon or ati drivers...) Posting your /var/log/Xorg.0.log would help us with that. 

If you are running a proprietary driver then post your /etc/X11/xorg.conf file. There is a setting that would cause that "angled" look that we can look for in there. We need to make sure it is "not" that first. If that file does not exist, then it is using the xorg drivers and picking them out on it's own.

If that is not it, then look at the (current) last two pages of my Graphics Resolution Sticky (link in my sig line) for instructions on resetting Unity profiles. There has been some problems for some users where some Unity profile options didn't translate well from version to version.

---

### Post by Nucleolus on 2013-05-07
> **Cheesemill said:**
> Don't tell me, tell AMD. They're the ones who decided to stop supporting your graphics card :)

Have you checked the integrity of your installation media like I suggested?

AMD :mad:
> **MAFoElffen said:**
> The OP said in post #1 that he did an online release upgrade from 12.10 to 13.04.

To the OP (Original Poster)-
Details... So are you running the open source frglx as a driver or no installed extra driver at all? (using xorg's radeon or ati drivers...) Posting your /var/log/Xorg.0.log would help us with that. 

If you are running a proprietary driver then post your /etc/X11/xorg.conf file. There is a setting that would cause that "angled" look that we can look for in there. We need to make sure it is "not" that first. If that file does not exist, then it is using the xorg drivers and picking them out on it's own.

If that is not it, then look at the (current) last two pages of my Graphics Resolution Sticky (link in my sig line) for instructions on resetting Unity profiles. There has been some problems for some users where some Unity profile options didn't translate well from version to version.

Now I'm running a clean installation 13.04 in my Laptop and I still see this.

I don't have any extra driver, only the drivers from the installation. Here is my /var/log/Xorg.0.org

```
[  2217.141] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[  2217.141] X Protocol Version 11, Revision 0
[  2217.141] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  2217.141] Current Operating System: Linux javier-pb-ubuntu 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64
[  2217.141] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=2f97632a-9282-4f3a-9532-a0887941f0f2 ro quiet splash vt.handoff=7
[  2217.141] Build Date: 17 April 2013  10:43:13PM
[  2217.141] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[  2217.142] Current version of pixman: 0.28.2
[  2217.142]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  2217.142] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2217.142] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May  7 15:34:25 2013
[  2217.167] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2217.182] (==) No Layout section.  Using the first Screen section.
[  2217.182] (==) No screen section available. Using defaults.
[  2217.182] (**) |-->Screen "Default Screen Section" (0)
[  2217.182] (**) |   |-->Monitor "<default monitor>"
[  2217.183] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  2217.183] (==) Automatically adding devices
[  2217.183] (==) Automatically enabling devices
[  2217.183] (==) Automatically adding GPU devices
[  2217.204] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2217.204]     Entry deleted from font path.
[  2217.204] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2217.204]     Entry deleted from font path.
[  2217.204] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2217.204]     Entry deleted from font path.
[  2217.204] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2217.204]     Entry deleted from font path.
[  2217.204] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2217.204]     Entry deleted from font path.
[  2217.204] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  2217.204]     Entry deleted from font path.
[  2217.204] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  2217.204] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2217.204] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2217.204] (II) Loader magic: 0x7fd5ad00cd20
[  2217.204] (II) Module ABI versions:
[  2217.204]     X.Org ANSI C Emulation: 0.4
[  2217.204]     X.Org Video Driver: 13.1
[  2217.204]     X.Org XInput driver : 18.0
[  2217.204]     X.Org Server Extension : 7.0
[  2217.205] (II) config/udev: Adding drm device (/dev/dri/card0)
[  2217.209] (--) PCI:*(0:1:5:0) 1002:791f:1631:c108 rev 0, Mem @ 0xc0000000/268435456, 0xfd8f0000/65536, 0xfd700000/1048576, I/O @ 0x00008800/256
[  2217.210] (II) Open ACPI successful (/var/run/acpid.socket)
[  2217.210] Initializing built-in extension Generic Event Extension
[  2217.210] Initializing built-in extension SHAPE
[  2217.210] Initializing built-in extension MIT-SHM
[  2217.210] Initializing built-in extension XInputExtension
[  2217.210] Initializing built-in extension XTEST
[  2217.210] Initializing built-in extension BIG-REQUESTS
[  2217.210] Initializing built-in extension SYNC
[  2217.210] Initializing built-in extension XKEYBOARD
[  2217.210] Initializing built-in extension XC-MISC
[  2217.210] Initializing built-in extension SECURITY
[  2217.210] Initializing built-in extension XINERAMA
[  2217.210] Initializing built-in extension XFIXES
[  2217.210] Initializing built-in extension RENDER
[  2217.210] Initializing built-in extension RANDR
[  2217.210] Initializing built-in extension COMPOSITE
[  2217.210] Initializing built-in extension DAMAGE
[  2217.210] Initializing built-in extension MIT-SCREEN-SAVER
[  2217.210] Initializing built-in extension DOUBLE-BUFFER
[  2217.210] Initializing built-in extension RECORD
[  2217.210] Initializing built-in extension DPMS
[  2217.210] Initializing built-in extension X-Resource
[  2217.210] Initializing built-in extension XVideo
[  2217.211] Initializing built-in extension XVideo-MotionCompensation
[  2217.211] Initializing built-in extension SELinux
[  2217.211] Initializing built-in extension XFree86-VidModeExtension
[  2217.211] Initializing built-in extension XFree86-DGA
[  2217.211] Initializing built-in extension XFree86-DRI
[  2217.211] Initializing built-in extension DRI2
[  2217.211] (II) LoadModule: "glx"
[  2217.392] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2217.444] (II) Module glx: vendor="X.Org Foundation"
[  2217.444]     compiled for 1.13.3, module version = 1.0.0
[  2217.444]     ABI class: X.Org Server Extension, version 7.0
[  2217.444] (==) AIGLX enabled
[  2217.444] Loading extension GLX
[  2217.445] (==) Matched fglrx as autoconfigured driver 0
[  2217.445] (==) Matched ati as autoconfigured driver 1
[  2217.445] (==) Matched fglrx as autoconfigured driver 2
[  2217.445] (==) Matched ati as autoconfigured driver 3
[  2217.445] (==) Matched vesa as autoconfigured driver 4
[  2217.445] (==) Matched modesetting as autoconfigured driver 5
[  2217.445] (==) Matched fbdev as autoconfigured driver 6
[  2217.445] (==) Assigned the driver to the xf86ConfigLayout
[  2217.445] (II) LoadModule: "fglrx"
[  2217.462] (WW) Warning, couldn't open module fglrx
[  2217.462] (II) UnloadModule: "fglrx"
[  2217.462] (II) Unloading fglrx
[  2217.462] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  2217.462] (II) LoadModule: "ati"
[  2217.463] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2217.476] (II) Module ati: vendor="X.Org Foundation"
[  2217.476]     compiled for 1.13.3, module version = 7.1.0
[  2217.476]     Module class: X.Org Video Driver
[  2217.476]     ABI class: X.Org Video Driver, version 13.1
[  2217.476] (II) LoadModule: "radeon"
[  2217.477] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  2217.492] (II) Module radeon: vendor="X.Org Foundation"
[  2217.492]     compiled for 1.13.3, module version = 7.1.0
[  2217.492]     Module class: X.Org Video Driver
[  2217.492]     ABI class: X.Org Video Driver, version 13.1
[  2217.492] (II) LoadModule: "vesa"
[  2217.493] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2217.503] (II) Module vesa: vendor="X.Org Foundation"
[  2217.503]     compiled for 1.12.99.902, module version = 2.3.2
[  2217.503]     Module class: X.Org Video Driver
[  2217.503]     ABI class: X.Org Video Driver, version 13.0
[  2217.503] (II) LoadModule: "modesetting"
[  2217.504] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  2217.509] (II) Module modesetting: vendor="X.Org Foundation"
[  2217.510]     compiled for 1.13.3, module version = 0.7.0
[  2217.510]     Module class: X.Org Video Driver
[  2217.510]     ABI class: X.Org Video Driver, version 13.1
[  2217.510] (II) LoadModule: "fbdev"
[  2217.511] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2217.523] (II) Module fbdev: vendor="X.Org Foundation"
[  2217.523]     compiled for 1.12.99.902, module version = 0.4.3
[  2217.523]     Module class: X.Org Video Driver
[  2217.523]     ABI class: X.Org Video Driver, version 13.0
[  2217.523] (==) Matched fglrx as autoconfigured driver 0
[  2217.523] (==) Matched ati as autoconfigured driver 1
[  2217.524] (==) Matched fglrx as autoconfigured driver 2
[  2217.524] (==) Matched ati as autoconfigured driver 3
[  2217.524] (==) Matched vesa as autoconfigured driver 4
[  2217.524] (==) Matched modesetting as autoconfigured driver 5
[  2217.524] (==) Matched fbdev as autoconfigured driver 6
[  2217.524] (==) Assigned the driver to the xf86ConfigLayout
[  2217.524] (II) LoadModule: "fglrx"
[  2217.525] (WW) Warning, couldn't open module fglrx
[  2217.525] (II) UnloadModule: "fglrx"
[  2217.525] (II) Unloading fglrx
[  2217.525] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  2217.525] (II) LoadModule: "ati"
[  2217.526] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2217.526] (II) Module ati: vendor="X.Org Foundation"
[  2217.526]     compiled for 1.13.3, module version = 7.1.0
[  2217.526]     Module class: X.Org Video Driver
[  2217.526]     ABI class: X.Org Video Driver, version 13.1
[  2217.526] (II) LoadModule: "vesa"
[  2217.527] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2217.527] (II) Module vesa: vendor="X.Org Foundation"
[  2217.527]     compiled for 1.12.99.902, module version = 2.3.2
[  2217.527]     Module class: X.Org Video Driver
[  2217.527]     ABI class: X.Org Video Driver, version 13.0
[  2217.527] (II) UnloadModule: "vesa"
[  2217.527] (II) Unloading vesa
[  2217.527] (II) Failed to load module "vesa" (already loaded, 0)
[  2217.527] (II) LoadModule: "modesetting"
[  2217.528] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  2217.528] (II) Module modesetting: vendor="X.Org Foundation"
[  2217.528]     compiled for 1.13.3, module version = 0.7.0
[  2217.528]     Module class: X.Org Video Driver
[  2217.528]     ABI class: X.Org Video Driver, version 13.1
[  2217.528] (II) UnloadModule: "modesetting"
[  2217.528] (II) Unloading modesetting
[  2217.529] (II) Failed to load module "modesetting" (already loaded, 0)
[  2217.529] (II) LoadModule: "fbdev"
[  2217.529] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2217.529] (II) Module fbdev: vendor="X.Org Foundation"
[  2217.529]     compiled for 1.12.99.902, module version = 0.4.3
[  2217.529]     Module class: X.Org Video Driver
[  2217.530]     ABI class: X.Org Video Driver, version 13.0
[  2217.530] (II) UnloadModule: "fbdev"
[  2217.530] (II) Unloading fbdev
[  2217.530] (II) Failed to load module "fbdev" (already loaded, 0)
[  2217.530] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[  2217.548] (II) VESA: driver for VESA chipsets: vesa
[  2217.548] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  2217.548] (II) FBDEV: driver for framebuffer: fbdev
[  2217.549] (++) using VT number 7

[  2217.549] (II) [KMS] Kernel modesetting enabled.
[  2217.549] (WW) Falling back to old probe method for vesa
[  2217.549] (WW) Falling back to old probe method for modesetting
[  2217.549] (WW) Falling back to old probe method for fbdev
[  2217.550] (II) Loading sub module "fbdevhw"
[  2217.550] (II) LoadModule: "fbdevhw"
[  2217.550] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  2217.571] (II) Module fbdevhw: vendor="X.Org Foundation"
[  2217.572]     compiled for 1.13.3, module version = 0.0.2
[  2217.572]     ABI class: X.Org Video Driver, version 13.1
[  2217.572] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  2217.572] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  2217.572] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  2217.572] (==) RADEON(0): Default visual is TrueColor
[  2217.572] (==) RADEON(0): RGB weight 888
[  2217.572] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  2217.572] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[  2217.573] (II) Loading sub module "dri2"
[  2217.573] (II) LoadModule: "dri2"
[  2217.573] (II) Module "dri2" already built-in
[  2217.573] (II) Loading sub module "exa"
[  2217.573] (II) LoadModule: "exa"
[  2217.573] (II) Loading /usr/lib/xorg/modules/libexa.so
[  2217.576] (II) Module exa: vendor="X.Org Foundation"
[  2217.576]     compiled for 1.13.3, module version = 2.6.0
[  2217.576]     ABI class: X.Org Video Driver, version 13.1
[  2217.576] (II) RADEON(0): KMS Color Tiling: enabled
[  2217.576] (II) RADEON(0): KMS Color Tiling 2D: disabled
[  2217.576] (II) RADEON(0): KMS Pageflipping: enabled
[  2217.576] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  2217.752] (II) RADEON(0): Output VGA-0 has no monitor section
[  2217.752] (II) RADEON(0): Output LVDS has no monitor section
[  2217.928] (II) RADEON(0): EDID for output VGA-0
[  2217.928] (II) RADEON(0): EDID for output LVDS
[  2217.928] (II) RADEON(0): Manufacturer: LPL  Model: e300  Serial#: 0
[  2217.928] (II) RADEON(0): Year: 2006  Week: 0
[  2217.928] (II) RADEON(0): EDID Version: 1.3
[  2217.928] (II) RADEON(0): Digital Display Input
[  2217.928] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  2217.928] (II) RADEON(0): Gamma: 2.20
[  2217.928] (II) RADEON(0): No DPMS capabilities specified
[  2217.928] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2217.928] (II) RADEON(0): First detailed timing is preferred mode
[  2217.928] (II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[  2217.928] (II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[  2217.928] (II) RADEON(0): Manufacturer's mask: 0
[  2217.928] (II) RADEON(0): Supported detailed timing:
[  2217.928] (II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  2217.928] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[  2217.928] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[  2217.929] (II) RADEON(0):  LGPhilipsLCD
[  2217.929] (II) RADEON(0):  LP154WX4-TLC3
[  2217.929] (II) RADEON(0): EDID (in hex):
[  2217.929] (II) RADEON(0):     00ffffffffffff00320c00e300000000
[  2217.929] (II) RADEON(0):     00100103802115780ab3409959538d27
[  2217.929] (II) RADEON(0):     25505400000001010101010101010101
[  2217.929] (II) RADEON(0):     010101010101bc1b00a0502017303020
[  2217.929] (II) RADEON(0):     36004bcf100000190000000000000000
[  2217.929] (II) RADEON(0):     00000000000000000000000000fe004c
[  2217.929] (II) RADEON(0):     475068696c6970734c43440a000000fe
[  2217.929] (II) RADEON(0):     004c503135345758342d544c4333003c
[  2217.929] (II) RADEON(0): Printing probed modes for output LVDS
[  2217.929] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2217.929] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[  2217.929] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[  2217.929] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[  2217.929] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[  2217.929] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[  2217.929] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[  2217.929] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[  2217.929] (II) RADEON(0): Output VGA-0 disconnected
[  2217.929] (II) RADEON(0): Output LVDS connected
[  2217.929] (II) RADEON(0): Using exact sizes for initial modes
[  2217.929] (II) RADEON(0): Output LVDS using initial mode 1280x800
[  2217.930] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  2217.930] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fbd8000
[  2217.930] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  2217.930] (==) RADEON(0): DPI set to (96, 96)
[  2217.930] (II) Loading sub module "fb"
[  2217.930] (II) LoadModule: "fb"
[  2217.931] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2217.932] (II) Module fb: vendor="X.Org Foundation"
[  2217.932]     compiled for 1.13.3, module version = 1.0.0
[  2217.932]     ABI class: X.Org ANSI C Emulation, version 0.4
[  2217.932] (II) Loading sub module "ramdac"
[  2217.932] (II) LoadModule: "ramdac"
[  2217.932] (II) Module "ramdac" already built-in
[  2217.932] (II) UnloadModule: "vesa"
[  2217.932] (II) Unloading vesa
[  2217.932] (II) UnloadModule: "modesetting"
[  2217.932] (II) Unloading modesetting
[  2217.933] (II) UnloadModule: "fbdev"
[  2217.933] (II) Unloading fbdev
[  2217.933] (II) UnloadSubModule: "fbdevhw"
[  2217.933] (II) Unloading fbdevhw
[  2217.933] (--) Depth 24 pixmap format is 32 bpp
[  2217.933] (II) RADEON(0): [DRI2] Setup complete
[  2217.933] (II) RADEON(0): [DRI2]   DRI driver: r300
[  2217.933] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[  2217.934] (II) RADEON(0): Front buffer size: 4000K
[  2217.934] (II) RADEON(0): VRAM usage limit set to 228470K
[  2217.934] (==) RADEON(0): Backing store disabled
[  2217.934] (II) RADEON(0): Direct rendering enabled
[  2217.934] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[  2217.934] (II) EXA(0): Driver allocated offscreen pixmaps
[  2217.934] (II) EXA(0): Driver registered support for the following operations:
[  2217.934] (II)         Solid
[  2217.934] (II)         Copy
[  2217.934] (II)         Composite (RENDER acceleration)
[  2217.934] (II)         UploadToScreen
[  2217.934] (II)         DownloadFromScreen
[  2217.934] (II) RADEON(0): Acceleration enabled
[  2217.934] (==) RADEON(0): DPMS enabled
[  2217.934] (==) RADEON(0): Silken mouse enabled
[  2217.935] (II) RADEON(0): Set up textured video
[  2217.935] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  2217.935] (II) RADEON(0): [XvMC] Extension initialized.
[  2217.935] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  2217.936] (--) RandR disabled
[  2217.955] (II) SELinux: Disabled on system
[  2218.151] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  2218.151] (II) AIGLX: enabled GLX_INTEL_swap_event
[  2218.151] (II) AIGLX: enabled GLX_ARB_create_context
[  2218.151] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  2218.151] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  2218.151] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  2218.152] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  2218.153] (II) AIGLX: Loaded and initialized r300
[  2218.153] (II) GLX: Initialized DRI2 GL provider for screen 0
[  2218.155] (II) RADEON(0): Setting screen physical size to 338 x 211
[  2218.239] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2218.262] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  2218.262] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2218.262] (II) LoadModule: "evdev"
[  2218.263] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2218.294] (II) Module evdev: vendor="X.Org Foundation"
[  2218.294]     compiled for 1.13.3, module version = 2.7.3
[  2218.294]     Module class: X.Org XInput Driver
[  2218.294]     ABI class: X.Org XInput driver, version 18.0
[  2218.294] (II) Using input driver 'evdev' for 'Power Button'
[  2218.294] (**) Power Button: always reports core events
[  2218.294] (**) evdev: Power Button: Device: "/dev/input/event3"
[  2218.295] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2218.295] (--) evdev: Power Button: Found keys
[  2218.295] (II) evdev: Power Button: Configuring as keyboard
[  2218.295] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  2218.295] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  2218.295] (**) Option "xkb_rules" "evdev"
[  2218.295] (**) Option "xkb_model" "pc105"
[  2218.295] (**) Option "xkb_layout" "es"
[  2218.303] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[  2218.313] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[  2218.313] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2218.313] (II) Using input driver 'evdev' for 'Video Bus'
[  2218.313] (**) Video Bus: always reports core events
[  2218.313] (**) evdev: Video Bus: Device: "/dev/input/event6"
[  2218.313] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  2218.313] (--) evdev: Video Bus: Found keys
[  2218.313] (II) evdev: Video Bus: Configuring as keyboard
[  2218.313] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6/event6"
[  2218.314] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  2218.314] (**) Option "xkb_rules" "evdev"
[  2218.314] (**) Option "xkb_model" "pc105"
[  2218.314] (**) Option "xkb_layout" "es"
[  2218.315] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  2218.315] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2218.316] (II) Using input driver 'evdev' for 'Power Button'
[  2218.316] (**) Power Button: always reports core events
[  2218.316] (**) evdev: Power Button: Device: "/dev/input/event0"
[  2218.316] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2218.316] (--) evdev: Power Button: Found keys
[  2218.316] (II) evdev: Power Button: Configuring as keyboard
[  2218.316] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  2218.316] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[  2218.316] (**) Option "xkb_rules" "evdev"
[  2218.316] (**) Option "xkb_model" "pc105"
[  2218.316] (**) Option "xkb_layout" "es"
[  2218.318] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[  2218.318] (II) No input driver specified, ignoring this device.
[  2218.318] (II) This device may have been added with another device file.
[  2218.319] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  2218.319] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  2218.319] (II) Using input driver 'evdev' for 'Sleep Button'
[  2218.319] (**) Sleep Button: always reports core events
[  2218.319] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  2218.319] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  2218.319] (--) evdev: Sleep Button: Found keys
[  2218.319] (II) evdev: Sleep Button: Configuring as keyboard
[  2218.319] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  2218.319] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[  2218.319] (**) Option "xkb_rules" "evdev"
[  2218.319] (**) Option "xkb_model" "pc105"
[  2218.319] (**) Option "xkb_layout" "es"
[  2218.321] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:05.0/drm/card0
[  2218.321] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  2218.322] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event10)
[  2218.322] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  2218.322] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  2218.322] (**) Logitech USB Receiver: always reports core events
[  2218.322] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event10"
[  2218.322] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[  2218.322] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[  2218.323] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[  2218.323] (--) evdev: Logitech USB Receiver: Found relative axes
[  2218.323] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[  2218.323] (II) evdev: Logitech USB Receiver: Configuring as mouse
[  2218.323] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[  2218.323] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  2218.323] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2218.323] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input10/event10"
[  2218.323] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 10)
[  2218.323] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[  2218.324] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  2218.324] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  2218.324] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  2218.324] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  2218.326] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[  2218.326] (II) No input driver specified, ignoring this device.
[  2218.326] (II) This device may have been added with another device file.
[  2218.327] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event11)
[  2218.327] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2218.327] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  2218.327] (**) Logitech USB Receiver: always reports core events
[  2218.327] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event11"
[  2218.327] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[  2218.327] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[  2218.327] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[  2218.327] (--) evdev: Logitech USB Receiver: Found relative axes
[  2218.327] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[  2218.327] (--) evdev: Logitech USB Receiver: Found absolute axes
[  2218.328] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[  2218.328] (--) evdev: Logitech USB Receiver: Found keys
[  2218.328] (II) evdev: Logitech USB Receiver: Configuring as mouse
[  2218.328] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[  2218.328] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[  2218.328] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  2218.328] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2218.328] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.1/input/input11/event11"
[  2218.328] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 11)
[  2218.328] (**) Option "xkb_rules" "evdev"
[  2218.328] (**) Option "xkb_model" "pc105"
[  2218.328] (**) Option "xkb_layout" "es"
[  2218.329] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[  2218.329] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[  2218.330] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  2218.330] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  2218.330] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  2218.330] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  2218.331] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event7)
[  2218.331] (II) No input driver specified, ignoring this device.
[  2218.331] (II) This device may have been added with another device file.
[  2218.332] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event8)
[  2218.332] (II) No input driver specified, ignoring this device.
[  2218.332] (II) This device may have been added with another device file.
[  2218.333] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event5)
[  2218.333] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[  2218.333] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[  2218.333] (**) Asus Laptop extra buttons: always reports core events
[  2218.333] (**) evdev: Asus Laptop extra buttons: Device: "/dev/input/event5"
[  2218.333] (--) evdev: Asus Laptop extra buttons: Vendor 0 Product 0
[  2218.333] (--) evdev: Asus Laptop extra buttons: Found keys
[  2218.333] (II) evdev: Asus Laptop extra buttons: Configuring as keyboard
[  2218.333] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input5/event5"
[  2218.333] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD, id 12)
[  2218.333] (**) Option "xkb_rules" "evdev"
[  2218.333] (**) Option "xkb_model" "pc105"
[  2218.333] (**) Option "xkb_layout" "es"
[  2218.335] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  2218.335] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  2218.335] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  2218.335] (**) AT Translated Set 2 keyboard: always reports core events
[  2218.335] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  2218.336] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  2218.336] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  2218.336] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  2218.336] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  2218.336] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[  2218.336] (**) Option "xkb_rules" "evdev"
[  2218.336] (**) Option "xkb_model" "pc105"
[  2218.336] (**) Option "xkb_layout" "es"
[  2218.338] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[  2218.338] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  2218.338] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  2218.338] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  2218.338] (II) LoadModule: "synaptics"
[  2218.339] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  2218.350] (II) Module synaptics: vendor="X.Org Foundation"
[  2218.350]     compiled for 1.13.1.901, module version = 1.6.2
[  2218.350]     Module class: X.Org XInput Driver
[  2218.350]     ABI class: X.Org XInput driver, version 18.0
[  2218.350] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  2218.350] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  2218.350] (**) Option "Device" "/dev/input/event9"
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  2218.360] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  2218.360] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  2218.360] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input9/event9"
[  2218.361] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[  2218.361] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  2218.361] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  2218.361] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  2218.362] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  2218.362] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  2218.362] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  2218.362] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  2218.362] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  2218.363] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  2218.363] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  2220.944] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2220.944] (II) RADEON(0): Printing DDC gathered Modelines:
[  2220.944] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2222.412] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2222.412] (II) RADEON(0): Printing DDC gathered Modelines:
[  2222.413] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2240.652] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2240.652] (II) RADEON(0): Printing DDC gathered Modelines:
[  2240.652] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2241.220] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2241.220] (II) RADEON(0): Printing DDC gathered Modelines:
[  2241.220] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2242.440] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2242.440] (II) RADEON(0): Printing DDC gathered Modelines:
[  2242.440] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2245.872] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2245.872] (II) RADEON(0): Printing DDC gathered Modelines:
[  2245.872] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[  2252.704] (II) XKB: reuse xkmfile /var/lib/xkb/server-1EEA8A8B5282F1A1C5B4CDBD09D3AB33A69761C2.xkm
[  2263.024] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  2263.024] (II) RADEON(0): Printing DDC gathered Modelines:
[  2263.024] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
```

[ATTACH=CONFIG]242293[/ATTACH]

---

### Post by Nucleolus on 2013-05-08
Up

---

### Post by Nucleolus on 2013-05-09
Up

---

