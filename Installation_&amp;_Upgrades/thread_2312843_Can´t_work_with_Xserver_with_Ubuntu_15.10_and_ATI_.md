---
title: "Can´t work with Xserver with Ubuntu 15.10 and ATI video card"
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by pedro-prados on 2016-02-07
Hi

On a reboot the graphics enviorement are dead. I was read many workarounds, try diferent combination, but the result has same, nothing. On the original instalation all work fine, i was work with unity. Now i can´t find the correct solution. The configuration data are this:

**System**
```
Ubuntu 15.10 \n \l
Linux ubuntu 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

**Video Card**
```
root@ubuntu:~# sudo lshw -C video
  *-display NO RECLAMADO
       descripción: VGA compatible controller
       producto: RV710 [Radeon HD 4350/4550]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi vga_controller bus_master cap_list
       configuración: latency=0
       recursos: memoria:d0000000-dfffffff memoria:fdee0000-fdeeffff ioport:de00(size=256) memoria:fde00000-fde1ffff
```


**No have /etc/X11/xorg.conf**
```
root@ubuntu:~# sudo aticonfig --initial -f
MobaXterm X11 proxy: Unsupported authorisation protocol
aticonfig: No supported adapters detected
```

**Can´t  start X**

```
root@ubuntu:~# startx
X.Org X Server 1.17.2
Release Date: 2015-06-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
Current Operating System: Linux ubuntu 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-19-generic root=UUID=0cf58171-bb90-458e-81c0-8e906fecf256 ro
Build Date: 12 November 2015  05:33:29PM
xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.32.6
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  7 23:04:30 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
modprobe: ERROR: could not insert 'fglrx_updates': No such device
(II) [KMS] drm report modesetting isn't supported.
(EE)
Fatal server error:
(EE) no screens found(EE)
(EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
```

**Test radeon driver**
```
root@ubuntu:~# modprobe radeon
modprobe: ERROR: ../libkmod/libkmod-module.c:832 kmod_module_insert_module() could not find module by name='off'
modprobe: ERROR: could not insert 'off': Function not implemented
```


But on the system i can´t find the file libkmod-module.c

**Lasted driver install used, whitout errors**
```
radeon-crimson-15.12-15.302-151217a-297685e.zip
```

**Another use after**
```
amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
```

**fglxr packages installed now.**
```
root@ubuntu:/usr/local/src# dpkg --get-selections | grep fgl
fglrx                                           install
fglrx-amdcccle-updates                          install
fglrx-core                                      install
fglrx-updates                                   install
fglrx-updates-core                              install
```

[B]Xorg packages installed now.
[/B]root@ubuntu:/usr/local/src# dpkg --get-selections | grep xorg
```
xorg-docs-core                                  install
xserver-xorg                                    install
xserver-xorg-core                               install
xserver-xorg-input-all                          install
xserver-xorg-input-evdev                        install
xserver-xorg-input-mouse                        install
xserver-xorg-input-synaptics                    install
xserver-xorg-input-vmmouse                      install
xserver-xorg-input-wacom                        install
xserver-xorg-video-amdgpu                       install
xserver-xorg-video-amdgpu-dbg                   install
xserver-xorg-video-ati                          install
xserver-xorg-video-intel                        deinstall
xserver-xorg-video-mach64                       install
xserver-xorg-video-openchrome                   deinstall
xserver-xorg-video-r128                         install
xserver-xorg-video-radeon                       install
xserver-xorg-video-vmware                       deinstall
```

**mesa**
```
root@menrva:/usr/local/src# dpkg --get-selections | grep mesa
libegl1-mesa:amd64                              install
libgl1-mesa-dri:amd64                           install
libgl1-mesa-glx:amd64                           install
libglapi-mesa:amd64                             install
libglu1-mesa:amd64                              install
libwayland-egl1-mesa:amd64                      install
mesa-utils                                      install
mir-client-platform-mesa2:amd64                 deinstall
```



**Last Xorg.0.log**
[  2240.506]
```
X.Org X Server 1.17.2
Release Date: 2015-06-16
[  2240.506] X Protocol Version 11, Revision 0
[  2240.506] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[  2240.506] Current Operating System: Linux menrva 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64
[  2240.506] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-19-generic root=UUID=0cf58171-bb90-458e-81c0-8e906fecf256 ro
[  2240.506] Build Date: 12 November 2015  05:33:29PM
[  2240.506] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[  2240.506] Current version of pixman: 0.32.6
[  2240.506]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[  2240.506] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2240.506] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  7 23:04:30 2016
[  2240.506] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2240.507] (==) No Layout section.  Using the first Screen section.
[  2240.507] (==) No screen section available. Using defaults.
[  2240.507] (**) |-->Screen "Default Screen Section" (0)
[  2240.507] (**) |   |-->Monitor "<default monitor>"
[  2240.507] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[  2240.507] (==) Automatically adding devices
[  2240.507] (==) Automatically enabling devices
[  2240.507] (==) Automatically adding GPU devices
[  2240.507] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2240.507]    Entry deleted from font path.
[  2240.507] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2240.507]    Entry deleted from font path.
[  2240.507] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2240.507]    Entry deleted from font path.
[  2240.507] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2240.507]    Entry deleted from font path.
[  2240.507] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2240.507]    Entry deleted from font path.
[  2240.507] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[  2240.507] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2240.507] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2240.507] (II) Loader magic: 0x5646c5082d40
[  2240.507] (II) Module ABI versions:
[  2240.507]    X.Org ANSI C Emulation: 0.4
[  2240.507]    X.Org Video Driver: 19.0
[  2240.507]    X.Org XInput driver : 21.0
[  2240.507]    X.Org Server Extension : 9.0
[  2240.508] (--) PCI:*(0:1:0:0) 1002:954f:1462:1615 rev 0, Mem @ 0xd0000000/268435456, 0xfdee0000/65536, I/O @ 0x0000de00/256, BIOS @
 0x????????/131072
