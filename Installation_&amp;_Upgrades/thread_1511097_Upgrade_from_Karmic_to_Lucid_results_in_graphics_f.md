---
title: "Upgrade from Karmic to Lucid results in graphics failing"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by jmc200 on 2010-06-16
Hi all,

I have an m9765uk PC from HP, which contains a GT220 graphics card. So I recently upgraded to Lucid and now the graphics driver fails to load, and I have to run in low-graphics mode. This had happened before in Karmic, and was fixed by simply reinstalling the graphics driver (195.36). However, that no longer works. The error is visible at the bottom of the Xorg log as follows. Any help would be seriously appreciated - I have been using Ubuntu for about a year and a half, and absolutely love it, but it becomes hard to advocate it when I can't even use it! ;)



Xorg.0.log:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux jonathan09 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64
Kernel command line: root=UUID=f92a6803-7adb-4282-9215-5dbcf8e5a3e9 ro quiet splash vmalloc=192M
Build Date: 09 June 2010  11:00:55AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 16 16:27:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:4:0:0) 14f1:8880:1461:e139 Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 rev 4, Mem @ 0xf9c00000/2097152
(--) PCI:*(0:7:0:0) 10de:0a20:1462:1910 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT"
(**) NVIDIA(0): Option "MetaModes" "1920x1080 +0+0"
(**) Jun 16 16:27:04 NVIDIA(0): Enabling RENDER acceleration
(**) Jun 16 16:27:04 NVIDIA(0): ConnectedMonitor string: "CRT"
(II) Jun 16 16:27:04 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 16 16:27:04 NVIDIA(0):     enabled.
(EE) Jun 16 16:27:04 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:7:0:0.
(EE) Jun 16 16:27:04 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Jun 16 16:27:04 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jun 16 16:27:04 NVIDIA(0):     README for additional information.
(EE) Jun 16 16:27:04 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found



Xorg.conf:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    Identifier "Monitor0"
    VendorName "Unknown"
    ModelName "Samsung SyncMaster"
    HorizSync 30.0 - 81.0
    VertRefresh 56.0 - 60.0
    Option "DPMS"
EndSection

Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce GT 220"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option "metamodes" "1920x1080 +0+0"
    Option         "ConnectedMonitor" "CRT"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by kansasnoob on 2010-06-16
Not sure if this will help but:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

> Incompatibility with nVidia upstream driver installer

Ubuntu 10.04 LTS includes improved integration for nVidia binary driver packages. Unfortunately, this comes at the expense of compatibility with the installer provided upstream on the nVidia website. Users who wish to use the nVidia binary video drivers with 10.04 LTS should install them using the Ubuntu packages, as made available under System -> Administration -> Hardware Drivers. 

---

### Post by jmc200 on 2010-06-16
Thanks for your response. I couldn't get the synaptic's drivers to work - I guess I'm going to have to reinstall Karmic then.

---

### Post by joncrndl on 2010-06-16
Check out the release notes for Lucid.  I stumbled onto this same problem when trying to install ANYTHING based on the Ubuntu 10.04.  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by  default on most common video chipsets.  While this is a major step  forward for the graphics architecture in Ubuntu, in some rare cases KMS ** will prevent your video output from working correctly, or from working  at all.**  If you need to disable KMS, you can do so by booting with the nomodeset  option.  You can also save this setting so that it's applied at every  boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset  to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset  to the line beginning with # kopt=, then run sudo update-grub).  ([533784]("https://bugs.launchpad.net/bugs/533784"), [541501]("https://bugs.launchpad.net/bugs/541501")) 

I can attest that this new feature KMS does keep the video from working until  the "nomodeset" option is added to the boot.

---

### Post by jmc200 on 2010-06-17
Thanks, but I'm afraid that didn't solve the problem. I get exactly the same log messages.

---

