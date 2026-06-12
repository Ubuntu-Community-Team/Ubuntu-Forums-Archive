---
title: "problems with nvidia drivers on acer aspire 8920g"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by jingo_man on 2011-12-18
i have been trying all weekend to install this, to be used as an xbmc client for a short while. the built-in screen does not work, but no issues with using an external monitor, and ultimately this will use the HDMI for HD playback in any case. i have no reason to believe the hardware is otherwise faulty, though if someone can see if from logs, etc, i would not be wholly surprised.

so i have gone through versions 11.10, 10.10 and now 10.04 to get this working.

all i do is a base install of ubuntu, then add in the repository "ppa:ubuntu-x-swat/x-updates"

then:
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

if i go to the hardware drivers (or additional drivers), it doesn't seem to provide a list of new drivers i may have installed, like i have seen in the past. just nvidia_current and on 10.04 there is also the 173 driver versions too.

i then run nvidia-xconfig and reboot after.

blank screen.

i have followed through the thread on this site which goes through a lot of stuff, including manual installs, nothing seems to help.

can anyone offer further insights?

as a final note, i installed windows 7 enterprise (a technet veal copy) and nvidia installs fine and xbmc is able to use it and offload HD decoding as expected.

thanks

jingo_man

---

### Post by MAFoElffen on 2011-12-18
> **jingo_man said:**
> i have been trying all weekend to install this, to be used as an xbmc client for a short while. the built-in screen does not work, but no issues with using an external monitor, and ultimately this will use the HDMI for HD playback in any case. i have no reason to believe the hardware is otherwise faulty, though if someone can see if from logs, etc, i would not be wholly surprised.

so i have gone through versions 11.10, 10.10 and now 10.04 to get this working.

all i do is a base install of ubuntu, then add in the repository "ppa:ubuntu-x-swat/x-updates"

then:
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

if i go to the hardware drivers (or additional drivers), it doesn't seem to provide a list of new drivers i may have installed, like i have seen in the past. just nvidia_current and on 10.04 there is also the 173 driver versions too.

i then run nvidia-xconfig and reboot after.

blank screen.

[COLOR=Red]i have followed through the thread on this site which goes through a lot of stuff, including manual installs, nothing seems to help.
[/COLOR] 
can anyone offer further insights?

as a final note, i installed windows 7 enterprise (a technet veal copy) and nvidia installs fine and xbmc is able to use it and offload HD decoding as expected.

thanks

jingo_man
I suspect the thread you were referring to in this forum was my sticky... Experience with XServer Issues since '88. Have a linux media server and clients (among a lot more).

To make sure we are on the same page-
- What are you doing and what do you want to do?
- What is your hgraphics ardware?

Even though you didn't really come out and say this, I take that you have a laptop (adds in ACPI and screen brightness settings) and that it has some kind of nVidia GPU.

If you could please post the results of 
```

lspci -vnn | grep VGA

```I'm going to end this post at that and continue in another. Purpose- I know you are trying to get this worked out and I need that info.

---

### Post by MAFoElffen on 2011-12-18
I see that you've tried different versions of Ubuntu.

I see that you added the xswat ppa(???) Why?  Was your reasoning that others didn't work as expected so you tried more? That is why you don't see other drivers / just the xswat drivers.

Have you looked at your laptop screen with a flashlight to see if it is just dimmed? If so... Have you tried this:
1) edit rc.local
```

gksudo gedit /etc/rc.local

```2) Add the command before EXIT 0     
```

setpci -s 00:02.0 F4.B-0

```3) Restart.

Also on laptops, I've notice with 2 out-of 5 of my laptops, that the hot-keys for bright or dim are reversed when running Ubuntu. One of those is my Acer Aspire (hint).

Also what might be of help is to post your /etc/X11/xorg.conf and /var/log/Xorg.0.log files.  Those would show how your devices are configured, how they show up when probed and the data they are returning.

EDIT-- nVidia GeForce 9650M GS

---

### Post by jingo_man on 2011-12-18
i basically need to get the nvidia drivers above version 180 (i think), when VDPAU was introduced. this is so XBMC can offload HD decoding.

and thats it. it'll connect via HDMI to the tv and be a media player.