[  2240.508] (II) LoadModule: "glx"
[  2240.509] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[  2240.509] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[  2240.509]    compiled for 6.9.0, module version = 1.0.0
[  2240.509] (==) Matched fglrx as autoconfigured driver 0
[  2240.509] (==) Matched ati as autoconfigured driver 1
[  2240.509] (==) Matched modesetting as autoconfigured driver 2
[  2240.509] (==) Matched fbdev as autoconfigured driver 3
[  2240.509] (==) Matched vesa as autoconfigured driver 4
[  2240.509] (==) Assigned the driver to the xf86ConfigLayout
[  2240.509] (II) LoadModule: "fglrx"
[  2240.509] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[  2240.532] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[  2240.532]    compiled for 1.4.99.906, module version = 15.20.3
[  2240.532]    Module class: X.Org Video Driver
[  2240.533] (II) Loading sub module "fglrxdrm"
[  2240.533] (II) LoadModule: "fglrxdrm"
[  2240.533] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[  2240.533] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[  2240.533]    compiled for 1.4.99.906, module version = 15.20.3
[  2240.533] (II) LoadModule: "ati"
[  2240.533] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2240.533] (II) Module ati: vendor="X.Org Foundation"
[  2240.533]    compiled for 1.17.2, module version = 7.5.99
[  2240.533]    Module class: X.Org Video Driver
[  2240.533]    ABI class: X.Org Video Driver, version 19.0
[  2240.533] (II) LoadModule: "radeon"
[  2240.534] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  2240.534] (II) Module radeon: vendor="X.Org Foundation"
[  2240.534]    compiled for 1.17.2, module version = 7.5.99
[  2240.534]    Module class: X.Org Video Driver
[  2240.534]    ABI class: X.Org Video Driver, version 19.0
[  2240.534] (II) LoadModule: "modesetting"
[  2240.534] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  2240.534] (II) Module modesetting: vendor="X.Org Foundation"
[  2240.534]    compiled for 1.17.2, module version = 1.17.2
[  2240.534]    Module class: X.Org Video Driver
[  2240.534]    ABI class: X.Org Video Driver, version 19.0
[  2240.534] (II) LoadModule: "fbdev"
[  2240.534] (WW) Warning, couldn't open module fbdev
[  2240.534] (II) UnloadModule: "fbdev"
[  2240.534] (II) Unloading fbdev
[  2240.535] (EE) Failed to load module "fbdev" (module does not exist, 0)
[  2240.535] (II) LoadModule: "vesa"
[  2240.535] (WW) Warning, couldn't open module vesa
[  2240.535] (II) UnloadModule: "vesa"
[  2240.535] (II) Unloading vesa
[  2240.535] (EE) Failed to load module "vesa" (module does not exist, 0)
[  2240.535] (==) Matched fglrx as autoconfigured driver 0
[  2240.535] (==) Matched ati as autoconfigured driver 1
[  2240.535] (==) Matched modesetting as autoconfigured driver 2
[  2240.535] (==) Matched fbdev as autoconfigured driver 3
[  2240.535] (==) Matched vesa as autoconfigured driver 4
[  2240.535] (==) Assigned the driver to the xf86ConfigLayout
[  2240.535] (II) LoadModule: "fglrx"
[  2240.535] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[  2240.535] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[  2240.535]    compiled for 1.4.99.906, module version = 15.20.3
[  2240.535]    Module class: X.Org Video Driver
[  2240.535] (II) LoadModule: "ati"
[  2240.535] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2240.535] (II) Module ati: vendor="X.Org Foundation"
[  2240.535]    compiled for 1.17.2, module version = 7.5.99
[  2240.535]    Module class: X.Org Video Driver
[  2240.535]    ABI class: X.Org Video Driver, version 19.0
[  2240.535] (II) LoadModule: "modesetting"
[  2240.535] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  2240.535] (II) Module modesetting: vendor="X.Org Foundation"
[  2240.536]    compiled for 1.17.2, module version = 1.17.2
[  2240.536]    Module class: X.Org Video Driver
[  2240.536]    ABI class: X.Org Video Driver, version 19.0
[  2240.536] (II) UnloadModule: "modesetting"
[  2240.536] (II) Unloading modesetting
[  2240.536] (II) Failed to load module "modesetting" (already loaded, 22086)
[  2240.536] (II) LoadModule: "fbdev"
[  2240.536] (WW) Warning, couldn't open module fbdev
[  2240.536] (II) UnloadModule: "fbdev"
[  2240.536] (II) Unloading fbdev
[  2240.536] (EE) Failed to load module "fbdev" (module does not exist, 0)
[  2240.536] (II) LoadModule: "vesa"
[  2240.536] (WW) Warning, couldn't open module vesa
[  2240.536] (II) UnloadModule: "vesa"
[  2240.536] (II) Unloading vesa
[  2240.536] (EE) Failed to load module "vesa" (module does not exist, 0)
[  2240.536] (II) AMD Proprietary Linux Driver Version Identifier:15.20.3
[  2240.536] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.201.1151
[  2240.536] (II) AMD Proprietary Linux Driver Build Date: Sep  8 2015 15:06:35
[  2240.536] (II) RADEON: Driver for ATI Radeon chipsets:
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
        SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
        VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
        OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
        OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
        BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
        BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
        KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
        KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
        MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
        MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
        KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
        KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
        KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
        HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[  2240.542] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  2240.542] (--) using VT number 2


