---
title: "Installing recent Ubuntus results in Screen(s) found, but none have a usable configur"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by h1ppo on 2012-05-31
Hi guys,

I've been having this problem for about a week now and has affected me when trying to install the following x64 distros

[LIST]Linux Mint 13 (cinnamon and mate editions)[/LIST]
[LIST]Ubuntu 12.04[/LIST]
[LIST]Ubuntu 11.10[/LIST]


I initially had Linux Mint 11 installed and wanted to upgrade to 13 but wasn't event able to get the Live CD because of the problem I'm about to describe. I did a package upgrade instead and technically it worked but there were a few parts which were not quite right and felt a clean install would be preferential and I wasn't entirely happy with the long boot time so tried Ubuntu 12.04.

The Live CD didn't work for Pangolin either but the install menu did work so I installed away but after install I was greeted with a terminal login and there appeared to be an error with the screen initialisation.

I am running this on a MacbookPro 6,2 which has the dual graphics card of Intel and Nvidia (troublesome right...).

I've tried quite a varied range of fixes I'd seen on posts regarding the same error message but so far I've not really made any progress. 

I'm a bit of a novice with Linux still but here are the typical bits of debug I see helpers ask for:

Xorg.0.log
```
[    27.341] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    27.341] X Protocol Version 11, Revision 0
[    27.341] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    27.341] Current Operating System: Linux jason-MacBookPro 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
[    27.341] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=14a81bd4-228d-4ea0-be9b-46c5ab470a31 ro nomodeset quiet splash vt.handoff=7
[    27.341] Build Date: 05 April 2012  04:32:37AM
[    27.341] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[    27.341] Current version of pixman: 0.24.4
[    27.341] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    27.341] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.341] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 31 10:59:13 2012
[    27.368] (==) Using config file: "/etc/X11/xorg.conf"
[    27.368] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.392] (==) No Layout section.  Using the first Screen section.
[    27.392] (==) No screen section available. Using defaults.
[    27.392] (**) |-->Screen "Default Screen Section" (0)
[    27.392] (**) |   |-->Monitor "<default monitor>"
[    27.402] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    27.402] (**) |   |-->Device "Default Device"
[    27.402] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    27.402] (==) Automatically adding devices
[    27.402] (==) Automatically enabling devices
[    27.432] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.432] 	Entry deleted from font path.
[    27.432] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.432] 	Entry deleted from font path.
[    27.432] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.432] 	Entry deleted from font path.
[    27.432] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.432] 	Entry deleted from font path.
[    27.432] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.432] 	Entry deleted from font path.
[    27.432] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    27.432] 	Entry deleted from font path.
[    27.432] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    27.432] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.432] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.432] (II) Loader magic: 0x7fd91c936b00
[    27.432] (II) Module ABI versions:
[    27.432] 	X.Org ANSI C Emulation: 0.4
[    27.432] 	X.Org Video Driver: 11.0
[    27.432] 	X.Org XInput driver : 16.0
[    27.433] 	X.Org Server Extension : 6.0
[    27.434] (--) PCI:*(0:0:2:0) 8086:0046:0000:0000 rev 24, Mem @ 0xc1400000/4194304, 0xb0000000/268435456, I/O @ 0x00003130/8
[    27.434] (--) PCI: (0:1:0:0) 10de:0a29:106b:00c7 rev 162, Mem @ 0xc0000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    27.434] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.434] (II) LoadModule: "extmod"
[    27.499] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.508] (II) Module extmod: vendor="X.Org Foundation"
[    27.508] 	compiled for 1.11.3, module version = 1.0.0
[    27.508] 	Module class: X.Org Server Extension
[    27.508] 	ABI class: X.Org Server Extension, version 6.0
[    27.508] (II) Loading extension MIT-SCREEN-SAVER
[    27.508] (II) Loading extension XFree86-VidModeExtension
[    27.508] (II) Loading extension XFree86-DGA
[    27.508] (II) Loading extension DPMS
[    27.508] (II) Loading extension XVideo
[    27.508] (II) Loading extension XVideo-MotionCompensation
[    27.508] (II) Loading extension X-Resource
[    27.508] (II) LoadModule: "dbe"
[    27.509] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.509] (II) Module dbe: vendor="X.Org Foundation"
[    27.509] 	compiled for 1.11.3, module version = 1.0.0
[    27.509] 	Module class: X.Org Server Extension
[    27.509] 	ABI class: X.Org Server Extension, version 6.0
[    27.509] (II) Loading extension DOUBLE-BUFFER
[    27.509] (II) LoadModule: "glx"
[    27.509] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    28.782] (II) Module glx: vendor="NVIDIA Corporation"
[    28.803] 	compiled for 4.0.2, module version = 1.0.0
[    28.803] 	Module class: X.Org Server Extension
[    28.803] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    28.803] (II) Loading extension GLX
[    28.803] (II) LoadModule: "record"
[    28.803] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.963] (II) Module record: vendor="X.Org Foundation"
[    28.963] 	compiled for 1.11.3, module version = 1.13.0
[    28.963] 	Module class: X.Org Server Extension
[    28.963] 	ABI class: X.Org Server Extension, version 6.0
[    28.963] (II) Loading extension RECORD
[    28.963] (II) LoadModule: "dri"
[    28.963] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.976] (II) Module dri: vendor="X.Org Foundation"
[    28.976] 	compiled for 1.11.3, module version = 1.0.0
[    28.976] 	ABI class: X.Org Server Extension, version 6.0
[    28.976] (II) Loading extension XFree86-DRI
[    28.976] (II) LoadModule: "dri2"
[    28.976] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.977] (II) Module dri2: vendor="X.Org Foundation"
[    28.977] 	compiled for 1.11.3, module version = 1.2.0
[    28.977] 	ABI class: X.Org Server Extension, version 6.0
[    28.977] (II) Loading extension DRI2
[    28.977] (==) Matched intel as autoconfigured driver 0
[    28.977] (==) Matched vesa as autoconfigured driver 1
[    28.977] (==) Matched fbdev as autoconfigured driver 2
[    28.977] (==) Assigned the driver to the xf86ConfigLayout
[    28.977] (II) LoadModule: "intel"
[    28.990] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.005] (II) Module intel: vendor="X.Org Foundation"
[    29.005] 	compiled for 1.11.3, module version = 2.17.0
[    29.005] 	Module class: X.Org Video Driver
[    29.005] 	ABI class: X.Org Video Driver, version 11.0
[    29.005] (II) LoadModule: "vesa"
[    29.006] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.013] (II) Module vesa: vendor="X.Org Foundation"
[    29.013] 	compiled for 1.11.3, module version = 2.3.0
[    29.013] 	Module class: X.Org Video Driver
[    29.013] 	ABI class: X.Org Video Driver, version 11.0
[    29.013] (II) LoadModule: "fbdev"
[    29.014] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.014] (II) Module fbdev: vendor="X.Org Foundation"
[    29.014] 	compiled for 1.11.3, module version = 0.4.2
[    29.014] 	ABI class: X.Org Video Driver, version 11.0
[    29.014] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    29.020] (II) VESA: driver for VESA chipsets: vesa
[    29.020] (II) FBDEV: driver for framebuffer: fbdev
[    29.021] (++) using VT number 7

[    29.022] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.022] (WW) Falling back to old probe method for fbdev
[    29.023] (II) Loading sub module "fbdevhw"
[    29.023] (II) LoadModule: "fbdevhw"
[    29.023] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.044] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.044] 	compiled for 1.11.3, module version = 0.0.2
[    29.044] 	ABI class: X.Org Video Driver, version 11.0
[    29.044] (II) Loading sub module "vbe"
[    29.044] (II) LoadModule: "vbe"
[    29.044] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.049] (II) Module vbe: vendor="X.Org Foundation"
[    29.049] 	compiled for 1.11.3, module version = 1.1.0
[    29.049] 	ABI class: X.Org Video Driver, version 11.0
[    29.049] (II) Loading sub module "int10"
[    29.049] (II) LoadModule: "int10"
[    29.049] (II) Loading /usr/lib/xorg/modules/libint10.so
[    29.051] (II) Module int10: vendor="X.Org Foundation"
[    29.051] 	compiled for 1.11.3, module version = 1.0.0
[    29.051] 	ABI class: X.Org Video Driver, version 11.0
[    29.051] (II) VESA(0): initializing int10
[    29.051] (EE) VESA(0): V_BIOS address 0xd00 out of range
[    29.051] (II) UnloadModule: "vesa"
[    29.051] (II) Unloading vesa
[    29.051] (II) UnloadModule: "int10"
[    29.051] (II) Unloading int10
[    29.051] (II) UnloadModule: "vbe"
[    29.051] (II) Unloading vbe
[    29.051] (EE) Screen(s) found, but none have a usable configuration.
[    29.051] 
Fatal server error:
[    29.051] no screens found
[    29.051] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    29.051] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    29.051] 
[    29.060]  ddxSigGiveUp: Closing log
[    29.060] Server terminated with error (1). Closing log file.
```

xorg.conf (default one)
```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 330M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 08)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

I also tried to remove the default xorg.conf and recreate it with nvidia-xconfig which produced this config:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Thu Apr  5 22:40:54 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

However, doing startx after this results in the system hanging with the last message being
```
saned; edit /etc/default/saned [OK]
```
I don't think that will help debug why it hang unfortunately but not sure which log I can look at after a reset to get that information...

Thanks in advance for any help you can give me guys, would hate to resort to developing back in OSX again :P Any other information you need let me know and I'll get it on here asap.

thanks again.

---

### Post by h1ppo on 2012-06-01
I've not managed to get this working (partially but enough to close this thread).

I ended up blacklisting and uninstalling packages relating to nouveau (apt-cache search nouveau) and just take out anything with nouveau in it.

Now to try and get unity to actually use my nvidia card :)

---

