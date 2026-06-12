---
title: "lightdm doesn't always start"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2014-04-19
I recently installed Ubuntu 12.04 on my partner's computer.  (I also have 2 computers using 12.04.)

On my partner's computer, everything seemed to be OK, but the past few days lightdm does not always start.  Instead, she gets dumped at console 1, which scares her!

If I press Ctrl-Alt-F7 I see a text screen with one item: "Checking battery state" and a tick opposite it.

After several tests, I can't seem to find any consistency about when lightdm starts and when it doesn't, and I have no idea why this problem has arisen.

Can anyone suggest what I should do next?

David

---

### Post by ivan-janes on 2014-04-19
Check for errors in /var/log/lightdm.log.  Look into file lightdm configuration file /etc/lightdm/lightdm.conf for any strange configuration entries. If you have any display-setup-script entry try to comment it out or remove.

My example of is /etc/lightdm/lightdm.conf (fairly basic):

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false

Ivan

---

### Post by DavidS on 2014-04-20
Thanks for your suggestions.

I had eventually thought of looking at /var/log/lightdm.log, but because of the intermittent nature of the fault and because lightdm doesn't seem to keep copies of old logs, I haven't had a chance yet to look at a log immediately after a failed boot sequence.  I booted the computer 3 times this morning, and it worked perfectly each time.

The /etc/lightdm/lightdm.conf file seems (to me) unremarkable:

```
[SeatDefaults]
autologin-guest=false
autologin-user=judith
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter
```

I'll certainly save /var/log/lightdm.log if the computer mis-boots again whilst I am here - but that isn't always the case.

David

Meanwhile, thanks again for the help.

---

### Post by DavidS on 2014-04-21
This morning I started my partner's computer 3 times.  The third time it booted correctly into a GUI (with her automatically logged in already), but the first 2 boots just dumped me at a console.  I didn't make any alterations to the system along the way: the behaviour appears to be quite random, although clearly there must be some explanation for it.