[  2240.550] (WW) Falling back to old probe method for fglrx
[  2240.564] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[  2240.641] ukiDynamicMajor: failed to open /proc/ati/major
[  2240.643] (EE) No supported AMD display adapters were found
[  2240.644] (II) [KMS] drm report modesetting isn't supported.
[  2240.644] (EE) open /dev/dri/card0: No such file or directory
[  2240.644] (EE) open /dev/dri/card0: No such file or directory
[  2240.644] (WW) Falling back to old probe method for modesetting
[  2240.644] (EE) open /dev/dri/card0: No such file or directory
[  2240.644] (EE) open /dev/dri/card0: No such file or directory
[  2240.644] (EE) Screen 0 deleted because of no matching config section.
[  2240.644] (II) UnloadModule: "radeon"
[  2240.644] (EE) Screen 0 deleted because of no matching config section.
[  2240.644] (II) UnloadModule: "modesetting"
[  2240.644] (EE) Screen 0 deleted because of no matching config section.
[  2240.644] (II) UnloadModule: "modesetting"
[  2240.644] (EE) Device(s) detected, but none match those in the config file.
[  2240.644] (EE)
Fatal server error:
[  2240.644] (EE) no screens found(EE)
[  2240.644] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[  2240.644] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2240.644] (EE)
[  2240.661] (EE) Server terminated with error (1). Closing log file.
```


Can anybody help me? I am desperate.

at least it's therapeutic to put it and hope

---

### Post by matt_symes on 2016-02-07
@pedro-prados

Please use code tags for any output from the terminal.

You use code tags like this

[noparse]```
output from terminal
```[/noparse]

to get output like this

```
output from terminal
```

Code tags aid readability and keep formatting.

---

### Post by pedro-prados on 2016-02-08
Hi Thanks for formatting my case, i belive that is my first caso on ubuntu forum.  Now I stop with the GUI error on the server and continue work on this for will have a Docker envioroment with Kubernetes. I want that this server will be a master node for the kubernetes cluster for test migration my applications to docker. I need test this funcionality and test my dockers. Need migrate application with wor fine results, because on the future clone the dockers to AWS and work with this technology on the future. On AWS i was deploment one Ubuntu Server 14.04 LTS for Dockers and want too test the native enviroment for dockers of amazon, dockers as a service, for find the optimized solution for the use dockers on enviroment multi-server. 

The server afected for the gui problem is the server for work whit this. No i can continue on console mode, but need recover the X and unity for work localy on this server and the remote access  SSH was an alternative for learn. On the future when i wil be finish all scripts for manager docker soluction, can be work only ssh with the GUI Kubernetes on production enviroment, the server affected for this problem is local. Thanks for your attention.

---

### Post by pedro-prados on 2016-02-08
Hi for complete this information

**dmesg output**
```

[  244.724041] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7749 MBytes.
[  244.724512] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[  244.724515] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[  245.044042] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7749 MBytes.
[  245.044508] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[  245.044511] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[  245.368066] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7749 MBytes.
[  245.368527] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[  245.368530] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[ 1238.060034] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7749 MBytes.
[ 1238.060557] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[ 1238.060560] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[ 1308.460034] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7749 MBytes.
[ 1308.460503] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[ 1308.460505] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[ 2240.608037] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7749 MBytes.
[ 2240.608504] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[ 2240.608507] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[ 5693.179986] perf interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

```

---

