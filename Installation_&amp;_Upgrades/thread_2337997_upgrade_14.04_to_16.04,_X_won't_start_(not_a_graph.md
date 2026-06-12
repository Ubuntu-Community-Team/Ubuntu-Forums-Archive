---
title: "upgrade 14.04 to 16.04, X won't start (not a graphics issue?)"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by denter2 on 2016-09-23
Hello everybody,
I installed xubuntu 14.04 on a friend's laptop a year back.
a couple of weeks ago, she agreed to upgrade to 16.04, and after that all she got was a black screen when booting.

i have the machine here now.
the system is upgraded, it is 16.04.1 LTS now, but the graphical session won't start.

Or, to be more precise, it looks like it starts ok, but stays completely black.

```
lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Fujitsu Technology Solutions Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915, intelfb
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Conexant softmodem SmartCP
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Fujitsu Technology Solutions NM10/ICH7 Family USB UHCI Controller
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Fujitsu Technology Solutions NM10/ICH7 Family USB UHCI Controller
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Fujitsu Technology Solutions NM10/ICH7 Family USB UHCI Controller
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Fujitsu Technology Solutions NM10/ICH7 Family USB UHCI Controller
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions NM10/ICH7 Family USB2 EHCI Controller
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Fujitsu Technology Solutions 82801GBM (ICH7-M) LPC Interface Bridge
    Kernel driver in use: lpc_ich
    Kernel modules: intel_rng, lpc_ich, leds_ss4200
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions 82801G (ICH7 Family) IDE Controller
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
    Subsystem: Fujitsu Technology Solutions 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions NM10/ICH7 Family SMBus Controller
    Kernel modules: i2c_i801
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation WM3945ABG MOW2
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
    Subsystem: Fujitsu Technology Solutions PRO/100 VE Network Connection
    Kernel driver in use: e100
    Kernel modules: e100
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
    Subsystem: Fujitsu Technology Solutions R5C832 IEEE 1394 Controller
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Fujitsu Technology Solutions R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci
07:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
    Subsystem: Fujitsu Technology Solutions R5C592 Memory Stick Bus Host Adapter
    Kernel driver in use: r592
    Kernel modules: r592
07:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
    Subsystem: Fujitsu Technology Solutions xD-Picture Card Controller
    Kernel driver in use: r852
    Kernel modules: r852
```
yes, not the newest anymore.