It gave me an opportunity to save /var/log/lightdm/lightdm.log though.  It reads:
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=915
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for automatic login as user judith
[+0.00s] DEBUG: Starting local X display
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.04s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.05s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.05s] DEBUG: Launching X Server
[+0.05s] DEBUG: Launching process 946: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.05s] DEBUG: Waiting for ready signal from X server :0
[+0.05s] DEBUG: Stopping Plymouth, no displays replace it
[+0.73s] DEBUG: Process 946 exited with return value 1
[+0.73s] DEBUG: X server stopped
[+0.73s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.73s] DEBUG: Releasing VT 7
[+0.73s] DEBUG: Display server stopped
[+0.73s] DEBUG: Stopping display
[+0.73s] DEBUG: Display stopped
[+0.73s] DEBUG: Stopping X local seat, failed to start a display
[+0.73s] DEBUG: Stopping seat
[+0.73s] DEBUG: Seat stopped
[+0.73s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
```

I can see that it is failing, but I have no idea why.

Any suggestions?

David

---

### Post by ivan-janes on 2014-04-21
The problem is here

```
[+0.05s] DEBUG: Launching X Server
[+0.05s] DEBUG: Launching process 946: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.05s] DEBUG: Waiting for ready signal from X server :0
[+0.05s] DEBUG: Stopping Plymouth, no displays replace it
[+0.73s] DEBUG: Process 946 exited with return value 1
[+0.73s] DEBUG: X server stopped
```

X server starts and stops.  

You can try to delay lightdm deamon start as suggested on [http://ubuntuforums.org/showthread.php?t=2120913](http://ubuntuforums.org/showthread.php?t=2120913).

What does the /var/log/lightdm/x-0.log or /var/log/lightdm/x-1.log shows ?

Ivan

---

### Post by DavidS on 2014-05-08
Partly because my partner lives 150 miles away from me, partly because we have been away for a week, and partly because of the intermittent nature of the fault, it has taken me till now to get a set of log files after a failed boot.  I haven't yet had an opportunity to try adding the time delay as you suggested, and shan't be in a position to access that computer again for some time.

lightdm.log is similar to the one previously posted.  x-0.log shows```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux judith-desktop 3.2.0-61-generic #92-Ubuntu SMP Mon Mar 31 23:47:59 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-61-generic root=UUID=75ea64dd-1eb7-4389-8f4b-904b61fd726e ro quiet splash vt.handoff=7
Build Date: 16 October 2013  04:41:23PM
xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 10:06:59 2014
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
DRM_IOCTL_I915_GEM_APERTURE failed: Bad file descriptor
Assuming 131072kB available aperture size.
May lead to reduced performance or incorrect rendering.
get chip id failed: -1 [9]
param: 4, val: 0

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
```Xorg.0.log shows:```
[    14.959] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    14.959] X Protocol Version 11, Revision 0
[    14.960] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    14.960] Current Operating System: Linux judith-desktop 3.2.0-61-generic #92-Ubuntu SMP Mon Mar 31 23:47:59 UTC 2014 x86_64
[    14.964] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-61-generic root=UUID=75ea64dd-1eb7-4389-8f4b-904b61fd726e ro quiet splash vt.handoff=7
[    14.964] Build Date: 16 October 2013  04:41:23PM
[    14.964] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    14.964] Current version of pixman: 0.30.2
[    14.964] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.964] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.965] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 10:06:59 2014
[    14.976] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.977] (==) No Layout section.  Using the first Screen section.
[    14.977] (==) No screen section available. Using defaults.
[    14.977] (**) |-->Screen "Default Screen Section" (0)
[    14.977] (**) |   |-->Monitor "<default monitor>"
[    14.978] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.978] (==) Automatically adding devices
[    14.978] (==) Automatically enabling devices
[    14.979] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.979] 	Entry deleted from font path.
[    14.979] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.979] 	Entry deleted from font path.
[    14.979] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.979] 	Entry deleted from font path.
[    14.979] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.979] 	Entry deleted from font path.
[    14.979] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.979] 	Entry deleted from font path.
[    14.979] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.979] 	Entry deleted from font path.
[    14.979] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    14.979] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.979] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.980] (II) Loader magic: 0x7f96b240fb00
[    14.980] (II) Module ABI versions:
[    14.980] 	X.Org ANSI C Emulation: 0.4
[    14.980] 	X.Org Video Driver: 11.0
[    14.980] 	X.Org XInput driver : 16.0
[    14.980] 	X.Org Server Extension : 6.0
[    14.982] (--) PCI:*(0:0:2:0) 8086:2772:8086:464c rev 2, Mem @ 0x90200000/524288, 0x80000000/268435456, 0x90280000/262144, I/O @ 0x000020e0/8
[    14.983] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.983] (II) LoadModule: "extmod"
[    14.996] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.997] (II) Module extmod: vendor="X.Org Foundation"
[    14.997] 	compiled for 1.11.3, module version = 1.0.0
[    14.997] 	Module class: X.Org Server Extension
[    14.997] 	ABI class: X.Org Server Extension, version 6.0
[    14.997] (II) Loading extension MIT-SCREEN-SAVER
[    14.997] (II) Loading extension XFree86-VidModeExtension
[    14.997] (II) Loading extension XFree86-DGA
[    14.997] (II) Loading extension DPMS
[    14.997] (II) Loading extension XVideo
[    14.997] (II) Loading extension XVideo-MotionCompensation
[    14.997] (II) Loading extension X-Resource
[    14.997] (II) LoadModule: "dbe"
[    14.999] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.000] (II) Module dbe: vendor="X.Org Foundation"
[    15.000] 	compiled for 1.11.3, module version = 1.0.0
[    15.000] 	Module class: X.Org Server Extension
[    15.000] 	ABI class: X.Org Server Extension, version 6.0
[    15.000] (II) Loading extension DOUBLE-BUFFER
[    15.000] (II) LoadModule: "glx"
[    15.002] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.002] (II) Module glx: vendor="X.Org Foundation"
[    15.002] 	compiled for 1.11.3, module version = 1.0.0
[    15.002] 	ABI class: X.Org Server Extension, version 6.0
[    15.003] (==) AIGLX enabled
[    15.003] (II) Loading extension GLX
[    15.003] (II) LoadModule: "record"
[    15.006] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.007] (II) Module record: vendor="X.Org Foundation"
[    15.007] 	compiled for 1.11.3, module version = 1.13.0
[    15.007] 	Module class: X.Org Server Extension
[    15.007] 	ABI class: X.Org Server Extension, version 6.0
[    15.007] (II) Loading extension RECORD
[    15.007] (II) LoadModule: "dri"
[    15.009] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.009] (II) Module dri: vendor="X.Org Foundation"
[    15.009] 	compiled for 1.11.3, module version = 1.0.0
[    15.010] 	ABI class: X.Org Server Extension, version 6.0
[    15.010] (II) Loading extension XFree86-DRI
[    15.010] (II) LoadModule: "dri2"
[    15.011] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.012] (II) Module dri2: vendor="X.Org Foundation"
[    15.012] 	compiled for 1.11.3, module version = 1.2.0
[    15.012] 	ABI class: X.Org Server Extension, version 6.0
[    15.012] (II) Loading extension DRI2
[    15.012] (==) Matched intel as autoconfigured driver 0
[    15.012] (==) Matched vesa as autoconfigured driver 1
[    15.012] (==) Matched fbdev as autoconfigured driver 2
[    15.013] (==) Assigned the driver to the xf86ConfigLayout
[    15.013] (II) LoadModule: "intel"
[    15.014] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.015] (II) Module intel: vendor="X.Org Foundation"
[    15.015] 	compiled for 1.11.3, module version = 2.17.0
[    15.015] 	Module class: X.Org Video Driver
[    15.015] 	ABI class: X.Org Video Driver, version 11.0
[    15.015] (II) LoadModule: "vesa"
[    15.017] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.017] (II) Module vesa: vendor="X.Org Foundation"
[    15.017] 	compiled for 1.11.3, module version = 2.3.0
[    15.017] 	Module class: X.Org Video Driver
[    15.017] 	ABI class: X.Org Video Driver, version 11.0
[    15.018] (II) LoadModule: "fbdev"
[    15.019] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.020] (II) Module fbdev: vendor="X.Org Foundation"
[    15.020] 	compiled for 1.11.3, module version = 0.4.2
[    15.020] 	ABI class: X.Org Video Driver, version 11.0
[    15.020] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2)
[    15.022] (II) VESA: driver for VESA chipsets: vesa
[    15.022] (II) FBDEV: driver for framebuffer: fbdev
[    15.022] (++) using VT number 7

