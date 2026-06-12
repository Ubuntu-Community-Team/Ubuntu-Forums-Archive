---
title: "Help configuring Xorg for 3 monitors"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by ChurruKa on 2012-10-23
Hi, I've been trying to configure X for 3 displays on a fresh Kubuntu install for the last couple of days to no sucess. I tried a lot of different changes to the config files and different changes on files on /usr/share/X11/xorg.conf.d/, and now I'm out of ideas. I have two Radeon cards, one integrated on the motherboard and a PCIe. The external one (X300SE) has a monitor plugged on the DVI port, and the internal (X1200) has two more (one the VGA and another on the DVI). Currently X only shows on the "main" card (the X300SE, used by the BIOS for the POST messages, the "primary adapter" :P), and the login screen looks "weird" (a "big" background filling the screen and a "smaller" login screen on top with the same background on top (I'll upload a screenshot if necessary)), but after login the desktop looks OK. The other two screens remain on powersaving mode (i.e. power led on, screen off).

Relevant config files and system info:

```

root@brainstorm:~# uname -a && lsb_release --release
Linux brainstorm 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Release:        12.10

```
```

root@brainstorm:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Display controller: Advanced Micro Devices [AMD] nee ATI RS690 [Radeon X1200 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV370 5B60 [Radeon X300 (PCIE)]
02:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV370 [Radeon X300SE]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
04:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
04:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

```
```

root@brainstorm:~# lsmod|grep ati   #no modules named "ati"
pata_atiixp            13204  0 
root@brainstorm:~# lsmod|grep radeon
radeon                895653  2 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon
root@brainstorm:~# 


```
```

root@brainstorm:~# aptitude search ati ; aptitude search radeon
p   atitvout:i386                                  - ATI TV Out Support Program                    
i   xserver-xorg-video-ati                  - X.Org X server -- AMD/ATI display driver wrapp
p   xserver-xorg-video-ati:i386        - X.Org X server -- AMD/ATI display driver wrapp
p   xserver-xorg-video-ati-dbg          - Servidor X de X.Org - envoltura de los control
p   xserver-xorg-video-ati-dbg:i386        - Servidor X de X.Org - envoltura de los control
i   libdrm-radeon1                                           - Interfaz en espacio de usuario a los servicios
p   libdrm-radeon1:i386                               - Interfaz en espacio de usuario a los servicios
p   libdrm-radeon1-dbg                               - Interfaz en espacio de usuario a los servicios
p   libdrm-radeon1-dbg:i386                     - Interfaz en espacio de usuario a los servicios
i   radeontool                                                   - Utilidad para controlar las funciones de retro
p   radeontool:i386                                      - Utilidad para controlar las funciones de retro
i   xserver-xorg-video-radeon                  - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-radeon:i386      - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg       - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg:i386  - X.Org X server -- AMD/ATI Radeon display drive
(-- I've removed non-relevant packages from the output --)
root@brainstorm:~# aptitude search xserver-xorg
i   xserver-xorg                        - X.Org X server                                
p   xserver-xorg:i386                   - X.Org X server                                
i   xserver-xorg-core                   - Xorg X server - core server                   
p   xserver-xorg-core:i386              - Xorg X server - core server                   
p   xserver-xorg-core-dbg               - Xorg - servidor X de X.Org (símbolos de depura
p   xserver-xorg-core-dbg:i386          - Xorg - servidor X de X.Org (símbolos de depura
p   xserver-xorg-dev                    - Xorg X server - development files             
p   xserver-xorg-dev:i386               - Xorg X server - development files             
 i   xserver-xorg-input-all              - X.Org X server -- input driver metapackage    
i   xserver-xorg-input-evdev            - X.Org X server -- evdev input driver          
p   xserver-xorg-input-evdev:i386       - X.Org X server -- evdev input driver          
p   xserver-xorg-input-evdev-dbg        - X.Org X server -- evdev input driver (developm
p   xserver-xorg-input-evdev-dbg:i386   - X.Org X server -- evdev input driver (developm
p   xserver-xorg-input-evdev-dev        - X.Org X server -- evdev input driver (developm
i   xserver-xorg-input-mouse            - X.Org X server -- mouse input driver          
i   xserver-xorg-input-synaptics        - Synaptics TouchPad driver for X.Org server    
i   xserver-xorg-input-vmmouse          - X.Org X server -- VMMouse input driver to use 
i   xserver-xorg-input-wacom            - Servidor X de X.Org -- controlador de entrada 
v   xserver-xorg-video-                 -                                               
v   xserver-xorg-video-:i386            -                                               
i   xserver-xorg-video-all              - X.Org X server -- output driver metapackage   
p   xserver-xorg-video-all:i386         - X.Org X server -- output driver metapackage   
v   xserver-xorg-video-amd:i386         -                                               
i   xserver-xorg-video-ati              - X.Org X server -- AMD/ATI display driver wrapp
p   xserver-xorg-video-ati:i386         - X.Org X server -- AMD/ATI display driver wrapp
p   xserver-xorg-video-ati-dbg          - Servidor X de X.Org - envoltura de los control
p   xserver-xorg-video-ati-dbg:i386     - Servidor X de X.Org - envoltura de los control
i   xserver-xorg-video-cirrus           - X.Org X server -- Cirrus display driver       
p   xserver-xorg-video-cirrus:i386      - X.Org X server -- Cirrus display driver           
i   xserver-xorg-video-fbdev            - X.Org X server -- fbdev display driver        
p   xserver-xorg-video-fbdev:i386       - X.Org X server -- fbdev display driver        
p   xserver-xorg-video-geode:i386       - X.Org X server -- Geode GX2/LX display driver 
p   xserver-xorg-video-geode-dbg:i386   - Controlador de pantalla Geode GX2/LX (símbolos
i   xserver-xorg-video-intel            - X.Org X server -- Intel i8xx, i9xx display dri
p   xserver-xorg-video-intel:i386       - X.Org X server -- Intel i8xx, i9xx display dri
p   xserver-xorg-video-intel-dbg        - Servidor X de X.Org -- controlador de vídeo In
p   xserver-xorg-video-intel-dbg:i386   - Servidor X de X.Org -- controlador de vídeo In
i   xserver-xorg-video-mach64           - X.Org X server -- ATI Mach64 display driver   
p   xserver-xorg-video-mach64:i386      - X.Org X server -- ATI Mach64 display driver   
p   xserver-xorg-video-mach64-dbg       - Servidor de X de X.Org -- controlador de panta
p   xserver-xorg-video-mach64-dbg:i386  - Servidor de X de X.Org -- controlador de panta
i   xserver-xorg-video-mga              - X.Org X server -- MGA display driver          
p   xserver-xorg-video-mga:i386         - X.Org X server -- MGA display driver          
i   xserver-xorg-video-modesetting      - X.Org X server -- Generic modesetting driver  
p   xserver-xorg-video-modesetting:i386 - X.Org X server -- Generic modesetting driver  
p   xserver-xorg-video-modesetting-dbg  - X.Org X server -- Generic modesetting driver (
p   xserver-xorg-video-modesetting-dbg: - X.Org X server -- Generic modesetting driver (
i   xserver-xorg-video-neomagic         - X.Org X server -- Neomagic display driver     
p   xserver-xorg-video-neomagic:i386    - X.Org X server -- Neomagic display driver     
i   xserver-xorg-video-nouveau          - X.Org X server -- Nouveau display driver      
p   xserver-xorg-video-nouveau:i386     - X.Org X server -- Nouveau display driver      
p   xserver-xorg-video-nouveau-dbg      - X.Org X server -- Nouveau display driver (debu
p   xserver-xorg-video-nouveau-dbg:i386 - X.Org X server -- Nouveau display driver (debu
i   xserver-xorg-video-r128             - X.Org X server -- ATI r128 display driver     
p   xserver-xorg-video-r128:i386        - X.Org X server -- ATI r128 display driver     
p   xserver-xorg-video-r128-dbg         - Servidor X de X.Org -- controlador de pantalla
p   xserver-xorg-video-r128-dbg:i386    - Servidor X de X.Org -- controlador de pantalla
i   xserver-xorg-video-radeon           - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-radeon:i386      - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg       - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg:i386  - X.Org X server -- AMD/ATI Radeon display drive
p   xserver-xorg-video-tdfx:i386        - X.Org X server -- tdfx display driver         
i   xserver-xorg-video-vesa             - X.Org X server -- VESA display driver         
p   xserver-xorg-video-vesa:i386        - X.Org X server -- VESA display driver         
  (-- I've removed some non-relevant packages from the output --)

```
```

root@brainstorm:~# aptitude show xserver-xorg
Paquete: xserver-xorg                            
Estado: instalado
Instalado automáticamente: no
Versión: 1:7.7+1ubuntu4
Prioridad: opcional
Sección: x11
Desarrollador: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Arquitectura: amd64
Tamaño sin comprimir: 373 k
Depende de: xserver-xorg-core (>= 2:1.11), xserver-xorg-video-all | xorg-driver-video,
            xserver-xorg-input-all | xorg-driver-input, xserver-xorg-input-evdev, libc6   (>= 2.7), xkb-data (>= 1.4), x11-xkb-utils
Recomienda: libgl1-mesa-dri
Tiene conflictos con: xserver-xorg
Proporciona: xserver
Descripción: X.Org X server
 This package depends on the full suite of the server and drivers for the X.Org X server.  It does not provide the actual server itself.

```
```

root@brainstorm:~# cat /etc/apt/sources.list
# 

# deb cdrom:[Kubuntu 12.10 _Quantal Quetzal_ - Beta amd64 (20121011)]/ quantal main multiverse restricted universe

# deb cdrom:[Kubuntu 12.10 _Quantal Quetzal_ - Beta amd64 (20121011)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://es.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal universe
deb http://es.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://es.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main

```
```

root@brainstorm:~# cat /usr/share/X11/xorg.conf.d/20-radeon.conf 
Section "Device"

        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "True"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"

        Identifier  "Card0"
#        VendorName  "ATI Technologies Inc"
        VendorName  "Advanced Micro Devices [AMD] nee ATI"
        BoardName   "RS690 [Radeon X1200 Series]"
#       BusID "PCI:1:5:0"
#       Driver "radeon"
        Driver "ati"
        Screen 0

        Option "Monitor-VGA-0"  "Monitor1"
        Option "Movnitor-DVI-0" "Monitor2"
EndSection

Section "Device"

        Identifier  "Card1"
        VendorName  "Advanced Micro Devices [AMD] nee ATI"
        BoardName   "RV370 5B60 [Radeon X300SE (PCIE)]"
#       BoardName   "RV370 5B60 [Radeon X300SE]"
        BusID "PCI:2:0:0"
#       Driver "radeon"
        Driver "ati"
        Screen 1

EndSection

Section "Monitor"
        Identifier "Monitor0"
#       Option "Primary" "false"
#       Option "DMPS"
EndSection

Section "Monitor"
        Identifier "Monitor1"
        Option "LeftOf" "Monitor0"
#       Option "Primary" "false"
#       Option "DMPS"
EndSection

Section "Monitor"
        Identifier "Monitor2"
        Option "LeftOf" "Monitor1"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device "Card0"
        Monitor "Monitor0"

        SubSection "Display"
                Viewport 0 0
                Depth 24
                Virtual 2560 2560
        EndSubsection

EndSection

Section "Screen"
        Identifier "Screen1"
        Device "Card1"
        Monitor "Monitor1"

        SubSection "Display"
                Viewport 0 0
                Depth 24
        EndSubsection
EndSection

Section "ServerLayout"
        Identifier "MainLayout"
        Screen 0 "Screen0" 0 0
        Screen 1 "Screen1" LeftOf "Screen0"
EndSection

```
```

root@brainstorm:~# cat /var/log/Xorg.0.log
[    21.079] 
X.Org X Server 1.12.3
Release Date: 2012-07-09
[    21.079] X Protocol Version 11, Revision 0
[    21.079] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    21.079] Current Operating System: Linux brainstorm 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    21.079] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-17-generic root=/dev/mapper/brainstorm-root ro splash vt.handoff=7
[    21.079] Build Date: 21 October 2012  07:08:05PM
[    21.079] xorg-server 3:1.12.3+git20120709~quantal2 (For technical support please see http://www.ubuntu.com/support) 
[    21.079] Current version of pixman: 0.26.0
[    21.079]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    21.079] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.079] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 23 17:10:41 2012
[    21.084] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.098] (==) ServerLayout "MainLayout"
[    21.098] (**) |-->Screen "Screen0" (0)
[    21.098] (**) |   |-->Monitor "Monitor0"
[    21.098] (**) |   |-->Device "Card0"
[    21.098] (**) |-->Screen "Screen1" (1)
[    21.098] (**) |   |-->Monitor "Monitor1"
[    21.099] (**) |   |-->Device "Card1"
[    21.099] (==) Automatically adding devices
[    21.099] (==) Automatically enabling devices
[    21.099] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.099]    Entry deleted from font path.
[    21.099] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.099]    Entry deleted from font path.
[    21.099] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.099]    Entry deleted from font path.
[    21.099] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.099]    Entry deleted from font path.
[    21.099] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.099]    Entry deleted from font path.
[    21.099] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    21.099]    Entry deleted from font path.
[    21.099] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    21.099] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.099] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.099] (II) Loader magic: 0x7fd203895b20
[    21.099] (II) Module ABI versions:
[    21.099]    X.Org ANSI C Emulation: 0.4
[    21.099]    X.Org Video Driver: 12.0
[    21.099]    X.Org XInput driver : 16.0
[    21.099]    X.Org Server Extension : 6.0
[    21.100] (--) PCI: (0:1:5:0) 1002:791e:1043:826d rev 0, Mem @ 0xf8000000/67108864, 0xfdbf0000/65536, 0xfda00000/1048576, I/O @ 0x0000ce00/256
[    21.100] (--) PCI:*(0:2:0:0) 1002:5b60:148c:2089 rev 0, Mem @ 0xf0000000/134217728, 0xfd9f0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    21.100] (--) PCI: (0:2:0:1) 1002:5b70:148c:2088 rev 0, Mem @ 0xfd9e0000/65536
[    21.100] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.100] (II) LoadModule: "extmod"
[    21.170] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.170] (II) Module extmod: vendor="X.Org Foundation"
[    21.170]    compiled for 1.12.3, module version = 1.0.0
[    21.170]    Module class: X.Org Server Extension
[    21.170]    ABI class: X.Org Server Extension, version 6.0
[    21.170] (II) Loading extension MIT-SCREEN-SAVER
[    21.170] (II) Loading extension XFree86-VidModeExtension
[    21.170] (II) Loading extension XFree86-DGA
[    21.170] (II) Loading extension DPMS
[    21.170] (II) Loading extension XVideo
[    21.170] (II) Loading extension XVideo-MotionCompensation
[    21.170] (II) Loading extension X-Resource
[    21.170] (II) LoadModule: "dbe"
[    21.170] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.170] (II) Module dbe: vendor="X.Org Foundation"
[    21.170]    compiled for 1.12.3, module version = 1.0.0
[    21.170]    Module class: X.Org Server Extension
[    21.170]    ABI class: X.Org Server Extension, version 6.0
[    21.170] (II) Loading extension DOUBLE-BUFFER
[    21.170] (II) LoadModule: "glx"
[    21.170] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.170] (II) Module glx: vendor="X.Org Foundation"
[    21.170]    compiled for 1.12.3, module version = 1.0.0
[    21.170]    ABI class: X.Org Server Extension, version 6.0
[    21.170] (==) AIGLX enabled
[    21.170] (II) Loading extension GLX
[    21.171] (II) LoadModule: "record"
[    21.171] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.171] (II) Module record: vendor="X.Org Foundation"
[    21.171]    compiled for 1.12.3, module version = 1.13.0
[    21.171]    Module class: X.Org Server Extension
[    21.171]    ABI class: X.Org Server Extension, version 6.0
[    21.171] (II) Loading extension RECORD
[    21.171] (II) LoadModule: "dri"
[    21.171] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.171] (II) Module dri: vendor="X.Org Foundation"
[    21.171]    compiled for 1.12.3, module version = 1.0.0
[    21.171]    ABI class: X.Org Server Extension, version 6.0
[    21.171] (II) Loading extension XFree86-DRI
[    21.171] (II) LoadModule: "dri2"
[    21.171] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.171] (II) Module dri2: vendor="X.Org Foundation"
[    21.171]    compiled for 1.12.3, module version = 1.2.0
[    21.171]    ABI class: X.Org Server Extension, version 6.0
[    21.171] (II) Loading extension DRI2
[    21.171] (II) LoadModule: "ati"
[    21.172] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.172] (II) Module ati: vendor="X.Org Foundation"
[    21.172]    compiled for 1.12.3, module version = 6.99.99
[    21.172]    Module class: X.Org Video Driver
[    21.172]    ABI class: X.Org Video Driver, version 12.0
[    21.172] (II) LoadModule: "radeon"
[    21.172] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.172] (II) Module radeon: vendor="X.Org Foundation"
[    21.172]    compiled for 1.12.3, module version = 6.99.99
[    21.172]    Module class: X.Org Video Driver
[    21.172]    ABI class: X.Org Video Driver, version 12.0
[    21.172] (II) RADEON: Driver for ATI Radeon chipsets:
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
        TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE
[    21.176] (++) using VT number 7

[    21.176] (II) [KMS] Kernel modesetting enabled.
[    21.176] (II) [KMS] Kernel modesetting enabled.
[    21.176] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    21.176] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.176] (==) RADEON(0): Default visual is TrueColor
[    21.176] (**) RADEON(0): Option "RenderAccel" "True"
[    21.176] (==) RADEON(0): RGB weight 888
[    21.176] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    21.176] (--) RADEON(0): Chipset: "ATI Radeon X300 (RV370) 5B60 (PCIE)" (ChipID = 0x5b60)
[    21.176] drmOpenDevice: node name is /dev/dri/card0
[    21.176] drmOpenDevice: open result is 9, (OK)
[    21.176] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    21.176] drmOpenDevice: node name is /dev/dri/card0
[    21.176] drmOpenDevice: open result is 9, (OK)
[    21.176] drmOpenByBusid: drmOpenMinor returns 9
[    21.176] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    21.176] drmOpenDevice: node name is /dev/dri/card1
[    21.176] drmOpenDevice: open result is 9, (OK)
[    21.176] drmOpenByBusid: drmOpenMinor returns 9
[    21.176] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    21.176] (II) RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
[    21.176] (II) Loading sub module "shadow"
[    21.176] (II) LoadModule: "shadow"
[    21.177] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.177] (II) Module shadow: vendor="X.Org Foundation"
[    21.177]    compiled for 1.12.3, module version = 1.1.0
[    21.177]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.177] (II) RADEON(0): KMS Color Tiling: disabled
[    21.177] (II) RADEON(0): KMS Pageflipping: enabled
[    21.177] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    21.209] (II) RADEON(0): Output VGA-1 using monitor section Monitor0
[    21.284] (II) RADEON(0): EDID for output VGA-1
[    21.284] (II) RADEON(0): Manufacturer: BNQ  Model: 7803  Serial#: 21573
[    21.284] (II) RADEON(0): Year: 2008  Week: 11
[    21.284] (II) RADEON(0): EDID Version: 1.3
[    21.284] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    21.284] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    21.284] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    21.284] (II) RADEON(0): Gamma: 2.20
[    21.284] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    21.284] (II) RADEON(0): Default color space is primary color space
[    21.284] (II) RADEON(0): First detailed timing is preferred mode
[    21.284] (II) RADEON(0): redX: 0.647 redY: 0.340   greenX: 0.288 greenY: 0.605
[    21.284] (II) RADEON(0): blueX: 0.145 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[    21.284] (II) RADEON(0): Supported established timings:
[    21.284] (II) RADEON(0): 720x400@70Hz
[    21.284] (II) RADEON(0): 640x480@60Hz
[    21.284] (II) RADEON(0): 640x480@75Hz
[    21.284] (II) RADEON(0): 800x600@60Hz
[    21.284] (II) RADEON(0): 800x600@75Hz
[    21.284] (II) RADEON(0): 832x624@75Hz
[    21.284] (II) RADEON(0): 1024x768@60Hz
[    21.284] (II) RADEON(0): 1024x768@75Hz
[    21.284] (II) RADEON(0): 1280x1024@75Hz
[    21.284] (II) RADEON(0): 1152x864@75Hz
[    21.284] (II) RADEON(0): Manufacturer's mask: 0
[    21.284] (II) RADEON(0): Supported standard timings:
[    21.284] (II) RADEON(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
[    21.284] (II) RADEON(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    21.284] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    21.284] (II) RADEON(0): Supported detailed timing:
[    21.284] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    21.284] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    21.284] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    21.284] (II) RADEON(0): Serial No: B3808667SL0
[    21.284] (II) RADEON(0): Ranges: V min: 55 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    21.284] (II) RADEON(0): Monitor name: BenQ G900
[    21.284] (II) RADEON(0): EDID (in hex):
[    21.284] (II) RADEON(0):    00ffffffffffff0009d1037845540000
[    21.284] (II) RADEON(0):    0b1201030e261e782ecc25a557499b25
[    21.284] (II) RADEON(0):    115054a56b8071008100814001010101
[    21.284] (II) RADEON(0):    010101010101302a009851002a403070
[    21.284] (II) RADEON(0):    1300782d1100001e000000ff00423338
[    21.284] (II) RADEON(0):    3038363637534c300a20000000fd0037
[    21.284] (II) RADEON(0):    4c1f530e000a202020202020000000fc
[    21.284] (II) RADEON(0):    0042656e5120473930300a0a0a0a00cf
[    21.284] (II) RADEON(0): EDID vendor "BNQ", prod id 30723
[    21.284] (II) RADEON(0): Using EDID range info for horizontal sync
[    21.284] (II) RADEON(0): Using EDID range info for vertical refresh
[    21.284] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.284] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    21.285] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.285] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    21.285] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    21.285] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.285] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    21.285] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    21.285] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    21.285] (II) RADEON(0): Printing probed modes for output VGA-1
[    21.285] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    21.285] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[    21.285] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz e)
[    21.285] (II) RADEON(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz e)
[    21.285] (II) RADEON(0): Modeline "1152x720"x60.0   67.28  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.7 kHz)
[    21.285] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    21.285] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.285] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[    21.285] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    21.285] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    21.285] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    21.285] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.285] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    21.285] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    21.285] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    21.285] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.285] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.285] (II) RADEON(0): Output VGA-1 connected
[    21.285] (II) RADEON(0): Using exact sizes for initial modes
[    21.285] (II) RADEON(0): Output VGA-1 using initial mode 1280x1024
[    21.285] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.285] (II) RADEON(0): mem size init: gart size :1feff000 vram size: s:8000000 visible:7ac0000
[    21.285] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    21.285] (**) RADEON(0): Display dimensions: (380, 300) mm
[    21.285] (**) RADEON(0): DPI set to (171, 216)
[    21.285] (II) Loading sub module "fb"
[    21.285] (II) LoadModule: "fb"
[    21.285] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.285] (II) Module fb: vendor="X.Org Foundation"
[    21.285]    compiled for 1.12.3, module version = 1.0.0
[    21.285]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.285] (II) Loading sub module "ramdac"
[    21.285] (II) LoadModule: "ramdac"
[    21.285] (II) Module "ramdac" already built-in
[    21.285] (==) RADEON(1): Depth 24, (--) framebuffer bpp 32
[    21.285] (II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.286] (==) RADEON(1): Default visual is TrueColor
[    21.286] (==) RADEON(1): RGB weight 888
[    21.286] (II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
[    21.286] (--) RADEON(1): Chipset: "ATI Radeon X300 (RV370) 5B60 (PCIE)" (ChipID = 0x5b60)
[    21.286] (II) RADEON(1):  reusing fd for second head
[    21.286] (II) RADEON(1): GPU accel disabled or not working, using shadowfb for KMS
[    21.286] (II) Loading sub module "shadow"
[    21.286] (II) LoadModule: "shadow"
[    21.286] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.286] (II) Module shadow: vendor="X.Org Foundation"
[    21.286]    compiled for 1.12.3, module version = 1.1.0
[    21.286]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.286] (II) RADEON(1): KMS Color Tiling: disabled
[    21.286] (II) RADEON(1): KMS Pageflipping: enabled
[    21.286] (II) RADEON(1): SwapBuffers wait for vsync: enabled
[    21.340] (II) RADEON(1): Output DVI-0 using monitor section Monitor1
[    21.340] (**) RADEON(1): Option "LeftOf" "Monitor0"
[    21.382] (II) RADEON(1): EDID for output DVI-0
[    21.382] (II) RADEON(1): Output DVI-0 disconnected
[    21.382] (WW) RADEON(1): No outputs definitely connected, trying again...
[    21.382] (II) RADEON(1): Output DVI-0 disconnected
[    21.382] (WW) RADEON(1): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    21.382] (EE) RADEON(1): Cannot position output DVI-0 relative to unknown output Monitor0
[    21.382] (II) RADEON(1): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.382] (II) RADEON(1): mem size init: gart size :1feff000 vram size: s:8000000 visible:7ac0000
[    21.382] (II) RADEON(1): EXA: Driver will allow EXA pixmaps in VRAM
[    21.382] (==) RADEON(1): DPI set to (96, 96)
[    21.382] (II) Loading sub module "fb"
[    21.382] (II) LoadModule: "fb"
[    21.382] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.382] (II) Module fb: vendor="X.Org Foundation"
[    21.382]    compiled for 1.12.3, module version = 1.0.0
[    21.382]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.382] (II) Loading sub module "ramdac"
[    21.382] (II) LoadModule: "ramdac"
[    21.382] (II) Module "ramdac" already built-in
[    21.382] (--) Depth 24 pixmap format is 32 bpp
[    21.382] (II) RADEON(0): Front buffer size: 25600K
[    21.382] (II) RADEON(0): VRAM usage limit set to 90086K
[    21.383] (==) RADEON(0): Backing store disabled
[    21.383] (WW) RADEON(0): Direct rendering disabled
[    21.383] (II) RADEON(0): Acceleration disabled
[    21.383] (==) RADEON(0): DPMS enabled
[    21.383] (==) RADEON(0): Silken mouse enabled
[    21.383] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.383] (WW) RADEON(0): Option "XAANoOffscreenPixmaps" is not used
[    21.383] (WW) RADEON(0): Option "VideoOverlay" is not used
[    21.383] (WW) RADEON(0): Option "OpenGLOverlay" is not used
[    21.383] (WW) RADEON(0): Option "Monitor-VGA-0" is not used
[    21.383] (WW) RADEON(0): Option "Movnitor-DVI-0" is not used
[    21.383] (--) RandR disabled
[    21.383] (II) RADEON(1): Front buffer size: 3072K
[    21.383] (II) RADEON(1): VRAM usage limit set to 110361K
[    21.383] (==) RADEON(1): Backing store disabled
[    21.383] (WW) RADEON(1): Direct rendering disabled
[    21.383] (II) RADEON(1): Acceleration disabled
[    21.383] (==) RADEON(1): DPMS enabled
[    21.383] (==) RADEON(1): Silken mouse enabled
[    21.383] (II) RADEON(1): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.383] (WW) RADEON(1): Option "LeftOf" is not used
[    21.383] (--) RandR disabled
[    21.383] (II) Initializing built-in extension Generic Event Extension
[    21.383] (II) Initializing built-in extension SHAPE
[    21.383] (II) Initializing built-in extension MIT-SHM
[    21.383] (II) Initializing built-in extension XInputExtension
[    21.383] (II) Initializing built-in extension XTEST
[    21.383] (II) Initializing built-in extension BIG-REQUESTS
[    21.383] (II) Initializing built-in extension SYNC
[    21.383] (II) Initializing built-in extension XKEYBOARD
[    21.383] (II) Initializing built-in extension XC-MISC
[    21.383] (II) Initializing built-in extension SECURITY
[    21.383] (II) Initializing built-in extension XINERAMA
[    21.383] (II) Initializing built-in extension XFIXES
[    21.383] (II) Initializing built-in extension RENDER
[    21.383] (II) Initializing built-in extension RANDR
[    21.383] (II) Initializing built-in extension COMPOSITE
[    21.383] (II) Initializing built-in extension DAMAGE
[    21.391] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.391] (II) AIGLX: Screen 0 is not DRI capable
[    21.403] (II) AIGLX: Loaded and initialized swrast
[    21.403] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    21.403] (II) AIGLX: Screen 1 is not DRI2 capable
[    21.403] (II) AIGLX: Screen 1 is not DRI capable
[    21.405] (II) AIGLX: Loaded and initialized swrast
[    21.405] (II) GLX: Initialized DRISWRAST GL provider for screen 1
[    21.434] (II) RADEON(0): Setting screen physical size to 338 x 270
[    21.434] (II) RADEON(0): Allocate new frame buffer 1280x1024 stride 1280
[    21.435] (II) RADEON(0): VRAM usage limit set to 108518K
[    21.459] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.462] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.462] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.462] (II) LoadModule: "evdev"
[    21.463] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.463] (II) Module evdev: vendor="X.Org Foundation"
[    21.463]    compiled for 1.12.3, module version = 2.7.0
[    21.463]    Module class: X.Org XInput Driver
[    21.463]    ABI class: X.Org XInput driver, version 16.0
[    21.463] (II) Using input driver 'evdev' for 'Power Button'
[    21.463] (**) Power Button: always reports core events
[    21.463] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.463] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.463] (--) evdev: Power Button: Found keys
[    21.463] (II) evdev: Power Button: Configuring as keyboard
[    21.463] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.463] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.463] (**) Option "xkb_rules" "evdev"
[    21.463] (**) Option "xkb_model" "pc105"
[    21.463] (**) Option "xkb_layout" "es"
[    21.466] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    21.467] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.467] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.467] (II) Using input driver 'evdev' for 'Power Button'
[    21.467] (**) Power Button: always reports core events
[    21.467] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.467] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.467] (--) evdev: Power Button: Found keys
[    21.467] (II) evdev: Power Button: Configuring as keyboard
[    21.468] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.468] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    21.468] (**) Option "xkb_rules" "evdev"
[    21.468] (**) Option "xkb_model" "pc105"
[    21.468] (**) Option "xkb_layout" "es"
[    21.468] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[    21.468] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    21.468] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    21.468] (**) Logitech USB Optical Mouse: always reports core events
[    21.468] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event4"
[    21.468] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    21.468] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[    21.468] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    21.468] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    21.468] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    21.468] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    21.468] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    21.468] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    21.468] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.468] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input4/event4"
[    21.468] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[    21.469] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    21.469] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    21.469] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    21.469] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    21.469] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    21.469] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[    21.469] (II) No input driver specified, ignoring this device.
[    21.469] (II) This device may have been added with another device file.
[    21.470] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    21.470] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    21.470] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    21.470] (**) Logitech USB Receiver: always reports core events
[    21.470] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[    21.470] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    21.470] (--) evdev: Logitech USB Receiver: Found keys
[    21.470] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    21.470] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input2/event2"
[    21.470] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    21.470] (**) Option "xkb_rules" "evdev"
[    21.470] (**) Option "xkb_model" "pc105"
[    21.470] (**) Option "xkb_layout" "es"
[    21.470] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    21.470] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    21.470] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    21.471] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    21.471] (**) Logitech USB Receiver: always reports core events
[    21.471] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    21.471] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    21.471] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    21.471] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    21.471] (--) evdev: Logitech USB Receiver: Found relative axes
[    21.471] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    21.471] (--) evdev: Logitech USB Receiver: Found absolute axes
[    21.471] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    21.471] (--) evdev: Logitech USB Receiver: Found keys
[    21.471] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    21.471] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    21.471] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    21.471] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    21.471] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.471] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input3/event3"
[    21.471] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[    21.471] (**) Option "xkb_rules" "evdev"
[    21.471] (**) Option "xkb_model" "pc105"
[    21.471] (**) Option "xkb_layout" "es"
[    21.471] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    21.471] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    21.471] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    21.471] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    21.471] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    21.471] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    21.472] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    21.472] (II) No input driver specified, ignoring this device.
[    21.472] (II) This device may have been added with another device file.
[  1315.800] (II) config/udev: removing device Logitech USB Optical Mouse
[  1315.800] (II) evdev: Logitech USB Optical Mouse: Close
[  1315.800] (II) UnloadModule: "evdev"
[  1317.538] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[  1317.538] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[  1317.538] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[  1317.538] (**) Logitech USB Optical Mouse: always reports core events
[  1317.538] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event4"
[  1317.538] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[  1317.538] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[  1317.538] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[  1317.538] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[  1317.538] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[  1317.538] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[  1317.538] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[  1317.538] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[  1317.538] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1317.538] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input5/event4"
[  1317.538] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[  1317.538] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[  1317.538] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[  1317.538] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[  1317.538] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[  1317.538] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[  1317.539] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[  1317.539] (II) No input driver specified, ignoring this device.
[  1317.539] (II) This device may have been added with another device file.
[ 12957.846] (II) Open ACPI successful (/var/run/acpid.socket)
[ 12957.884] (II) RADEON(0): EDID vendor "BNQ", prod id 30723
[ 12957.884] (II) RADEON(0): Using hsync ranges from config file
[ 12957.884] (II) RADEON(0): Using vrefresh ranges from config file
[ 12957.884] (II) RADEON(0): Printing DDC gathered Modelines:
[ 12957.884] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[ 12957.884] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 12957.884] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 12957.884] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 12957.884] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 12957.884] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 12957.885] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 13004.766] (II) Open ACPI successful (/var/run/acpid.socket)
[ 13004.808] (II) RADEON(0): EDID vendor "BNQ", prod id 30723
[ 13004.809] (II) RADEON(0): Using hsync ranges from config file
[ 13004.809] (II) RADEON(0): Using vrefresh ranges from config file
[ 13004.809] (II) RADEON(0): Printing DDC gathered Modelines:
[ 13004.809] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[ 13004.809] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 13004.809] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 13021.835] (II) RADEON(0): EDID vendor "BNQ", prod id 30723
[ 13021.835] (II) RADEON(0): Using hsync ranges from config file
[ 13021.835] (II) RADEON(0): Using vrefresh ranges from config file
[ 13021.835] (II) RADEON(0): Printing DDC gathered Modelines:
[ 13021.835] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[ 13021.835] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 13021.835] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 13032.795] (II) RADEON(0): EDID vendor "BNQ", prod id 30723
[ 13032.795] (II) RADEON(0): Using hsync ranges from config file
[ 13032.795] (II) RADEON(0): Using vrefresh ranges from config file
[ 13032.795] (II) RADEON(0): Printing DDC gathered Modelines:
[ 13032.796] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[ 13032.796] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 13032.796] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
root@brainstorm:~# 

```

Any help would be appreciated.

---

### Post by dino99 on 2012-10-23
all you need to do is to custom a xorg.conf with the 3 displays specs

sudo gedit /etc/X11/xorg.conf

either use the catalyst settings or follow:

[http://askubuntu.com/questions/128258/the-desktop-cannot-be-created-because-its-area-is-too-large-with-ati-card-and-du/128862#128862](http://askubuntu.com/questions/128258/the-desktop-cannot-be-created-because-its-area-is-too-large-with-ati-card-and-du/128862#128862)

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

note: some howto are around by googling
[http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver](http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver)

---