```
cat /var/log/Xorg.0.log
[   324.434] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[   324.434] X Protocol Version 11, Revision 0
[   324.434] Build Operating System: Linux 3.13.0-92-generic i686 Ubuntu
[   324.434] Current Operating System: Linux thinkpad 3.16.0-77-generic #99~14.04.1-Ubuntu SMP Tue Jun 28 19:18:41 UTC 2016 i686
[   324.434] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-77-generic root=UUID=b3450d19-8ac3-4084-85d4-d423e7cf4ffa ro quiet splash atkbd.reset vt.handoff=7
[   324.434] Build Date: 22 July 2016  07:50:53AM
[   324.434] xorg-server 2:1.18.3-1ubuntu2.3 (For technical support please see http://www.ubuntu.com/support) 
[   324.435] Current version of pixman: 0.33.6
[   324.435]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   324.435] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   324.435] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 23 19:25:19 2016
[   324.435] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   324.435] (==) No Layout section.  Using the first Screen section.
[   324.435] (==) No screen section available. Using defaults.
[   324.435] (**) |-->Screen "Default Screen Section" (0)
[   324.435] (**) |   |-->Monitor "<default monitor>"
[   324.436] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   324.436] (==) Automatically adding devices
[   324.436] (==) Automatically enabling devices
[   324.436] (==) Automatically adding GPU devices
[   324.436] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   324.436] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   324.436]     Entry deleted from font path.
[   324.436] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   324.436]     Entry deleted from font path.
[   324.436] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   324.436]     Entry deleted from font path.
[   324.436] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   324.436]     Entry deleted from font path.
[   324.436] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   324.436]     Entry deleted from font path.
[   324.436] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   324.436] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   324.436] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   324.436] (II) Loader magic: 0xb77b7700
[   324.436] (II) Module ABI versions:
[   324.436]     X.Org ANSI C Emulation: 0.4
[   324.436]     X.Org Video Driver: 20.0
[   324.436]     X.Org XInput driver : 22.1
[   324.436]     X.Org Server Extension : 9.0
[   324.437] (++) using VT number 7

[   324.437] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[   324.438] (II) xfree86: Adding drm device (/dev/dri/card0)
[   324.441] (--) PCI:*(0:0:2:0) 8086:27a2:1734:10ad rev 3, Mem @ 0xdc100000/524288, 0xc0000000/268435456, 0xdc200000/262144, I/O @ 0x00001800/8
[   324.441] (--) PCI: (0:0:2:1) 8086:27a6:1734:10ad rev 3, Mem @ 0xdc180000/524288
[   324.441] (II) LoadModule: "glx"
[   324.441] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   324.442] (EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so: libGL.so.1: cannot open shared object file: No such file or directory
[   324.442] (II) UnloadModule: "glx"
[   324.442] (II) Unloading glx
[   324.442] (EE) Failed to load module "glx" (loader failed, 7)
[   324.442] (==) Matched intel as autoconfigured driver 0
[   324.442] (==) Matched intel as autoconfigured driver 1
[   324.442] (==) Matched modesetting as autoconfigured driver 2
[   324.442] (==) Matched fbdev as autoconfigured driver 3
[   324.442] (==) Matched vesa as autoconfigured driver 4
[   324.442] (==) Assigned the driver to the xf86ConfigLayout
[   324.442] (II) LoadModule: "intel"
[   324.442] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   324.443] (II) Module intel: vendor="X.Org Foundation"
[   324.443]     compiled for 1.18.1, module version = 2.99.917
[   324.443]     Module class: X.Org Video Driver
[   324.443]     ABI class: X.Org Video Driver, version 20.0
[   324.443] (II) LoadModule: "modesetting"
[   324.443] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   324.443] (II) Module modesetting: vendor="X.Org Foundation"
[   324.443]     compiled for 1.18.3, module version = 1.18.3
[   324.443]     Module class: X.Org Video Driver
[   324.443]     ABI class: X.Org Video Driver, version 20.0
[   324.443] (II) LoadModule: "fbdev"
[   324.443] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   324.444] (II) Module fbdev: vendor="X.Org Foundation"
[   324.444]     compiled for 1.18.1, module version = 0.4.4
[   324.444]     Module class: X.Org Video Driver
[   324.444]     ABI class: X.Org Video Driver, version 20.0
[   324.444] (II) LoadModule: "vesa"
[   324.444] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   324.444] (II) Module vesa: vendor="X.Org Foundation"
[   324.444]     compiled for 1.18.1, module version = 2.3.4
[   324.444]     Module class: X.Org Video Driver
[   324.444]     ABI class: X.Org Video Driver, version 20.0
[   324.444] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   324.445] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   324.445] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   324.445] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   324.445] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   324.445] (II) FBDEV: driver for framebuffer: fbdev
[   324.445] (II) VESA: driver for VESA chipsets: vesa
[   324.445] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[   324.445] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[   324.445] (II) intel(0): SNA compiled for use with valgrind
[   324.445] (WW) Falling back to old probe method for modesetting
[   324.445] (WW) Falling back to old probe method for fbdev
[   324.445] (II) Loading sub module "fbdevhw"
[   324.445] (II) LoadModule: "fbdevhw"
[   324.446] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   324.446] (II) Module fbdevhw: vendor="X.Org Foundation"
[   324.446]     compiled for 1.18.3, module version = 0.0.2
[   324.446]     ABI class: X.Org Video Driver, version 20.0
[   324.446] (WW) Falling back to old probe method for vesa
[   324.446] (--) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[   324.446] (--) intel(0): CPU: x86, sse2, sse3, ssse3; using a maximum of 2 threads
[   324.446] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   324.446] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   324.446] (==) intel(0): RGB weight 888
[   324.446] (==) intel(0): Default visual is TrueColor
[   324.447] (II) intel(0): Output LVDS1 has no monitor section
[   324.447] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[   324.447] (II) intel(0): Enabled output LVDS1
[   324.447] (II) intel(0): Output VGA1 has no monitor section
[   324.447] (II) intel(0): Enabled output VGA1
[   324.447] (II) intel(0): Output DVI1 has no monitor section
[   324.447] (II) intel(0): Enabled output DVI1
[   324.447] (II) intel(0): Output TV1 has no monitor section
[   324.447] (II) intel(0): Enabled output TV1
[   324.447] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[   324.447] (II) intel(0): Output VIRTUAL1 has no monitor section
[   324.447] (II) intel(0): Enabled output VIRTUAL1
[   324.447] (--) intel(0): Output LVDS1 using initial mode 1280x800 on pipe 1
[   324.448] (==) intel(0): TearFree disabled
[   324.448] (==) intel(0): DPI set to (96, 96)
[   324.448] (II) Loading sub module "dri2"
[   324.448] (II) LoadModule: "dri2"
[   324.448] (II) Module "dri2" already built-in
[   324.448] (II) Loading sub module "present"
[   324.448] (II) LoadModule: "present"
[   324.448] (II) Module "present" already built-in
[   324.448] (II) UnloadModule: "modesetting"
[   324.448] (II) Unloading modesetting
[   324.448] (II) UnloadModule: "fbdev"
[   324.448] (II) Unloading fbdev
[   324.448] (II) UnloadSubModule: "fbdevhw"
[   324.448] (II) Unloading fbdevhw
[   324.448] (II) UnloadModule: "vesa"
[   324.448] (II) Unloading vesa
[   324.448] (==) Depth 24 pixmap format is 32 bpp
[   324.448] (II) intel(0): SNA initialized with Alviso (gen3) backend
[   324.448] (==) intel(0): Backing store enabled
[   324.448] (==) intel(0): Silken mouse enabled
[   324.448] (II) intel(0): HW Cursor enabled
[   324.448] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   324.449] (==) intel(0): DPMS enabled
[   324.449] (==) intel(0): Display hotplug detection enabled
[   324.449] (II) intel(0): [XvMC] i915_xvmc driver initialized.
[   324.449] (II) intel(0): [DRI2] Setup complete
[   324.449] (II) intel(0): [DRI2]   DRI driver: i915
[   324.449] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[   324.449] (II) intel(0): direct rendering: DRI2 enabled
[   324.449] (II) intel(0): hardware support for Present enabled
[   324.449] (--) RandR disabled
[   324.462] (II) SELinux: Disabled on system
[   324.476] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[   324.476] (II) intel(0): Setting screen physical size to 338 x 211
[   324.539] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   324.539] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   324.539] (II) LoadModule: "evdev"
[   324.539] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   324.540] (II) Module evdev: vendor="X.Org Foundation"
[   324.540]     compiled for 1.18.1, module version = 2.10.1
[   324.540]     Module class: X.Org XInput Driver
[   324.540]     ABI class: X.Org XInput driver, version 22.1
[   324.540] (II) Using input driver 'evdev' for 'Power Button'
[   324.540] (**) Power Button: always reports core events
[   324.540] (**) evdev: Power Button: Device: "/dev/input/event3"
[   324.540] (--) evdev: Power Button: Vendor 0 Product 0x1
[   324.540] (--) evdev: Power Button: Found keys
[   324.540] (II) evdev: Power Button: Configuring as keyboard
[   324.540] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   324.540] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   324.540] (**) Option "xkb_rules" "evdev"
[   324.540] (**) Option "xkb_model" "pc105"
[   324.540] (**) Option "xkb_layout" "fi"
[   324.571] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[   324.571] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   324.571] (II) Using input driver 'evdev' for 'Video Bus'
[   324.571] (**) Video Bus: always reports core events
[   324.571] (**) evdev: Video Bus: Device: "/dev/input/event6"
[   324.571] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   324.571] (--) evdev: Video Bus: Found keys
[   324.571] (II) evdev: Video Bus: Configuring as keyboard
[   324.571] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event6"
[   324.571] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   324.571] (**) Option "xkb_rules" "evdev"
[   324.571] (**) Option "xkb_model" "pc105"
[   324.571] (**) Option "xkb_layout" "fi"
[   324.572] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   324.572] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   324.572] (II) Using input driver 'evdev' for 'Power Button'
[   324.572] (**) Power Button: always reports core events
[   324.572] (**) evdev: Power Button: Device: "/dev/input/event0"
[   324.572] (--) evdev: Power Button: Vendor 0 Product 0x1
[   324.573] (--) evdev: Power Button: Found keys
[   324.573] (II) evdev: Power Button: Configuring as keyboard
[   324.573] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   324.573] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   324.573] (**) Option "xkb_rules" "evdev"
[   324.573] (**) Option "xkb_model" "pc105"
[   324.573] (**) Option "xkb_layout" "fi"
[   324.574] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[   324.574] (II) No input driver specified, ignoring this device.
[   324.574] (II) This device may have been added with another device file.
[   324.574] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   324.574] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   324.574] (II) Using input driver 'evdev' for 'Sleep Button'
[   324.575] (**) Sleep Button: always reports core events
[   324.575] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   324.575] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   324.575] (--) evdev: Sleep Button: Found keys
[   324.575] (II) evdev: Sleep Button: Configuring as keyboard
[   324.575] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[   324.575] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   324.575] (**) Option "xkb_rules" "evdev"
[   324.575] (**) Option "xkb_model" "pc105"
[   324.575] (**) Option "xkb_layout" "fi"
[   324.576] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[   324.576] (II) No input driver specified, ignoring this device.
[   324.576] (II) This device may have been added with another device file.
[   324.577] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   324.577] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   324.577] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   324.577] (**) AT Translated Set 2 keyboard: always reports core events
[   324.577] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   324.577] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   324.577] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   324.577] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   324.577] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   324.577] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[   324.577] (**) Option "xkb_rules" "evdev"
[   324.577] (**) Option "xkb_model" "pc105"
[   324.577] (**) Option "xkb_layout" "fi"
[   324.578] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   324.579] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   324.579] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   324.579] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   324.579] (II) LoadModule: "synaptics"
[   324.579] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   324.579] (II) Module synaptics: vendor="X.Org Foundation"
[   324.579]     compiled for 1.18.1, module version = 1.8.2
[   324.579]     Module class: X.Org XInput Driver
[   324.579]     ABI class: X.Org XInput driver, version 22.1
[   324.579] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   324.579] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   324.579] (**) Option "Device" "/dev/input/event5"
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 63)
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 109)
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   324.624] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   324.624] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   324.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[   324.648] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[   324.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   324.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   324.648] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[   324.648] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   324.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   324.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   324.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   324.649] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   324.650] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   324.650] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   324.974] (II) UnloadModule: "synaptics"
[   324.974] (II) evdev: AT Translated Set 2 keyboard: Close
[   324.974] (II) UnloadModule: "evdev"
[   324.974] (II) evdev: Sleep Button: Close
[   324.974] (II) UnloadModule: "evdev"
[   324.974] (II) evdev: Power Button: Close
[   324.974] (II) UnloadModule: "evdev"
[   324.974] (II) evdev: Video Bus: Close
[   324.974] (II) UnloadModule: "evdev"
[   324.974] (II) evdev: Power Button: Close
[   324.974] (II) UnloadModule: "evdev"
[   325.747] (II) Server terminated successfully (0). Closing log file.
```
so it just seems to start the server, and shut it down again.
no errors, although i can see a few warnings that might be relevant, even graphics related.