i tried the different O/S versions as I wasn't sure if the different versions would work better with the drivers.

i have only previously used the nvidia-vdpau and x-swat repositories, which have worked so i didn't see any need to change. plus i don't know many other packages and would rather use these pre-made packages than manually compiling.

however, through the course of troubleshooting, i tried the manual install with the .run files directly from nvidia too.

output of the command you were asking for produced:

```

	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 9500M GS] (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-

```

i have attached the 2 Xorg files you mentioned too. the xorg.conf file i renamed to .broken so it would produce some desktop to use.

thanks for getting back to me on this though

---

### Post by MAFoElffen on 2011-12-18
> **jingo_man said:**
> i basically need to get the nvidia drivers above version 180 (i think), when VDPAU was introduced. this is so XBMC can offload HD decoding.

and thats it. it'll connect via HDMI to the tv and be a media player.

i tried the different O/S versions as I wasn't sure if the different versions would work better with the drivers.

i have only previously used the nvidia-vdpau and x-swat repositories, which have worked so i didn't see any need to change. plus i don't know many other packages and would rather use these pre-made packages than manually compiling.

however, through the course of troubleshooting, i tried the manual install with the .run files directly from nvidia too.

output of the command you were asking for produced:

```

01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 9500M GS] (rev a1)

```i have attached the 2 Xorg files you mentioned too. the xorg.conf file i renamed to .broken so it would produce some desktop to use.

thanks for getting back to me on this though
I'm running binary v109.10 and is running well. I have a good turial on that here:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")**[/SIZE][/COLOR][/SIZE][/COLOR]

Other notes- Ubuntu version is mood point.  Just different modules and layers under X... Just as You can stack different layer on top of X.

*** Looking through your logs.... Back soon.

---

