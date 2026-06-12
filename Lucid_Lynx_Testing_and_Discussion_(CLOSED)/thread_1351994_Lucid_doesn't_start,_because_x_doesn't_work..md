---
title: "Lucid doesn't start, because x doesn't work."
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chares on 2009-12-11
In testing Ubuntu 10.4, but this don't run, because x doesn't start. Logs:
[http://launchpadlibrarian.net/36665455/Xorg.0.log](http://launchpadlibrarian.net/36665455/Xorg.0.log)
[http://launchpadlibrarian.net/36665456/Xorg.1.log](http://launchpadlibrarian.net/36665456/Xorg.1.log)

Here bug on Launchpad: [https://bugs.launchpad.net/xorg-server/+bug/495157](https://bugs.launchpad.net/xorg-server/+bug/495157)

PS. I use open drivers and ATI Radeon 9600.

---

### Post by andrek on 2009-12-11
I'm using fglrx driver for my ati 4570 and had similar problems, I downgraded xorg and xserver packages to the karmic ones and it works again.

---

### Post by Chares on 2009-12-11
But I use Xserver-xorg-video-radeon and Xserver-xorg-video-ati. These packages aren't in lucid repository and Xorg can't run.

---

### Post by kansasnoob on 2009-12-11
In both Karmic and Lucid I've had to be bold and use the Xorg crack pushers ppa, but be mindful that I'm just using a plain-Jane 2D VIA graphics card that relies on the openchrome driver.

Also take into consideration the first paragraph from their Launchpad intro page:

> Packages for those who think development versions, experimental and unstable are for old ladies. We want our crack straight from upstream git! Well, straight, we want it built and packaged so we don't need to know what we're doing, except that **[COLOR="Red"]we will break our X and put our computers on fire[/COLOR]**.

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

So there is a risk! The crack ppa is here:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

But it is a "proceed at your own peril" type thing! I closely monitor my cpu and gpu temps, and I know if I fry my hardware it's just my tough luck!

---

### Post by Gina on 2009-12-11
I've installed Lucid Alpha 1.  It boots but after a minute or so of blank screen, dumps me to a CLI login.  Log in and type **startx** and I get masses of warnings and errors flash up and off the top of the screen finally getting the words "giving up" and dumped back at the CLI.  Fortunately, **sudo reboot** works and I'm back in Jaunty! And writing this.

---

### Post by Chares on 2009-12-11
How I can add this repo?: deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main 
If gedit doesn't work (X don't start). I only write in console (terminal).

---

### Post by tekstr1der on 2009-12-11
```
sudo nano /etc/apt/sources.list
```

You might want to stay away from early alphas and wait on more stable beta release if uncomfortable without GUI.

---

### Post by andrek on 2009-12-11
Try

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by zika on 2009-12-11
> **Gina said:**
> I've installed Lucid Alpha 1.  It boots but after a minute or so of blank screen, dumps me to a CLI login.  Log in and type **startx** and I get masses of warnings and errors flash up and off the top of the screen finally getting the words "giving up" and dumped back at the CLI.  Fortunately, **sudo reboot** works and I'm back in Jaunty! And writing this.You might try ```
sudo service gdm restart
```or```
sudo service gdm start
```at CLI. Or, try adding "text" in kernel boot line and, once in CLI try startx, with or without very good advice about xorg-edgers ...

---

### Post by Regenweald on 2009-12-11
I installed karmic fresh yesterday, then did update-manager -d ***without*** first installing the proprietary drivers. Lucid is fine here. Using the fallback drivers until the binary ones are properly sorted out.

---

### Post by Chares on 2009-12-11
> **tekstr1der said:**
> ```
sudo nano /etc/apt/sources.list
```You might want to stay away from early alphas and wait on more stable beta release if uncomfortable without GUI.

It is working, but X don't start...

---

### Post by Chares on 2009-12-11
```
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```
Any ideas how resolve this?

---

### Post by Gina on 2009-12-11
That looks like what I get too.

---

### Post by Chares on 2009-12-12
When I use:
```
sudo /etc/init.d/gdm stop
sudo X
```X is running but, I have black screen.

Log running X:
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.7.99.2
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-26-xen i686 Ubuntu
Current Operating System: Linux krzysztof-desktop 2.6.32-020632-generic #020632 SMP Thu Dec 3 10:58:45 UTC 2009 i686
Kernel command line: root=UUID=6ed258a1-616e-4ff9-ad44-5bcfa3c1ca4d ro quiet vga=799 
Build Date: 11 December 2009  03:57:50PM
xorg-server 2:1.7.99.2~git20091211.12fb3181-0ubuntu0sarvatt (buildd@) 
Current version of pixman: 0.16.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: [    0.000000] (--) probed, [    0.000068] (**) from config file, [    0.000126] (==) default setting,
    [    0.000318] (++) from command line, [    0.000377] (!!) notice, [    0.000433] (II) informational,
    [    0.000624] (WW) warning, [    0.000681] (EE) error, [    0.000737] (NI) not implemented, [    0.000795] (??) unknown.
[    0.000977] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 12 10:46:12 2009
[    0.001152] (==) Using config file: "/etc/X11/xorg.conf"
[    0.001352] (==) No Layout section.  Using the first Screen section.
[    0.001366] (**) |-->Screen "Default Screen" (0)
[    0.001376] (**) |   |-->Monitor "Configured Monitor"
[    0.001665] (**) |   |-->Device "Configured Video Device"
[    0.001694] (==) Automatically adding devices
[    0.001702] (==) Automatically enabling devices
[    0.001827] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    0.001883] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    0.001892] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.001901] (II) Cannot locate a core pointer device.
[    0.001910] (II) Cannot locate a core keyboard device.
[    0.001917] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    0.001926] (II) Loader magic: 0x81f15e0
[    0.001934] (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
[    0.038614] (--) PCI:*(0:3:0:0) 1002:4150:174b:7c29 ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xc0000000/268435456, 0xe6000000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    0.038719] (--) PCI: (0:3:0:1) 1002:4170:174b:7c28 ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) rev 0, Mem @ 0xd0000000/268435456, 0xe6010000/65536
[    0.039130] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.039160] (II) LoadModule: "extmod"
[    0.039585] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    0.039798] (II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.039839] (II) Loading extension MIT-SCREEN-SAVER
[    0.039848] (II) Loading extension XFree86-VidModeExtension
[    0.039856] (II) Loading extension XFree86-DGA
[    0.039865] (II) Loading extension DPMS
[    0.039873] (II) Loading extension XVideo
[    0.039882] (II) Loading extension XVideo-MotionCompensation
[    0.039889] (II) Loading extension X-Resource
[    0.039898] (II) LoadModule: "dbe"
[    0.040110] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    0.040198] (II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.040251] (II) Loading extension DOUBLE-BUFFER
[    0.040260] (II) LoadModule: "glx"
[    0.040476] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    0.040639] (II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.040681] (==) AIGLX enabled
[    0.040694] (II) Loading extension GLX
[    0.040706] (II) LoadModule: "record"
[    0.040931] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    0.041020] (II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.041058] (II) Loading extension RECORD
[    0.041067] (II) LoadModule: "dri"
[    0.041289] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    0.041490] (II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.041526] (II) Loading extension XFree86-DRI
[    0.041540] (II) LoadModule: "dri2"
[    0.041760] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    0.041852] (II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
[    0.041885] (II) Loading extension DRI2
[    0.041902] (==) Matched ati for the autoconfigured driver
[    0.041911] (==) Assigned the driver to the xf86ConfigLayout
[    0.041920] (II) LoadModule: "ati"
[    0.042075] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    0.042160] (II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
[    0.042209] (II) LoadModule: "radeon"
[    0.042364] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    0.042668] (II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
[    0.042720] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
    ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI Radeon RV730 (AGP),
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
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI RS880
[    0.047121] (--) using VT number 7

[    0.052327] (II) Primary Device is: PCI 03@00:00:0
[    0.052555] (II) [KMS] drm report modesetting isn't supported.
[    0.052715] (II) RADEON(0): Built from git commit 0e5c9d87b5d7e0751df71cc8958ca5ccaed25104
[    0.052742] (II) RADEON(0): TOTO SAYS 00000000e6000000
[    0.052753] (II) RADEON(0): MMIO registers at 0x00000000e6000000: size 64KB
[    0.052819] (II) RADEON(0): PCI bus 3 card 0 func 0
[    0.052840] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    0.052853] (==) RADEON(0): Depth 24, [    0.052861] (--) framebuffer bpp 32
[    0.052871] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    0.052885] (==) RADEON(0): Default visual is TrueColor
[    0.052927] (II) Loading sub module "vgahw"
[    0.052936] (II) LoadModule: "vgahw"
[    0.053212] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    0.053364] (II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
[    0.053424] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.053437] (==) RADEON(0): RGB weight 888
[    0.053447] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    0.053461] (--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)
[    0.053471] (--) RADEON(0): Linear framebuffer at 0x00000000c0000000
[    0.053527] (II) RADEON(0): AGP card detected
[    0.053560] (II) Loading sub module "int10"
[    0.053569] (II) LoadModule: "int10"
[    0.053742] (II) Loading /usr/lib/xorg/modules/libint10.so
[    0.053847] (II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
[    0.053883] (II) RADEON(0): initializing int10
[    0.063981] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    0.064876] (II) RADEON(0): Legacy BIOS detected
[    0.064962] drmOpenDevice: node name is /dev/dri/card0
[    0.065157] drmOpenDevice: open result is 13, (OK)
[    0.065360] drmOpenByBusid: Searching for BusID pci:0000:03:00.0
[    0.065420] drmOpenDevice: node name is /dev/dri/card0
[    0.065581] drmOpenDevice: open result is 13, (OK)
[    0.065636] drmOpenByBusid: drmOpenMinor returns 13
[    0.065670] drmOpenByBusid: drmGetBusid reports pci:0000:03:00.0
[    0.065903] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
[    0.065964] (==) RADEON(0): Page Flipping disabled
[    0.065976] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    0.065989] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    0.065998] (II) RADEON(0): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
[    0.066012] (--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
[    0.066021] (II) RADEON(0): Color tiling enabled by default
[    0.066036] (II) Loading sub module "ddc"
[    0.066044] (II) LoadModule: "ddc"
[    0.066071] (II) Module "ddc" already built-in
[    0.066080] (II) Loading sub module "i2c"
[    0.066087] (II) LoadModule: "i2c"
[    0.066102] (II) Module "i2c" already built-in
[    0.066151] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 29700, sclk: 398.000000, mclk: 297.000000
[    0.066184] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=29700
[    0.066217] (II) RADEON(0): DFP table revision: 3
[    0.066252] (II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
[    0.066275] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    0.066293] (II) RADEON(0): Output DVI-0 has no monitor section
[    0.066303] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    0.066314] (II) RADEON(0): Output S-video has no monitor section
[    0.066324] (II) RADEON(0): Default TV standard: NTSC
[    0.066333] (II) RADEON(0): TV standards supported by chip: NTSC PAL 
[    0.066388] (II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
[    0.066440] (II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT2: INTERNAL_DAC2
  DFP1: INTERNAL_TMDS1
  DDC reg: 0x64
[    0.066517] (II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
[    0.066585] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    0.078061] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
[    0.078148] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    0.080356] (II) RADEON(0): I2C device "DVI-0:DDC control interface" registered at address 0x6E.
[    0.159938] (II) RADEON(0): EDID for output DVI-0
[    0.159970] (II) RADEON(0): Manufacturer: GSM  Model: 567e  Serial#: 52291
[    0.159981] (II) RADEON(0): Year: 2008  Week: 5
[    0.159990] (II) RADEON(0): EDID Version: 1.3
[    0.159998] (II) RADEON(0): Digital Display Input
[    0.160009] (II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    0.160027] (II) RADEON(0): Gamma: 2.20
[    0.160043] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    0.160067] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    0.160076] (II) RADEON(0): First detailed timing is preferred mode
[    0.160084] (II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[    0.160103] (II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    0.160120] (II) RADEON(0): Supported established timings:
[    0.160127] (II) RADEON(0): 720x400@70Hz
[    0.160135] (II) RADEON(0): 640x480@60Hz
[    0.160143] (II) RADEON(0): 640x480@75Hz
[    0.160150] (II) RADEON(0): 800x600@56Hz
[    0.160158] (II) RADEON(0): 800x600@60Hz
[    0.160165] (II) RADEON(0): 800x600@75Hz
[    0.160173] (II) RADEON(0): 832x624@75Hz
[    0.160181] (II) RADEON(0): 1024x768@60Hz
[    0.160188] (II) RADEON(0): 1024x768@75Hz
[    0.160196] (II) RADEON(0): 1280x1024@75Hz
[    0.160203] (II) RADEON(0): 1152x864@75Hz
[    0.160211] (II) RADEON(0): Manufacturer's mask: 0
[    0.160219] (II) RADEON(0): Supported standard timings:
[    0.160227] (II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.160236] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.160244] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.160253] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.160262] (II) RADEON(0): Supported detailed timing:
[    0.160270] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.160288] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.160303] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.160317] (II) RADEON(0): Supported detailed timing:
[    0.160325] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.160340] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.160354] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.160367] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
[    0.160381] (II) RADEON(0): Monitor name: W2252
[    0.160388] (II) RADEON(0): EDID (in hex):
[    0.160401] (II) RADEON(0):     00ffffffffffff001e6d7e5643cc0000
[    0.160414] (II) RADEON(0):     05120103ea312078eaaec5a2574a9c25
[    0.160426] (II) RADEON(0):     125054a76b80950081808140714f0101
[    0.160438] (II) RADEON(0):     0101010101017c2e90a0601a1e403020
[    0.160450] (II) RADEON(0):     3600da281100001a21399030621a2740
[    0.160462] (II) RADEON(0):     68b03600da281100001c000000fd0038
[    0.160474] (II) RADEON(0):     4b1e530f000a202020202020000000fc
[    0.160486] (II) RADEON(0):     0057323235320a202020202020200051
[    0.160497] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
[    0.160507] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.160517] (II) RADEON(0): Manufacturer: GSM  Model: 567e  Serial#: 52291
[    0.160527] (II) RADEON(0): Year: 2008  Week: 5
[    0.160535] (II) RADEON(0): EDID Version: 1.3
[    0.160543] (II) RADEON(0): Digital Display Input
[    0.160570] (II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    0.160587] (II) RADEON(0): Gamma: 2.20
[    0.160596] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    0.160620] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    0.160628] (II) RADEON(0): First detailed timing is preferred mode
[    0.160635] (II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[    0.160651] (II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    0.160667] (II) RADEON(0): Supported established timings:
[    0.160675] (II) RADEON(0): 720x400@70Hz
[    0.160683] (II) RADEON(0): 640x480@60Hz
[    0.160690] (II) RADEON(0): 640x480@75Hz
[    0.160698] (II) RADEON(0): 800x600@56Hz
[    0.160705] (II) RADEON(0): 800x600@60Hz
[    0.160712] (II) RADEON(0): 800x600@75Hz
[    0.160720] (II) RADEON(0): 832x624@75Hz
[    0.160728] (II) RADEON(0): 1024x768@60Hz
[    0.160735] (II) RADEON(0): 1024x768@75Hz
[    0.160743] (II) RADEON(0): 1280x1024@75Hz
[    0.160750] (II) RADEON(0): 1152x864@75Hz
[    0.160757] (II) RADEON(0): Manufacturer's mask: 0
[    0.160765] (II) RADEON(0): Supported standard timings:
[    0.160773] (II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.160781] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.160790] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.160798] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.160808] (II) RADEON(0): Supported detailed timing:
[    0.160816] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.160831] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.160845] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.160858] (II) RADEON(0): Supported detailed timing:
[    0.160865] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.160880] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.160893] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.160907] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
[    0.160920] (II) RADEON(0): Monitor name: W2252
[    0.160928] (II) RADEON(0): EDID (in hex):
[    0.160940] (II) RADEON(0):     00ffffffffffff001e6d7e5643cc0000
[    0.160952] (II) RADEON(0):     05120103ea312078eaaec5a2574a9c25
[    0.160964] (II) RADEON(0):     125054a76b80950081808140714f0101
[    0.160975] (II) RADEON(0):     0101010101017c2e90a0601a1e403020
[    0.160987] (II) RADEON(0):     3600da281100001a21399030621a2740
[    0.160999] (II) RADEON(0):     68b03600da281100001c000000fd0038
[    0.161011] (II) RADEON(0):     4b1e530f000a202020202020000000fc
[    0.161023] (II) RADEON(0):     0057323235320a202020202020200051
finished output detect: 1
[    0.161066] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
[    0.168544] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    0.168559] (II) RADEON(0): EDID for output VGA-0
[    0.232320] (II) RADEON(0): EDID for output DVI-0
[    0.232334] (II) RADEON(0): Manufacturer: GSM  Model: 567e  Serial#: 52291
[    0.232343] (II) RADEON(0): Year: 2008  Week: 5
[    0.232351] (II) RADEON(0): EDID Version: 1.3
[    0.232359] (II) RADEON(0): Digital Display Input
[    0.232367] (II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    0.232383] (II) RADEON(0): Gamma: 2.20
[    0.232393] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    0.232417] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    0.232425] (II) RADEON(0): First detailed timing is preferred mode
[    0.232432] (II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[    0.232449] (II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    0.232465] (II) RADEON(0): Supported established timings:
[    0.232483] (II) RADEON(0): 720x400@70Hz
[    0.232492] (II) RADEON(0): 640x480@60Hz
[    0.232499] (II) RADEON(0): 640x480@75Hz
[    0.232507] (II) RADEON(0): 800x600@56Hz
[    0.232514] (II) RADEON(0): 800x600@60Hz
[    0.232522] (II) RADEON(0): 800x600@75Hz
[    0.232529] (II) RADEON(0): 832x624@75Hz
[    0.232536] (II) RADEON(0): 1024x768@60Hz
[    0.232544] (II) RADEON(0): 1024x768@75Hz
[    0.232551] (II) RADEON(0): 1280x1024@75Hz
[    0.232559] (II) RADEON(0): 1152x864@75Hz
[    0.232566] (II) RADEON(0): Manufacturer's mask: 0
[    0.232574] (II) RADEON(0): Supported standard timings:
[    0.232582] (II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.232590] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.232599] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.232608] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.232617] (II) RADEON(0): Supported detailed timing:
[    0.232625] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.232640] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.232653] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.232667] (II) RADEON(0): Supported detailed timing:
[    0.232674] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.232689] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.232702] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.232715] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
[    0.232729] (II) RADEON(0): Monitor name: W2252
[    0.232736] (II) RADEON(0): EDID (in hex):
[    0.232748] (II) RADEON(0):     00ffffffffffff001e6d7e5643cc0000
[    0.232760] (II) RADEON(0):     05120103ea312078eaaec5a2574a9c25
[    0.232772] (II) RADEON(0):     125054a76b80950081808140714f0101
[    0.232784] (II) RADEON(0):     0101010101017c2e90a0601a1e403020
[    0.232795] (II) RADEON(0):     3600da281100001a21399030621a2740
[    0.232807] (II) RADEON(0):     68b03600da281100001c000000fd0038
[    0.232819] (II) RADEON(0):     4b1e530f000a202020202020000000fc
[    0.232831] (II) RADEON(0):     0057323235320a202020202020200051
[    0.232840] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
[    0.232849] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.232857] (II) RADEON(0): Manufacturer: GSM  Model: 567e  Serial#: 52291
[    0.232865] (II) RADEON(0): Year: 2008  Week: 5
[    0.232874] (II) RADEON(0): EDID Version: 1.3
[    0.232881] (II) RADEON(0): Digital Display Input
[    0.232889] (II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    0.232905] (II) RADEON(0): Gamma: 2.20
[    0.232914] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    0.232938] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    0.232945] (II) RADEON(0): First detailed timing is preferred mode
[    0.232953] (II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[    0.232969] (II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    0.232985] (II) RADEON(0): Supported established timings:
[    0.232993] (II) RADEON(0): 720x400@70Hz
[    0.233000] (II) RADEON(0): 640x480@60Hz
[    0.233007] (II) RADEON(0): 640x480@75Hz
[    0.233015] (II) RADEON(0): 800x600@56Hz
[    0.233022] (II) RADEON(0): 800x600@60Hz
[    0.233030] (II) RADEON(0): 800x600@75Hz
[    0.233037] (II) RADEON(0): 832x624@75Hz
[    0.233045] (II) RADEON(0): 1024x768@60Hz
[    0.233052] (II) RADEON(0): 1024x768@75Hz
[    0.233060] (II) RADEON(0): 1280x1024@75Hz
[    0.233067] (II) RADEON(0): 1152x864@75Hz
[    0.233075] (II) RADEON(0): Manufacturer's mask: 0
[    0.233083] (II) RADEON(0): Supported standard timings:
[    0.233091] (II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.233099] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.233108] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.233128] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.233138] (II) RADEON(0): Supported detailed timing:
[    0.233146] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.233161] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.233174] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.233187] (II) RADEON(0): Supported detailed timing:
[    0.233195] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.233209] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.233223] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.233236] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
[    0.233249] (II) RADEON(0): Monitor name: W2252
[    0.233257] (II) RADEON(0): EDID (in hex):
[    0.233269] (II) RADEON(0):     00ffffffffffff001e6d7e5643cc0000
[    0.233281] (II) RADEON(0):     05120103ea312078eaaec5a2574a9c25
[    0.233292] (II) RADEON(0):     125054a76b80950081808140714f0101
[    0.233304] (II) RADEON(0):     0101010101017c2e90a0601a1e403020
[    0.233316] (II) RADEON(0):     3600da281100001a21399030621a2740
[    0.233328] (II) RADEON(0):     68b03600da281100001c000000fd0038
[    0.233340] (II) RADEON(0):     4b1e530f000a202020202020000000fc
[    0.233352] (II) RADEON(0):     0057323235320a202020202020200051
[    0.233365] (II) RADEON(0): Panel infos found from DDC detailed: 1680x1050
[    0.233376] (II) RADEON(0): EDID vendor "GSM", prod id 22142
[    0.233445] (II) RADEON(0): Printing probed modes for output DVI-0
[    0.233459] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    0.233476] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    0.233493] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    0.233508] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    0.233524] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    0.233540] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    0.233554] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.233569] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.233584] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.233600] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.233615] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.233630] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.233644] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.233659] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.233674] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.233689] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    0.233704] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    0.233714] (II) RADEON(0): EDID for output S-video
[    0.233726] (II) RADEON(0): Output VGA-0 disconnected
[    0.233735] (II) RADEON(0): Output DVI-0 connected
[    0.233744] (II) RADEON(0): Output S-video disconnected
[    0.233765] (II) RADEON(0): Using exact sizes for initial modes
[    0.233775] (II) RADEON(0): Output DVI-0 using initial mode 1680x1050
[    0.233802] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    0.233824] (==) RADEON(0): DPI set to (96, 96)
[    0.233833] (II) Loading sub module "fb"
[    0.233842] (II) LoadModule: "fb"
[    0.234085] (II) Loading /usr/lib/xorg/modules/libfb.so
[    0.234288] (II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
[    0.234328] (II) Loading sub module "ramdac"
[    0.234336] (II) LoadModule: "ramdac"
[    0.234354] (II) Module "ramdac" already built-in
[    0.234367] (==) RADEON(0): Using EXA acceleration architecture
[    0.234375] (II) Loading sub module "exa"
[    0.234383] (II) LoadModule: "exa"
[    0.234575] (II) Loading /usr/lib/xorg/modules/libexa.so
[    0.234679] (II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
[    0.234717] (==) RADEON(0): Assuming overlay scaler buffer width is 1920
[    0.234727] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    0.234887] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    0.234926] (--) Depth 24 pixmap format is 32 bpp
[    0.234979] (II) RADEON(0): RADEONScreenInit c0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable FP1
[    0.342901] (II) RADEON(0): Dynamic Power Management Disabled
[    0.342939] (==) RADEON(0): Using 24 bit depth buffer
[    0.342954] (II) RADEON(0): RADEONInitMemoryMap() : 
[    0.342962] (II) RADEON(0):   mem_size         : 0x08000000
[    0.342970] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000
[    0.342978] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    0.342988] (II) RADEON(0): Depth moves disabled by default
[    0.343030] (II) RADEON(0): Allocating from a screen of 131072 kb
[    0.343040] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00b13000
[    0.343050] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00b17000
[    0.343059] (II) RADEON(0): Will use 11340 kb for front buffer at offset 0x00000000
[    0.343071] (II) RADEON(0): Will use 11340 kb for back buffer at offset 0x00b1b000
[    0.343080] (II) RADEON(0): Will use 11340 kb for depth buffer at offset 0x0162e000
[    0.343089] (II) RADEON(0): Will use 48128 kb for textures at offset 0x02141000
[    0.343098] (II) RADEON(0): Will use 48892 kb for X Server offscreen at offset 0x05041000
[    0.343151] drmOpenDevice: node name is /dev/dri/card0
[    0.343380] drmOpenDevice: open result is 13, (OK)
[    0.343603] drmOpenDevice: node name is /dev/dri/card0
[    0.343804] drmOpenDevice: open result is 13, (OK)
[    0.343982] drmOpenByBusid: Searching for BusID pci:0000:03:00.0
[    0.344041] drmOpenDevice: node name is /dev/dri/card0
[    0.344207] drmOpenDevice: open result is 13, (OK)
[    0.344262] drmOpenByBusid: drmOpenMinor returns 13
[    0.344285] drmOpenByBusid: drmGetBusid reports pci:0000:03:00.0
[    0.344312] (II) [drm] DRM interface version 1.3
[    0.344375] (II) [drm] DRM open master succeeded.
[    0.344408] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    0.344421] (II) RADEON(0): [drm] framebuffer handle = 0xc0000000
[    0.344455] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    0.344479] (II) RADEON(0): X context handle = 0x1
[    0.344526] (II) RADEON(0): [drm] installed DRM signal handler
[    0.344556] (==) RADEON(0): Using AGP 8x
[    0.344567] (II) RADEON(0): [agp] Mode 0x1f00420a [AGP 0x10de/0x01e0; Card 0x1002/0x4150 0x174b/0x7c29]
[    0.385457] (II) RADEON(0): [agp] 32768 kB allocated with handle 0x00000001
[    0.387133] (II) RADEON(0): [agp] ring handle = 0xe0000000
[    0.387233] (II) RADEON(0): [agp] Ring mapped at 0xb70b2000
[    0.387247] (II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
[    0.387263] (II) RADEON(0): [agp] Ring read ptr mapped at 0xb70b1000
[    0.387296] (II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
[    0.387375] (II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaee32000
[    0.387389] (II) RADEON(0): [agp] GART texture map handle = 0xe0302000
[    0.388232] (II) RADEON(0): [agp] GART Texture map mapped at 0xad1b2000
[    0.388283] (II) RADEON(0): [drm] register handle = 0x2cc00000
[    0.388311] (II) RADEON(0): [dri] Visual configs initialized
[    0.388428] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.388439] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000 0x1fff0000
[    0.388448] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    0.588634] (==) RADEON(0): Backing store disabled
[    0.588657] (II) RADEON(0): [DRI] installation complete
[    0.597852] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    0.597988] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    0.598039] (II) RADEON(0): [drm] dma control initialized, using IRQ 19
[    0.598053] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
[    0.598083] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    0.598093] (WW) RADEON(0):   MC_FB_LOCATION  was: 0xc7ffc000 is: 0xc7ffc000
[    0.598103] (WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe1ffe000
[    0.598114] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.598122] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000 0xc7ffc000
[    0.598131] (II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
[    0.698233] (II) RADEON(0): Direct rendering enabled
[    0.698345] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    0.698358] (II) RADEON(0): Setting EXA maxPitchBytes
[    0.698384] (II) RADEON(0): num quad-pipes is 1
[    0.698448] (II) EXA(0): Offscreen pixmap area of 50065408 bytes
[    0.698466] (II) EXA(0): Driver registered support for the following operations:
[    0.698474] (II)         Solid
[    0.698481] (II)         Copy
[    0.698487] (II)         Composite (RENDER acceleration)
[    0.698494] (II)         UploadToScreen
[    0.698506] (II) RADEON(0): Acceleration enabled
[    0.698520] (==) RADEON(0): DPMS enabled
[    0.698536] (==) RADEON(0): Silken mouse enabled
[    0.698613] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    0.698629] (II) Loading sub module "theatre_detect"
[    0.698638] (II) LoadModule: "theatre_detect"
[    0.698847] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    0.699013] (II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
[    0.699057] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    0.699108] (II) RADEON(0): Set up overlay video
[    0.699147] (II) RADEON(0): Set up textured video
disable primary dac
disable FP1
disable TV
disable FP1
init memmap
init common
init crtc1
init pll1
freq: 119000000
best_freq: 119000000
best_feedback_div: 238
best_frac_feedback_div: 0
best_ref_div: 27
best_post_div: 2
restore memmap
[    0.749532] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.749541] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000 0xc7ffc000
[    0.749550] (II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set FP1
enable FP1
disable primary dac
disable TV
[    0.899934] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    0.900159] (--) RandR disabled
[    0.900178] (II) Initializing built-in extension Generic Event Extension
[    0.900187] (II) Initializing built-in extension SHAPE
[    0.900195] (II) Initializing built-in extension MIT-SHM
[    0.900202] (II) Initializing built-in extension XInputExtension
[    0.900209] (II) Initializing built-in extension XTEST
[    0.900216] (II) Initializing built-in extension BIG-REQUESTS
[    0.900224] (II) Initializing built-in extension SYNC
[    0.900231] (II) Initializing built-in extension XKEYBOARD
[    0.900253] (II) Initializing built-in extension XC-MISC
[    0.900261] (II) Initializing built-in extension SECURITY
[    0.900269] (II) Initializing built-in extension XINERAMA
[    0.900276] (II) Initializing built-in extension XFIXES
[    0.900283] (II) Initializing built-in extension RENDER
[    0.900290] (II) Initializing built-in extension RANDR
[    0.900297] (II) Initializing built-in extension COMPOSITE
[    0.900304] (II) Initializing built-in extension DAMAGE
record: RECORD extension enabled at configure time.
record: This extension is known to be broken, disabling extension now..
record: http://bugs.freedesktop.org/show_bug.cgi?id=20500
[    0.911238] (II) AIGLX: Screen 0 is not DRI2 capable
[    0.911272] drmOpenDevice: node name is /dev/dri/card0
[    0.911309] drmOpenDevice: open result is 14, (OK)
[    0.911335] drmOpenByBusid: Searching for BusID pci:0000:03:00.0
[    0.911347] drmOpenDevice: node name is /dev/dri/card0
[    0.911362] drmOpenDevice: open result is 14, (OK)
[    0.911371] drmOpenByBusid: drmOpenMinor returns 14
[    0.911381] drmOpenByBusid: drmGetBusid reports pci:0000:03:00.0
[    0.917343] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    0.917387] (II) AIGLX: enabled GLX_SGI_make_current_read
[    0.917396] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    0.917403] (II) AIGLX: enabled GLX_texture_from_pixmap with driver support
[    0.917453] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    0.917463] (II) GLX: Initialized DRI GL provider for screen 0
[    0.917990] (II) RADEON(0): Setting screen physical size to 444 x 277
[    1.011840] (II) config/udev: Adding input device "Power Button" (/dev/input/event1)
[    1.011884] (II) LoadModule: "evdev"
[    1.012070] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    1.012232] (II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.99.2, module version = 2.3.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
[    1.012309] (**) "Power Button": always reports core events
[    1.012325] (**) "Power Button": Device: "/dev/input/event1"
[    1.012377] (II) "Power Button": Found keys
[    1.012388] (II) "Power Button": Configuring as keyboard
[    1.012407] (II) XINPUT: Adding extended input device ""Power Button"" (type: KEYBOARD)
[    1.012424] (**) Option "xkb_rules" "evdev"
[    1.012441] (**) Option "xkb_model" "pc105"
[    1.012458] (**) Option "xkb_layout" "pl"
[    1.069363] (II) config/udev: Adding input device "Power Button" (/dev/input/event0)
[    1.069427] (**) "Power Button": always reports core events
[    1.069441] (**) "Power Button": Device: "/dev/input/event0"
[    1.069476] (II) "Power Button": Found keys
[    1.069487] (II) "Power Button": Configuring as keyboard
[    1.069507] (II) XINPUT: Adding extended input device ""Power Button"" (type: KEYBOARD)
[    1.069519] (**) Option "xkb_rules" "evdev"
[    1.069537] (**) Option "xkb_model" "pc105"
[    1.069553] (**) Option "xkb_layout" "pl"
[    1.070141] (II) config/udev: Adding input device "AT Translated Set 2 keyboard" (/dev/input/event3)
[    1.070181] (**) "AT Translated Set 2 keyboard": always reports core events
[    1.070193] (**) "AT Translated Set 2 keyboard": Device: "/dev/input/event3"
[    1.070220] (II) "AT Translated Set 2 keyboard": Found keys
[    1.070230] (II) "AT Translated Set 2 keyboard": Configuring as keyboard
[    1.070245] (II) XINPUT: Adding extended input device ""AT Translated Set 2 keyboard"" (type: KEYBOARD)
[    1.070257] (**) Option "xkb_rules" "evdev"
[    1.070273] (**) Option "xkb_model" "pc105"
[    1.070289] (**) Option "xkb_layout" "pl"
[    1.070856] (II) config/udev: Adding input device "ImExPS/2 Generic Explorer Mouse" (/dev/input/event4)
[    1.070924] (**) "ImExPS/2 Generic Explorer Mouse": always reports core events
[    1.070939] (**) "ImExPS/2 Generic Explorer Mouse": Device: "/dev/input/event4"
[    1.070967] (II) "ImExPS/2 Generic Explorer Mouse": Found 9 mouse buttons
[    1.070977] (II) "ImExPS/2 Generic Explorer Mouse": Found scroll wheel(s)
[    1.070996] (II) "ImExPS/2 Generic Explorer Mouse": Found relative axes
[    1.071004] (II) "ImExPS/2 Generic Explorer Mouse": Found x and y relative axes
[    1.071012] (II) "ImExPS/2 Generic Explorer Mouse": Configuring as mouse
[    1.071028] (**) "ImExPS/2 Generic Explorer Mouse": YAxisMapping: buttons 4 and 5
[    1.071038] (**) "ImExPS/2 Generic Explorer Mouse": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.071054] (II) XINPUT: Adding extended input device ""ImExPS/2 Generic Explorer Mouse"" (type: MOUSE)
[    1.071119] (**) "ImExPS/2 Generic Explorer Mouse": (accel) keeping acceleration scheme 1
[    1.071134] (**) "ImExPS/2 Generic Explorer Mouse": (accel) acceleration profile 0
[    1.071154] (II) "ImExPS/2 Generic Explorer Mouse": initialized for relative axes.
[    1.071636] (II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/event2)
[    1.071672] (**) "Macintosh mouse button emulation": always reports core events
[    1.071684] (**) "Macintosh mouse button emulation": Device: "/dev/input/event2"
[    1.071713] (II) "Macintosh mouse button emulation": Found 3 mouse buttons
[    1.071723] (II) "Macintosh mouse button emulation": Found relative axes
[    1.071730] (II) "Macintosh mouse button emulation": Found x and y relative axes
[    1.071738] (II) "Macintosh mouse button emulation": Configuring as mouse
[    1.071750] (**) "Macintosh mouse button emulation": YAxisMapping: buttons 4 and 5
[    1.071759] (**) "Macintosh mouse button emulation": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.071773] (II) XINPUT: Adding extended input device ""Macintosh mouse button emulation"" (type: MOUSE)
[    1.071803] (**) "Macintosh mouse button emulation": (accel) keeping acceleration scheme 1
[    1.071816] (**) "Macintosh mouse button emulation": (accel) acceleration profile 0
[    1.071835] (II) "Macintosh mouse button emulation": initialized for relative axes.
```My xorg-conf file:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen1" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
    Load  "record"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      490   320    # mm
    Identifier   "Monitor1"
    VendorName   "GSM"
    ModelName    "W2252"
    HorizSync    30.0 - 83.0
    VertRefresh  56.0 - 75.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AP [Radeon 9600]"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

Please help.

---

### Post by goldberg333 on 2009-12-21
Hello, everybody. I've got geforce m8600gt and neither ubuntu nor kubuntu can't start x server. I recieve a segmentation fault and tty2 appears. Upgrade from xorg:edgers didn't help. It doesn't work with nvidia drivers (185,190) and obviously with standard drivers ('cause I can't even start graphical installation wizzard, so I had to install kubuntu from alternate cd)
Does anybody know how to overcome this? Thanks in advance.

---

### Post by Kobalt on 2009-12-21
I've had troubles booting as well, after today's updates. But booting to a root shell and restarting GDM does the trick.

---