```
cat ~/.xsession-errors
openConnection: connect: Tiedostoa tai hakemistoa ei ole
cannot connect to brltty at :0
Script for none started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: upstart-event-bridge main prosessi (1871) lopetti tilakoodilla 1
init: upstart-event-bridge main prosessi päättyi, uudelleenkäynnistetään
init: upstart-dbus-session-bridge main prosessi (1897) lopetti tilakoodilla 1
init: upstart-dbus-session-bridge main prosessi päättyi, uudelleenkäynnistetään
init: upstart-dbus-system-bridge main prosessi (1899) lopetti tilakoodilla 1
init: upstart-dbus-system-bridge main prosessi päättyi, uudelleenkäynnistetään
init: upstart-file-bridge main prosessi (1901) lopetti tilakoodilla 1
init: upstart-file-bridge main prosessi päättyi, uudelleenkäynnistetään
Xsession: X session started for niina at pe 23.9.2016 19.26.56 +0300
localuser:niina being added to access control list
openConnection: connect: Tiedostoa tai hakemistoa ei ole
cannot connect to brltty at :0
xfce4-session-Message: SSH authentication agent is already running
gpg-agent[2220]: WARNING: "--write-env-file" is an obsolete option - it has no effect
gpg-agent[2220]: directory '/home/niina/.gnupg' created
gpg-agent[2220]: directory '/home/niina/.gnupg/private-keys-v1.d' created
gpg-agent[2221]: gpg-agent (GnuPG) 2.1.11 started

(x-session-manager:2048): xfce4-session-WARNING **: gpg-agent returned no PID in the variables

(x-session-manager:2048): xfce4-session-WARNING **: xfsm_manager_load_session: Something wrong with /home/niina/.cache/sessions/xfce4-session-thinkpad:0, Does it exist? Permissions issue?

(x-session-manager:2048): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': Tiedostoa tai hakemistoa ei ole

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Couldn't open libGL.so.1: libGL.so.1: jaettua objektitiedostoa ei voi avata: Tiedostoa tai hakemistoa ei ole
Couldn't open libGL.so.1: libGL.so.1: jaettua objektitiedostoa ei voi avata: Tiedostoa tai hakemistoa ei ole
initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upstart instance.
Couldn't open libGL.so.1: libGL.so.1: jaettua objektitiedostoa ei voi avata: Tiedostoa tai hakemistoa ei ole
Couldn't open libGL.so.1: libGL.so.1: jaettua objektitiedostoa ei voi avata: Tiedostoa tai hakemistoa ei ole
Unable to update the static FcBlanks: 0x0600
Unable to update the static FcBlanks: 0x0601
Unable to update the static FcBlanks: 0x0602
Unable to update the static FcBlanks: 0x0603
Unable to update the static FcBlanks: 0x06dd
Unable to update the static FcBlanks: 0x070f
Unable to update the static FcBlanks: 0x2028
Unable to update the static FcBlanks: 0x2029
Unable to update the static FcBlanks: 0xfff9
Unable to update the static FcBlanks: 0xfffa
Unable to update the static FcBlanks: 0xfffb
Unable to update the static FcBlanks: 0x0600
Unable to update the static FcBlanks: 0x0601
Unable to update the static FcBlanks: 0x0602
Unable to update the static FcBlanks: 0x0603
Unable to update the static FcBlanks: 0x06dd
Unable to update the static FcBlanks: 0x070f
Unable to update the static FcBlanks: 0x2028
Unable to update the static FcBlanks: 0x2029
Unable to update the static FcBlanks: 0xfff9
Unable to update the static FcBlanks: 0xfffa
Unable to update the static FcBlanks: 0xfffb
Couldn't open libGL.so.1: libGL.so.1: cannot open shared object file: No such file or directory
Epäonnistuminen: Moduulin alustus epäonnistui

** (process:2242): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed

** (process:2242): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-i686-linux-gnu/src/volume-control.c: line 1775: uncaught error: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Ei rajapintaa (g-dbus-error-quark, 16)
No window manager registered on screen 0. To start the xfdesktop without this check, run with --disable-wm-check.
Traceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 32, in <module>
    import cupshelpers.installdriver
ImportError: No module named cupshelpers.installdriver
xfce4-panel: No window manager registered on screen 0. To start the panel without this check, run with --disable-wm-check.

(xfce4-panel:2227): xfce4-panel-CRITICAL **: Failed to spawn the xfce4-panel-wrapper: Lapsiprosessin ”/usr/lib/i386-linux-gnu/xfce4/panel/wrapper-2.0” käynnistäminen epäonnistui (Tiedostoa tai hakemistoa ei ole)
Unable to update the static FcBlanks: 0x0600
Unable to update the static FcBlanks: 0x0601
Unable to update the static FcBlanks: 0x0602
Unable to update the static FcBlanks: 0x0603
Unable to update the static FcBlanks: 0x06dd
Unable to update the static FcBlanks: 0x070f
Unable to update the static FcBlanks: 0x2028
Unable to update the static FcBlanks: 0x2029
Unable to update the static FcBlanks: 0xfff9
Unable to update the static FcBlanks: 0xfffa
Unable to update the static FcBlanks: 0xfffb

(wrapper-1.0:2330): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': Tiedostoa tai hakemistoa ei ole

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/22/nodata.png

(wrapper-1.0:2330): weather-WARNING **: No default icon theme? This should not happen, plugin will crash!

(wrapper-1.0:2330): Gtk-CRITICAL **: IA__gtk_misc_set_alignment: assertion 'GTK_IS_MISC (misc)' failed

(wrapper-1.0:2330): Gtk-CRITICAL **: gtk_box_pack: assertion 'GTK_IS_WIDGET (child)' failed

(wrapper-1.0:2330): Gtk-CRITICAL **: IA__gtk_misc_set_alignment: assertion 'GTK_IS_MISC (misc)' failed

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/22/nodata.png

(wrapper-1.0:2330): Gtk-CRITICAL **: IA__gtk_image_set_from_pixbuf: assertion 'GTK_IS_IMAGE (image)' failed

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/128/nodata.png

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/22/nodata.png

(wrapper-1.0:2330): Gtk-CRITICAL **: IA__gtk_image_set_from_pixbuf: assertion 'GTK_IS_IMAGE (image)' failed

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/128/nodata.png

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/22/nodata.png

(wrapper-1.0:2330): Gtk-CRITICAL **: IA__gtk_image_set_from_pixbuf: assertion 'GTK_IS_IMAGE (image)' failed

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/128/nodata.png

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/22/nodata.png

(wrapper-1.0:2330): Gtk-CRITICAL **: IA__gtk_image_set_from_pixbuf: assertion 'GTK_IS_IMAGE (image)' failed

(wrapper-1.0:2330): weather-WARNING **: Failed to open fallback icon from standard theme: /usr/share/xfce4/weather/icons/liquid/128/nodata.png
Unable to update the static FcBlanks: 0x0600
Unable to update the static FcBlanks: 0x0601
Unable to update the static FcBlanks: 0x0602
Unable to update the static FcBlanks: 0x0603
Unable to update the static FcBlanks: 0x06dd
Unable to update the static FcBlanks: 0x070f
Unable to update the static FcBlanks: 0x2028
Unable to update the static FcBlanks: 0x2029
Unable to update the static FcBlanks: 0xfff9
Unable to update the static FcBlanks: 0xfffa
Unable to update the static FcBlanks: 0xfffb

(gst-plugin-scanner:2280): GStreamer-WARNING **: Failed to load plugin '/usr/lib/i386-linux-gnu/gstreamer-1.0/libgstgtksink.so': libGL.so.1: cannot open shared object file: No such file or directory

(gst-plugin-scanner:2280): GStreamer-WARNING **: Failed to load plugin '/usr/lib/i386-linux-gnu/gstreamer-1.0/libgstopengl.so': libGL.so.1: cannot open shared object file: No such file or directory

(gst-plugin-scanner:2280): GStreamer-WARNING **: Failed to load plugin '/usr/lib/i386-linux-gnu/gstreamer-1.0/libgstlibav.so': libGL.so.1: cannot open shared object file: No such file or directory

(gst-plugin-scanner:2280): GStreamer-WARNING **: Failed to load plugin '/usr/lib/i386-linux-gnu/gstreamer-1.0/libgstopencv.so': libGL.so.1: cannot open shared object file: No such file or directory

(xfdesktop:2231): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': Tiedostoa tai hakemistoa ei ole

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Unable to update the static FcBlanks: 0x0600
Unable to update the static FcBlanks: 0x0601
Unable to update the static FcBlanks: 0x0602
Unable to update the static FcBlanks: 0x0603
Unable to update the static FcBlanks: 0x06dd
Unable to update the static FcBlanks: 0x070f
Unable to update the static FcBlanks: 0x2028
Unable to update the static FcBlanks: 0x2029
Unable to update the static FcBlanks: 0xfff9
Unable to update the static FcBlanks: 0xfffa
Unable to update the static FcBlanks: 0xfffb
xfsettingsd: No window manager registered on screen 0.

(xfsettingsd:2232): xfsettingsd-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
gpg-agent[2221]: SIGTERM received - shutting down ...
gpg-agent[2221]: gpg-agent (GnuPG) 2.1.11 stopped

(xfwm4:2223): Gtk-CRITICAL **: IA__gtk_main_quit: assertion 'main_loops != NULL' failed
xfwm4: Fatal IO error 2 (Tiedostoa tai hakemistoa ei ole) on X server :0.0.
xfdesktop: Fatal IO error 2 (Tiedostoa tai hakemistoa ei ole) on X server :0.0.
```
i have tried to execute "gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache" both with and without sudo, but all iget is "gdk-pixbuf-query-loaders is currently not installed..."

what now?

---

### Post by denter2 on 2016-09-24
i am still having the problem.
additionally, i cannot un/install anything because i can't figure out how to connect to the internet, either wireless or wired.
maybe something got messed up there, too?

i removed the xubuntu tag from the title since i do not believe this to be xubuntu specific.

---

### Post by denter2 on 2016-09-24
there seems to have been some sort of interrupted update.
maybe she tried to do the upgrade on battery power.

```
apt-get update
```
recommended to run
```
dpkg --configure -a
```
this took a loooong time.
after that i ran
```
apt-get upgrade
apt-get dist-upgrade
```and probably also```
apt-get -f install
```at some point.

there was 1 package in a "very bad and inconsistent state" - reinstalling it with```
apt-get --reinstall install <package>
```was sufficient.

i rebooted, rinsed & repeated, had to update the flashplugin, and did```
apt-get autoremove
```

everything seems to be ok.

I have now disabled the "New Ubuntu version" notification.

---