### Post by MAFoElffen on 2011-12-18
I'm posting this from "my" Acer Aspire 5570Z, connected to an external monitor so you can see some differences from your Xorg.O.log file and this one. Yes this one has an Intel GPU, but basically...
```

[   350.416] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   350.416] X Protocol Version 11, Revision 0
[   350.416] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   350.417] Current Operating System: Linux Aspire-5570Z 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[   350.417] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c70e0157-cf9d-4688-9370-9eaf716c2be8 ro quiet splash vt.handoff=7
[   350.417] Build Date: 19 October 2011  05:09:41AM
[   350.417] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   350.417] Current version of pixman: 0.22.2
[   350.417]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   350.417] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   350.417] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 18 13:07:01 2011
[   350.417] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   350.418] (==) No Layout section.  Using the first Screen section.
[   350.418] (==) No screen section available. Using defaults.
[   350.418] (**) |-->Screen "Default Screen Section" (0)
[   350.418] (**) |   |-->Monitor "<default monitor>"
[   350.418] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   350.418] (==) Automatically adding devices
[   350.418] (==) Automatically enabling devices
[   350.418] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   350.418]     Entry deleted from font path.
[   350.418] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   350.418] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   350.418] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   350.418] (II) Loader magic: 0x823ada0
[   350.418] (II) Module ABI versions:
[   350.418]     X.Org ANSI C Emulation: 0.4
[   350.418]     X.Org Video Driver: 10.0
[   350.418]     X.Org XInput driver : 12.3
[   350.418]     X.Org Server Extension : 5.0
[   350.419] (--) PCI:*(0:0:2:0) 8086:27a2:1025:0110 rev 3, Mem @ 0xd0300000/524288, 0xc0000000/268435456, 0xd0400000/262144, I/O @ 0x00001800/8
[   350.420] (--) PCI: (0:0:2:1) 8086:27a6:1025:0110 rev 3, Mem @ 0xd0380000/524288
[   350.420] (II) Open ACPI successful (/var/run/acpid.socket)
[   350.420] (II) LoadModule: "extmod"
[   350.420] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   350.421] (II) Module extmod: vendor="X.Org Foundation"
[   350.421]     compiled for 1.10.4, module version = 1.0.0
[   350.421]     Module class: X.Org Server Extension
[   350.421]     ABI class: X.Org Server Extension, version 5.0
[   350.421] (II) Loading extension MIT-SCREEN-SAVER
[   350.421] (II) Loading extension XFree86-VidModeExtension
[   350.421] (II) Loading extension XFree86-DGA
[   350.421] (II) Loading extension DPMS
[   350.421] (II) Loading extension XVideo
[   350.421] (II) Loading extension XVideo-MotionCompensation
[   350.421] (II) Loading extension X-Resource
[   350.421] (II) LoadModule: "dbe"
[   350.421] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   350.421] (II) Module dbe: vendor="X.Org Foundation"
[   350.421]     compiled for 1.10.4, module version = 1.0.0
[   350.421]     Module class: X.Org Server Extension
[   350.421]     ABI class: X.Org Server Extension, version 5.0
[   350.421] (II) Loading extension DOUBLE-BUFFER
[   350.421] (II) LoadModule: "glx"
[   350.421] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   350.422] (II) Module glx: vendor="X.Org Foundation"
[   350.422]     compiled for 1.10.4, module version = 1.0.0
[   350.422]     ABI class: X.Org Server Extension, version 5.0
[   350.422] (==) AIGLX enabled
[   350.422] (II) Loading extension GLX
[   350.422] (II) LoadModule: "record"
[   350.422] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   350.422] (II) Module record: vendor="X.Org Foundation"
[   350.422]     compiled for 1.10.4, module version = 1.13.0
[   350.422]     Module class: X.Org Server Extension
[   350.422]     ABI class: X.Org Server Extension, version 5.0
[   350.422] (II) Loading extension RECORD
[   350.422] (II) LoadModule: "dri"
[   350.422] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   350.423] (II) Module dri: vendor="X.Org Foundation"
[   350.423]     compiled for 1.10.4, module version = 1.0.0
[   350.423]     ABI class: X.Org Server Extension, version 5.0
[   350.423] (II) Loading extension XFree86-DRI
[   350.423] (II) LoadModule: "dri2"
[   350.423] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   350.423] (II) Module dri2: vendor="X.Org Foundation"
[   350.423]     compiled for 1.10.4, module version = 1.2.0
[   350.423]     ABI class: X.Org Server Extension, version 5.0
[   350.423] (II) Loading extension DRI2
[   350.423] (==) Matched intel as autoconfigured driver 0
[   350.423] (==) Matched vesa as autoconfigured driver 1
[   350.423] (==) Matched fbdev as autoconfigured driver 2
[   350.423] (==) Assigned the driver to the xf86ConfigLayout
[   350.423] (II) LoadModule: "intel"
[   350.424] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   350.424] (II) Module intel: vendor="X.Org Foundation"
[   350.424]     compiled for 1.10.4, module version = 2.15.901
[   350.424]     Module class: X.Org Video Driver
[   350.424]     ABI class: X.Org Video Driver, version 10.0
[   350.424] (II) LoadModule: "vesa"
[   350.424] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   350.425] (II) Module vesa: vendor="X.Org Foundation"
[   350.425]     compiled for 1.10.2, module version = 2.3.0
[   350.425]     Module class: X.Org Video Driver
[   350.425]     ABI class: X.Org Video Driver, version 10.0
[   350.425] (II) LoadModule: "fbdev"
[   350.425] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   350.425] (II) Module fbdev: vendor="X.Org Foundation"
[   350.425]     compiled for 1.10.0, module version = 0.4.2
[   350.425]     ABI class: X.Org Video Driver, version 10.0
[   350.425] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   350.426] (II) VESA: driver for VESA chipsets: vesa
[   350.426] (II) FBDEV: driver for framebuffer: fbdev
[   350.426] (++) using VT number 7

[   350.428] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   350.428] (WW) Falling back to old probe method for vesa
[   350.428] (WW) Falling back to old probe method for fbdev
[   350.428] (II) Loading sub module "fbdevhw"
[   350.428] (II) LoadModule: "fbdevhw"
[   350.429] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   350.429] (II) Module fbdevhw: vendor="X.Org Foundation"
[   350.429]     compiled for 1.10.4, module version = 0.0.2
[   350.429]     ABI class: X.Org Video Driver, version 10.0
[   350.429] drmOpenDevice: node name is /dev/dri/card0
[   350.429] drmOpenDevice: open result is 12, (OK)
[   350.429] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   350.429] drmOpenDevice: node name is /dev/dri/card0
[   350.429] drmOpenDevice: open result is 12, (OK)
[   350.429] drmOpenByBusid: drmOpenMinor returns 12
[   350.429] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   350.429] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   350.429] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   350.429] (==) intel(0): RGB weight 888
[   350.429] (==) intel(0): Default visual is TrueColor
[   350.429] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[   350.429] (--) intel(0): Chipset: "945GM"
[   350.429] (**) intel(0): Relaxed fencing disabled
[   350.429] (**) intel(0): Wait on SwapBuffers? enabled
[   350.429] (**) intel(0): Triple buffering? enabled
[   350.429] (**) intel(0): Framebuffer tiled
[   350.429] (**) intel(0): Pixmaps tiled
[   350.429] (**) intel(0): 3D buffers tiled
[   350.429] (**) intel(0): SwapBuffers wait enabled
[   350.429] (==) intel(0): video overlay key set to 0x101fe
[   350.429] (II) intel(0): Output LVDS1 has no monitor section
[   350.430] (II) intel(0): found backlight control interface /sys/class/backlight/intel_backlight
[   350.501] (II) intel(0): Output VGA1 has no monitor section
[   350.501] (II) intel(0): Output TV1 has no monitor section
[   350.501] (II) intel(0): EDID for output LVDS1
[   350.501] (II) intel(0): Manufacturer: QDS  Model: 1f  Serial#: 0
[   350.501] (II) intel(0): Year: 2005  Week: 0
[   350.501] (II) intel(0): EDID Version: 1.3
[   350.501] (II) intel(0): Digital Display Input
[   350.501] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[   350.501] (II) intel(0): Gamma: 2.20
[   350.501] (II) intel(0): No DPMS capabilities specified
[   350.501] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   350.501] (II) intel(0): First detailed timing is preferred mode
[   350.502] (II) intel(0): redX: 0.569 redY: 0.329   greenX: 0.310 greenY: 0.550
[   350.502] (II) intel(0): blueX: 0.159 blueY: 0.135   whiteX: 0.312 whiteY: 0.328
[   350.502] (II) intel(0): Manufacturer's mask: 0
[   350.502] (II) intel(0): Supported detailed timing:
[   350.502] (II) intel(0): clock: 68.9 MHz   Image Size:  304 x 190 mm
[   350.502] (II) intel(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1408 h_border: 0
[   350.502] (II) intel(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 816 v_border: 0
[   350.502] (II) intel(0): Unknown vendor-specific block f
[   350.502] (II) intel(0):  QUANTADISPLAY
[   350.502] (II) intel(0):  QD14TL012
[   350.502] (II) intel(0): EDID (in hex):
[   350.502] (II) intel(0):     00ffffffffffff0044931f0000000000
[   350.502] (II) intel(0):     000f0103801e13780ad7e091544f8c28
[   350.502] (II) intel(0):     22505400000001010101010101010101
[   350.502] (II) intel(0):     010101010101ea1a0080502010301520
[   350.502] (II) intel(0):     440030be100000180000000f0008002a
[   350.502] (II) intel(0):     0001000400324a041901000000fe0051
[   350.502] (II) intel(0):     55414e5441444953504c4159000000fe
[   350.502] (II) intel(0):     0051443134544c3031320a202020003f
[   350.502] (II) intel(0): EDID vendor "QDS", prod id 31
[   350.502] (II) intel(0): Printing DDC gathered Modelines:
[   350.502] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   350.502] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   350.502] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   350.502] (II) intel(0): Printing probed modes for output LVDS1
[   350.502] (II) intel(0): Modeline "1280x800"x60.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   350.502] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   350.502] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   350.502] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   350.502] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   350.569] (II) intel(0): EDID for output VGA1
[   350.569] (II) intel(0): Manufacturer: NEC  Model: 5dc4  Serial#: 16843009
[   350.569] (II) intel(0): Year: 2000  Week: 32
[   350.569] (II) intel(0): EDID Version: 1.2
[   350.569] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   350.569] (II) intel(0): Sync:  Separate  Composite
[   350.569] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 24
[   350.569] (II) intel(0): Gamma: 2.20
[   350.569] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   350.569] (II) intel(0): First detailed timing is preferred mode
[   350.569] (II) intel(0): redX: 0.629 redY: 0.334   greenX: 0.289 greenY: 0.599
[   350.569] (II) intel(0): blueX: 0.148 blueY: 0.067   whiteX: 0.283 whiteY: 0.297
[   350.569] (II) intel(0): Supported established timings:
[   350.569] (II) intel(0): 720x400@70Hz
[   350.569] (II) intel(0): 720x400@88Hz
[   350.569] (II) intel(0): 640x480@60Hz
[   350.569] (II) intel(0): 640x480@67Hz
[   350.569] (II) intel(0): 640x480@72Hz
[   350.569] (II) intel(0): 640x480@75Hz
[   350.569] (II) intel(0): 800x600@56Hz
[   350.569] (II) intel(0): 800x600@60Hz
[   350.569] (II) intel(0): 800x600@72Hz
[   350.569] (II) intel(0): 800x600@75Hz
[   350.569] (II) intel(0): 832x624@75Hz
[   350.569] (II) intel(0): 1024x768@60Hz
[   350.569] (II) intel(0): 1024x768@70Hz
[   350.569] (II) intel(0): 1024x768@75Hz
[   350.569] (II) intel(0): Manufacturer's mask: 0
[   350.569] (II) intel(0): Supported standard timings:
[   350.569] (II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[   350.570] (II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[   350.570] (II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[   350.570] (II) intel(0): #3: hsize: 1152  vsize 864  refresh: 70  vid: 19057
[   350.570] (II) intel(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   350.570] (II) intel(0): Supported detailed timing:
[   350.570] (II) intel(0): clock: 94.5 MHz   Image Size:  310 x 232 mm
[   350.570] (II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
[   350.570] (II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
[   350.570] (II) intel(0): Ranges: V min: 55 V max: 120 Hz, H min: 31 H max: 70 kHz, PixClock max 115 MHz
[   350.570] (II) intel(0): Monitor name: AccuSync 70
[   350.570] (II) intel(0): Serial No: 0838594YA
[   350.570] (II) intel(0): EDID (in hex):
[   350.570] (II) intel(0):     00ffffffffffff0038a3c45d01010101
[   350.570] (II) intel(0):     200a01020c211878ea2118a1554a9926
[   350.570] (II) intel(0):     11484cffee00315945596159714a8140
[   350.570] (II) intel(0):     010101010101ea240060410028303060
[   350.570] (II) intel(0):     130036e81000001e000000fd0037781f
[   350.570] (II) intel(0):     460b000a202020202020000000fc0041
[   350.570] (II) intel(0):     63637553796e632037300a20000000ff
[   350.570] (II) intel(0):     003038333835393459410a20202000ea
[   350.570] (II) intel(0): Printing probed modes for output VGA1
[   350.570] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   350.570] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   350.570] (II) intel(0): Modeline "1152x864"x70.0   96.73  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[   350.570] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   350.570] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   350.570] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   350.570] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   350.570] (II) intel(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   350.570] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   350.570] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   350.570] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   350.570] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   350.570] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   350.570] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   350.570] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   350.570] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   350.570] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   350.570] (II) intel(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[   350.570] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   350.570] (II) intel(0): EDID for output TV1
[   350.570] (II) intel(0): Printing probed modes for output TV1
[   350.570] (II) intel(0): Modeline "848x480"x30.0   14.51  848 849 912 944  480 481 512 513 (15.4 kHz)
[   350.570] (II) intel(0): Modeline "640x480"x30.0   11.31  640 641 704 736  480 481 512 513 (15.4 kHz)
[   350.570] (II) intel(0): Modeline "1024x768"x30.0   26.89  1024 1025 1088 1120  768 769 800 801 (24.0 kHz)
[   350.570] (II) intel(0): Modeline "800x600"x30.0   17.00  800 801 864 896  600 601 632 633 (19.0 kHz)
[   350.570] (II) intel(0): Output LVDS1 connected
[   350.570] (II) intel(0): Output VGA1 connected
[   350.570] (II) intel(0): Output TV1 disconnected
[   350.570] (II) intel(0): Using exact sizes for initial modes
[   350.570] (II) intel(0): Output LVDS1 using initial mode 1024x768
[   350.570] (II) intel(0): Output VGA1 using initial mode 1024x768
[   350.570] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   350.571] (II) intel(0): Kernel page flipping support detected, enabling
[   350.571] (**) intel(0): Display dimensions: (300, 190) mm
[   350.571] (**) intel(0): DPI set to (86, 102)
[   350.571] (II) Loading sub module "fb"
[   350.571] (II) LoadModule: "fb"
[   350.571] (II) Loading /usr/lib/xorg/modules/libfb.so
[   350.571] (II) Module fb: vendor="X.Org Foundation"
[   350.571]     compiled for 1.10.4, module version = 1.0.0
[   350.571]     ABI class: X.Org ANSI C Emulation, version 0.4
[   350.571] (II) Loading sub module "dri2"
[   350.571] (II) LoadModule: "dri2"
[   350.572] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   350.572] (II) Module dri2: vendor="X.Org Foundation"
[   350.572]     compiled for 1.10.4, module version = 1.2.0
[   350.572]     ABI class: X.Org Server Extension, version 5.0
[   350.572] (II) UnloadModule: "vesa"
[   350.572] (II) Unloading vesa
[   350.572] (II) UnloadModule: "fbdev"
[   350.572] (II) Unloading fbdev
[   350.572] (II) UnloadModule: "fbdevhw"
[   350.572] (II) Unloading fbdevhw
[   350.572] (==) Depth 24 pixmap format is 32 bpp
[   350.572] (II) intel(0): [DRI2] Setup complete
[   350.572] (II) intel(0): [DRI2]   DRI driver: i915
[   350.572] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[   350.572] (II) UXA(0): Driver registered support for the following operations:
[   350.572] (II)         solid
[   350.572] (II)         copy
[   350.572] (II)         composite (RENDER acceleration)
[   350.572] (II)         put_image
[   350.572] (II)         get_image
[   350.572] (==) intel(0): Backing store disabled
[   350.572] (==) intel(0): Silken mouse enabled
[   350.572] (II) intel(0): Initializing HW Cursor
[   350.684] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   350.685] (==) intel(0): DPMS enabled
[   350.685] (==) intel(0): Intel XvMC decoder disabled
[   350.685] (II) intel(0): Set up textured video
[   350.685] (II) intel(0): Set up overlay video
[   350.685] (II) intel(0): direct rendering: DRI2 Enabled
[   350.685] (==) intel(0): hotplug detection: "enabled"
[   350.686] (--) RandR disabled
[   350.686] (II) Initializing built-in extension Generic Event Extension
[   350.686] (II) Initializing built-in extension SHAPE
[   350.686] (II) Initializing built-in extension MIT-SHM
[   350.686] (II) Initializing built-in extension XInputExtension
[   350.686] (II) Initializing built-in extension XTEST
[   350.686] (II) Initializing built-in extension BIG-REQUESTS
[   350.686] (II) Initializing built-in extension SYNC
[   350.686] (II) Initializing built-in extension XKEYBOARD
[   350.686] (II) Initializing built-in extension XC-MISC
[   350.686] (II) Initializing built-in extension SECURITY
[   350.686] (II) Initializing built-in extension XINERAMA
[   350.686] (II) Initializing built-in extension XFIXES
[   350.686] (II) Initializing built-in extension RENDER
[   350.686] (II) Initializing built-in extension RANDR
[   350.686] (II) Initializing built-in extension COMPOSITE
[   350.686] (II) Initializing built-in extension DAMAGE
[   350.686] (II) Initializing built-in extension GESTURE
[   350.710] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i915_dri.so
[   350.715] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   350.715] (II) AIGLX: enabled GLX_INTEL_swap_event
[   350.715] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   350.715] (II) AIGLX: enabled GLX_SGI_make_current_read
[   350.715] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   350.715] (II) AIGLX: Loaded and initialized i915
[   350.715] (II) GLX: Initialized DRI2 GL provider for screen 0
[   350.716] (II) intel(0): Setting screen physical size to 270 x 203
[   350.742] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   350.755] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   350.755] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   350.755] (II) LoadModule: "evdev"
[   350.755] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   350.756] (II) Module evdev: vendor="X.Org Foundation"
[   350.756]     compiled for 1.10.2, module version = 2.6.0
[   350.756]     Module class: X.Org XInput Driver
[   350.756]     ABI class: X.Org XInput driver, version 12.3
[   350.756] (II) Using input driver 'evdev' for 'Power Button'
[   350.756] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   350.756] (**) Power Button: always reports core events
[   350.756] (**) Power Button: Device: "/dev/input/event3"
[   350.756] (--) Power Button: Found keys
[   350.756] (II) Power Button: Configuring as keyboard
[   350.756] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   350.756] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   350.756] (**) Option "xkb_rules" "evdev"
[   350.756] (**) Option "xkb_model" "pc105"
[   350.756] (**) Option "xkb_layout" "us"
[   350.773] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   350.774] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   350.774] (II) Using input driver 'evdev' for 'Video Bus'
[   350.774] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   350.774] (**) Video Bus: always reports core events
[   350.774] (**) Video Bus: Device: "/dev/input/event5"
[   350.774] (--) Video Bus: Found keys
[   350.774] (II) Video Bus: Configuring as keyboard
[   350.774] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[   350.774] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   350.774] (**) Option "xkb_rules" "evdev"
[   350.774] (**) Option "xkb_model" "pc105"
[   350.774] (**) Option "xkb_layout" "us"
[   350.977] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   350.977] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   350.977] (II) Using input driver 'evdev' for 'Power Button'
[   350.977] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   350.977] (**) Power Button: always reports core events
[   350.977] (**) Power Button: Device: "/dev/input/event1"
[   350.977] (--) Power Button: Found keys
[   350.978] (II) Power Button: Configuring as keyboard
[   350.978] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[   350.978] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   350.978] (**) Option "xkb_rules" "evdev"
[   350.978] (**) Option "xkb_model" "pc105"
[   350.978] (**) Option "xkb_layout" "us"
[   350.979] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   350.979] (II) No input driver/identifier specified (ignoring)
[   350.980] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   350.980] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   350.980] (II) Using input driver 'evdev' for 'Sleep Button'
[   350.980] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   350.980] (**) Sleep Button: always reports core events
[   350.981] (**) Sleep Button: Device: "/dev/input/event2"
[   350.981] (--) Sleep Button: Found keys
[   350.981] (II) Sleep Button: Configuring as keyboard
[   350.981] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[   350.981] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   350.981] (**) Option "xkb_rules" "evdev"
[   350.981] (**) Option "xkb_model" "pc105"
[   350.981] (**) Option "xkb_layout" "us"
[   350.986] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[   350.986] (II) No input driver/identifier specified (ignoring)
[   350.995] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   350.995] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   350.995] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   350.995] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   350.995] (**) AT Translated Set 2 keyboard: always reports core events
[   350.995] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   350.995] (--) AT Translated Set 2 keyboard: Found keys
[   350.996] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   350.996] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   350.996] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   350.996] (**) Option "xkb_rules" "evdev"
[   350.996] (**) Option "xkb_model" "pc105"
[   350.996] (**) Option "xkb_layout" "us"
[   350.997] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[   350.997] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   350.997] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   350.997] (II) LoadModule: "synaptics"
[   350.997] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   350.997] (II) Module synaptics: vendor="X.Org Foundation"
[   350.997]     compiled for 1.10.4, module version = 1.4.1
[   350.997]     Module class: X.Org XInput Driver
[   350.997]     ABI class: X.Org XInput driver, version 12.3
[   350.997] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   350.997] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   350.997] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   350.997] (**) Option "Device" "/dev/input/event6"
[   350.998] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   350.998] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   350.998] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   350.998] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   350.998] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[   351.004] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   351.004] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   351.016] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[   351.016] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   351.016] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   351.016] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   351.016] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[   351.016] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   351.017] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   351.017] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   351.017] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   351.017] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[   351.017] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   351.018] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   351.018] (II) No input driver/identifier specified (ignoring)
[   351.427] (II) intel(0): EDID vendor "QDS", prod id 31
[   351.427] (II) intel(0): Printing DDC gathered Modelines:
[   351.427] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   351.658] (II) intel(0): EDID vendor "QDS", prod id 31
[   351.658] (II) intel(0): Printing DDC gathered Modelines:
[   351.658] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   351.727] (II) intel(0): EDID vendor "QDS", prod id 31
[   351.727] (II) intel(0): Printing DDC gathered Modelines:
[   351.727] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   359.640] (II) intel(0): EDID vendor "QDS", prod id 31
[   359.640] (II) intel(0): Printing DDC gathered Modelines:
[   359.640] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   360.021] (II) intel(0): EDID vendor "QDS", prod id 31
[   360.021] (II) intel(0): Printing DDC gathered Modelines:
[   360.021] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   360.117] (II) intel(0): EDID vendor "QDS", prod id 31
[   360.117] (II) intel(0): Printing DDC gathered Modelines:
[   360.117] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
[   360.219] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[   366.420] (II) intel(0): EDID vendor "QDS", prod id 31
[   366.420] (II) intel(0): Printing DDC gathered Modelines:
[   366.420] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)

```