[    15.029] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.029] (WW) Falling back to old probe method for vesa
[    15.029] (WW) Falling back to old probe method for fbdev
[    15.029] (II) Loading sub module "fbdevhw"
[    15.029] (II) LoadModule: "fbdevhw"
[    15.030] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.030] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.030] 	compiled for 1.11.3, module version = 0.0.2
[    15.030] 	ABI class: X.Org Video Driver, version 11.0
[    15.031] drmOpenDevice: node name is /dev/dri/card0
[    15.031] drmOpenDevice: open result is 9, (OK)
[    15.062] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.062] drmOpenDevice: node name is /dev/dri/card0
[    15.063] drmOpenDevice: open result is 9, (OK)
[    15.063] drmOpenByBusid: drmOpenMinor returns 9
[    15.063] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    15.063] drmOpenByBusid: drmGetBusid reports 
[    15.063] drmOpenDevice: node name is /dev/dri/card1
[    15.070] drmOpenByBusid: drmOpenMinor returns -1
[    15.070] drmOpenDevice: node name is /dev/dri/card2
[    15.078] drmOpenByBusid: drmOpenMinor returns -1
[    15.078] drmOpenDevice: node name is /dev/dri/card3
[    15.083] drmOpenByBusid: drmOpenMinor returns -1
[    15.083] drmOpenDevice: node name is /dev/dri/card4
[    15.090] drmOpenByBusid: drmOpenMinor returns -1
[    15.091] drmOpenDevice: node name is /dev/dri/card5
[    15.096] drmOpenByBusid: drmOpenMinor returns -1
[    15.096] drmOpenDevice: node name is /dev/dri/card6
[    15.102] drmOpenByBusid: drmOpenMinor returns -1
[    15.102] drmOpenDevice: node name is /dev/dri/card7
[    15.108] drmOpenByBusid: drmOpenMinor returns -1
[    15.108] drmOpenDevice: node name is /dev/dri/card8
[    15.113] drmOpenByBusid: drmOpenMinor returns -1
[    15.113] drmOpenDevice: node name is /dev/dri/card9
[    15.118] drmOpenByBusid: drmOpenMinor returns -1
[    15.118] drmOpenDevice: node name is /dev/dri/card10
[    15.123] drmOpenByBusid: drmOpenMinor returns -1
[    15.123] drmOpenDevice: node name is /dev/dri/card11
[    15.128] drmOpenByBusid: drmOpenMinor returns -1
[    15.128] drmOpenDevice: node name is /dev/dri/card12
[    15.134] drmOpenByBusid: drmOpenMinor returns -1
[    15.134] drmOpenDevice: node name is /dev/dri/card13
[    15.139] drmOpenByBusid: drmOpenMinor returns -1
[    15.139] drmOpenDevice: node name is /dev/dri/card14
[    15.143] drmOpenByBusid: drmOpenMinor returns -1
[    15.143] drmOpenDevice: node name is /dev/dri/card15
[    15.149] drmOpenByBusid: drmOpenMinor returns -1
[    15.149] drmOpenDevice: node name is /dev/dri/card0
[    15.149] drmOpenDevice: open result is 9, (OK)
[    15.262] drmOpenDevice: node name is /dev/dri/card0
[    15.263] drmOpenDevice: open result is 9, (OK)
[    15.263] drmGetBusid returned ''
[    15.263] (EE) intel(0): [drm] failed to set drm interface version.
[    15.352] (EE) intel(0): Failed to become DRM master.
[    15.353] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.353] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    15.353] (==) intel(0): RGB weight 888
[    15.353] (==) intel(0): Default visual is TrueColor
[    15.353] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
[    15.353] (--) intel(0): Chipset: "945G"
[    15.353] (II) UnloadModule: "intel"
[    15.353] (II) Unloading intel
[    15.353] (EE) Screen(s) found, but none have a usable configuration.
[    15.353] 
Fatal server error:
[    15.353] no screens found
[    15.353] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    15.353] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.353] 
[    15.378]  ddxSigGiveUp: Closing log
[    15.378] Server terminated with error (1). Closing log file.
```I can see where the failure is occurring of course, but I have no idea what to do about it.  I'd be very grateful for any further suggestions.

David

---