Then 2 things I just rembered on this laptop... Function keys 
- If you use <Fn><F5> it toggles all dislays off/on
- If you use <Fn><F6> it toggles just the internal LCDall dislay off/on, hile leaving the external display on.
You boot these and it retains that setting...

Okay, back to my other PC.

---

### Post by MAFoElffen on 2011-12-18
Back- In your logs, I saw your card fine. I see that it's currently using VESA. and some "DELL 1703FP" display, which I'm assuming is the external display.  What I do not see is any trace your your internal display...

Please install "hwinfo" and post the results of:
```

sudo hwinfo --monitor
xrandr -r

```
Like I said, I see the Dell.  Maybe also if you temporarily point to the nvidia driver (maybe run "sudo nvidia-xconfig" again with both monitor and LCD...) then I could see if that Xorg.0.log see what it does with that.

---

### Post by jingo_man on 2011-12-20
hey MAF

Thanks for that. I will get the extra info you require later today (this whole damn work thing keeps getting in the way! haha)

But the builtin monitor has a faulty backlight, and cant be made out at all. Hence why the Dell monitor always needs to be plugged in, or output to a HDTV via HDMI, to get the desktop.

Would this make a difference? Perhaps the xorg.conf is pointing to the wrong device id/number/etc?

---

### Post by jingo_man on 2011-12-20
here's the output of the hwinfo command:

```

user@host:~$ sudo hwinfo --monitor
32: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 640x480@60Hz
  Driver Info #0:
    Max. Resolution: 640x480
    Vert. Sync Range: 50-70 Hz
    Hor. Sync Range: 31-33 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

the main thread i started working through was the sticky at the top of this site's Installation sub-forum:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

inside this, i also followed the link to "Installing Nvidia Binary drivers" guide which you reference, on at least 1 of my installation attempts. i will redo the steps here to ensure i have expected drivers we are at least in the same chapter, if not the same page...

and to confirm its an Acer Aspire 8920G laptop, which has an NVidia 9500M GS graphics card.

thanks again

---

### Post by jingo_man on 2011-12-20
I followed through the manual Install Binary Drivers guide again, and attached are the relevant log files.

There are references to the driver(s) for NVidia are loading.

> 
user@host:~$ dmesg | grep -i nvidia
[   10.147214] nvidia: module license 'NVIDIA' taints kernel.
[   10.501235] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.501250] nvidia 0000:01:00.0: setting latency timer to 64
[   10.502194] NVRM: loading NVIDIA UNIX x86 Kernel Module  290.10  Wed Nov 16 19:27:25 PST 2011


It detects 2 devices:

> 
/var/log/Xorg.0.log

exert:
(--) Dec 20 14:51:29 NVIDIA(0): Connected display device(s) on GeForce 9500M GS at PCI:1:0:0
(--) Dec 20 14:51:29 NVIDIA(0):     DELL 1703FP (CRT-0)
(--) Dec 20 14:51:29 NVIDIA(0):     Seiko/Epson (DFP-0)
(--) Dec 20 14:51:29 NVIDIA(0): DELL 1703FP (CRT-0): 400.0 MHz maximum pixel clock
(--) Dec 20 14:51:29 NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock


There doesnt seem to be obvious errors.

Yet, I have a blank screen on the attached/external Dell monitor. If I delete the Xorg.conf and reboot, I get a desktop back and in the System > Admin > Hardware Drivers says "No proprietary drivers are in use on this system."

---

