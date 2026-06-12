---
title: "xubuntu-13.10-desktop-amd64 live cd does not boot GUI instead drops to shell prompt"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by empires.varun on 2013-11-30
Hello All,

I am trying to boot xubuntu live cd but after the splash screen I see no GUI instead it drops into shell prompt. Due to this I am unable to install. I have no idea how to fix this. Xorg logs indicates that it crashed with **"Segmentation Fault"**.  Any help in fixing this is greatly appreciated. I am providing inputs that I could think of for you experts to advice. Let me know if any more is needed. 

Here is the fragment from Xorg.log which indicates Seg Fault
```

[    29.996] (II) RADEON(0): Acceleration enabled
[    29.996] (==) RADEON(0): DPMS enabled
[    29.996] (==) RADEON(0): Silken mouse enabled
[    29.996] (II) RADEON(0): Set up textured video
[    29.996] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    29.996] (II) RADEON(0): [XvMC] Extension initialized.
[    29.996] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.996] (--) RandR disabled
[    30.002] (II) SELinux: Disabled on system
[    30.004] (EE) AIGLX error: Calling driver entry point failed
[    30.004] (EE) AIGLX: reverting to software rendering
[    30.004] (II) AIGLX: Screen 0 is not DRI capable
[    30.004] (EE) 
[    30.004] (EE) Backtrace:
[    30.005] (EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7f9d26fba02d]
[    30.005] (EE) 1: /usr/bin/X (0x7f9d26e18000+0x1a5d99) [0x7f9d26fbdd99]
[    30.005] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f9d25ef8000+0xfbb0) [0x7f9d25f07bb0]
[    30.005] (EE) 3: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (radeon_drm_winsys_create+0xb9) [0x7f9d1f947579]
[    30.005] (EE) 4: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (0x7f9d1f920000+0x9b79) [0x7f9d1f929b79]
[    30.005] (EE) 5: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (0x7f9d1f920000+0x22a02) [0x7f9d1f942a02]
[    30.005] (EE) 6: /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so (0x7f9d20560000+0xd1bd) [0x7f9d2056d1bd]
[    30.005] (EE) 7: /usr/lib/xorg/modules/extensions/libglx.so (0x7f9d20e58000+0x3ba11) [0x7f9d20e93a11]
[    30.005] (EE) 8: /usr/lib/xorg/modules/extensions/libglx.so (0x7f9d20e58000+0x3b00a) [0x7f9d20e9300a]
[    30.005] (EE) 9: /usr/bin/X (InitExtensions+0x41) [0x7f9d26ede341]
[    30.005] (EE) 10: /usr/bin/X (0x7f9d26e18000+0x443a0) [0x7f9d26e5c3a0]
[    30.005] (EE) 11: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f9d24b19de5]
[    30.005] (EE) 12: /usr/bin/X (0x7f9d26e18000+0x448af) [0x7f9d26e5c8af]
[    30.005] (EE) 
[    30.005] (EE) Segmentation fault at address 0x0
[    30.005] (EE) 
Fatal server error:
[    30.005] (EE) Caught signal 11 (Segmentation fault). Server aborting
[    30.005] (EE) 
[    30.005] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    30.005] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    30.005] (EE) 
[    30.041] (EE) Server terminated with error (1). Closing log file.

```

Here is **[SIZE=4]boot.log[/SIZE]**
```
calling: test-builtin 
error reading /lib/udev/hwdb.bin: No such file or directory 
load module index 
unload module index 
calling: test-builtin 
error reading /lib/udev/hwdb.bin: No such file or directory 
load module index 
unload module index 
Generating locales... 
  en_US.UTF-8... done 
Generation complete. 
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_xubuntu-default-settings.gschema.override'; ignoring override for this key. 
pwconv: failed to change the mode of /etc/passwd- to 0600 
Using CD-ROM mount point /cdrom/ 
Identifying.. [38ad09c45ad0ca8d4bd1f9cc03044a52-2] 
Scanning disc for index files.. 
Found 4 package indexes, 0 source indexes, 0 translation indexes and 1 signatures 
Found label 'Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)' 
This disc is called:  
'Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)' 
Copying package lists...gpgv: Signature made Wed Oct 16 21:29:29 2013 UTC using DSA key ID FBB75451 
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" 
 Reading Package Indexes... 0%  Reading Package Indexes... Done  
Writing new source list 
Source list entries for this disc are: 
deb cdrom:[Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)]/ saucy main multiverse restricted universe 
Repeat this process for the rest of the CDs in your set. 
 * Starting SystemD login management service[234G[ OK ] 
 * Starting Bridge file events into upstart[234G[ OK ] 
 * Starting system logging daemon[234G[ OK ] 
 * Starting mDNS/DNS-SD daemon[234G[ OK ] 
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[234G[ OK ] 
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[234G[[31mfail[39;49m] 
 * Starting bluetooth daemon[234G[ OK ] 
 * Starting startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Stopping startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting Uncomplicated firewall[234G[ OK ] 
 * Starting configure network device[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting Mount network filesystems[234G[ OK ] 
 * Starting Failsafe Boot Delay[234G[ OK ] 
 * Stopping Mount network filesystems[234G[ OK ] 
 * Starting Bridge socket events into upstart[234G[ OK ] 
 * Starting startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Stopping startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Stopping Failsafe Boot Delay[234G[ OK ] 
 * Starting System V initialisation compatibility[234G[ OK ] 
 * Starting modem connection manager[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting configure network device[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Stopping startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Starting configure network device[234G[ OK ] 
 * Starting CUPS printing spooler/server[234G[ OK ] 
 * Starting cups-browsed - Bonjour remote printer browsing daemon[234G[ OK ] 
 * Starting startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Stopping startpar bridge for notification of upstart job start/stop[234G[ OK ] 
 * Setting up X socket directories...       [240G  [234G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
saned disabled; edit /etc/default/saned 
 * Restoring resolver state...       [240G   * Stopping System V initialisation compatibility[234G[ OK ] 
[234G[ OK ] 
 * Starting network connection manager[234G[ OK ] 
 * Starting System V runlevel compatibility[234G[ OK ] 
 * Starting [234G[ OK ] 
 * Starting [234G[ OK ] 
 * Starting Restore Sound Card State[234G[ OK ] 
 * Starting ACPI daemon[234G[ OK ] 
 * Starting [234G[ OK ] 
 * Starting [234G[ OK ] 
 * Starting save kernel messages[234G[ OK ] 
 * Starting [234G[ OK ] 
 * Starting [234G[ OK ] 
 * Starting automatic crash report generation[234G[ OK ] 
 * Starting Restore Sound Card State[234G[[31mfail[39;49m] 
 * Starting regular background program processing daemon[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting CPU interrupts balancing daemon[234G[ OK ] 
 * Stopping Restore Sound Card State[234G[ OK ] 
 * Stopping crash report submission daemon[234G[ OK ] 
 * Stopping save kernel messages[234G[ OK ] 
 * Starting configure virtual network devices[234G[ OK ] 
 * Stopping System V runlevel compatibility[234G[ OK ] 
 * Starting [234G[ OK ]
```

Here is complete[SIZE=4]** Xorg.log**[/SIZE]
```
[    29.410] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    29.410] X Protocol Version 11, Revision 0
[    29.410] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    29.410] Current Operating System: Linux xubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    29.410] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
[    29.410] Build Date: 15 October 2013  09:23:37AM
[    29.410] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    29.410] Current version of pixman: 0.30.2
[    29.410]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.410] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.410] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 30 15:25:22 2013
[    29.411] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.411] (==) No Layout section.  Using the first Screen section.
[    29.411] (==) No screen section available. Using defaults.
[    29.411] (**) |-->Screen "Default Screen Section" (0)
[    29.411] (**) |   |-->Monitor "<default monitor>"
[    29.411] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.411] (==) Automatically adding devices
[    29.411] (==) Automatically enabling devices
[    29.411] (==) Automatically adding GPU devices
[    29.411] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.411]     Entry deleted from font path.
[    29.411] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.411]     Entry deleted from font path.
[    29.411] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.411]     Entry deleted from font path.
[    29.411] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.411]     Entry deleted from font path.
[    29.411] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.411]     Entry deleted from font path.
[    29.411] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.411] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.411] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.411] (II) Loader magic: 0x7f9d2723ad20
[    29.411] (II) Module ABI versions:
[    29.411]     X.Org ANSI C Emulation: 0.4
[    29.411]     X.Org Video Driver: 14.1
[    29.411]     X.Org XInput driver : 19.1
[    29.411]     X.Org Server Extension : 7.0
[    29.411] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.412] (II) xfree86: Adding drm device (/dev/dri/card1)
[    29.413] (--) PCI:*(0:0:1:0) 1002:9900:1043:1527 rev 0, Mem @ 0xb0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256
[    29.413] (--) PCI: (0:1:0:0) 1002:682f:1043:1527 rev 0, Mem @ 0xc0000000/268435456, 0xfea00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    29.413] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.414] Initializing built-in extension Generic Event Extension
[    29.414] Initializing built-in extension SHAPE
[    29.414] Initializing built-in extension MIT-SHM
[    29.414] Initializing built-in extension XInputExtension
[    29.414] Initializing built-in extension XTEST
[    29.414] Initializing built-in extension BIG-REQUESTS
[    29.414] Initializing built-in extension SYNC
[    29.414] Initializing built-in extension XKEYBOARD
[    29.414] Initializing built-in extension XC-MISC
[    29.414] Initializing built-in extension SECURITY
[    29.414] Initializing built-in extension XINERAMA
[    29.414] Initializing built-in extension XFIXES
[    29.414] Initializing built-in extension RENDER
[    29.414] Initializing built-in extension RANDR
[    29.414] Initializing built-in extension COMPOSITE
[    29.414] Initializing built-in extension DAMAGE
[    29.414] Initializing built-in extension MIT-SCREEN-SAVER
[    29.414] Initializing built-in extension DOUBLE-BUFFER
[    29.414] Initializing built-in extension RECORD
[    29.414] Initializing built-in extension DPMS
[    29.414] Initializing built-in extension X-Resource
[    29.414] Initializing built-in extension XVideo
[    29.414] Initializing built-in extension XVideo-MotionCompensation
[    29.414] Initializing built-in extension SELinux
[    29.414] Initializing built-in extension XFree86-VidModeExtension
[    29.414] Initializing built-in extension XFree86-DGA
[    29.414] Initializing built-in extension XFree86-DRI
[    29.414] Initializing built-in extension DRI2
[    29.414] (II) "glx" will be loaded by default.
[    29.414] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.414] (II) LoadModule: "dri2"
[    29.414] (II) Module "dri2" already built-in
[    29.414] (II) LoadModule: "glamoregl"
[    29.414] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    29.416] (II) Module glamoregl: vendor="X.Org Foundation"
[    29.416]     compiled for 1.14.2.901, module version = 0.5.1
[    29.416]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.416] (II) LoadModule: "glx"
[    29.416] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.416] (II) Module glx: vendor="X.Org Foundation"
[    29.416]     compiled for 1.14.3, module version = 1.0.0
[    29.416]     ABI class: X.Org Server Extension, version 7.0
[    29.416] (==) AIGLX enabled
[    29.416] Loading extension GLX
[    29.416] (==) Matched fglrx as autoconfigured driver 0
[    29.417] (==) Matched ati as autoconfigured driver 1
[    29.417] (==) Matched fglrx as autoconfigured driver 2
[    29.417] (==) Matched ati as autoconfigured driver 3
[    29.417] (==) Matched fglrx as autoconfigured driver 4
[    29.417] (==) Matched ati as autoconfigured driver 5
[    29.417] (==) Matched vesa as autoconfigured driver 6
[    29.417] (==) Matched modesetting as autoconfigured driver 7
[    29.417] (==) Matched fbdev as autoconfigured driver 8
[    29.417] (==) Assigned the driver to the xf86ConfigLayout
[    29.417] (II) LoadModule: "fglrx"
[    29.417] (WW) Warning, couldn't open module fglrx
[    29.417] (II) UnloadModule: "fglrx"
[    29.417] (II) Unloading fglrx
[    29.417] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    29.417] (II) LoadModule: "ati"
[    29.417] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    29.418] (II) Module ati: vendor="X.Org Foundation"
[    29.418]     compiled for 1.14.3, module version = 7.2.0
[    29.418]     Module class: X.Org Video Driver
[    29.418]     ABI class: X.Org Video Driver, version 14.1
[    29.418] (II) LoadModule: "radeon"
[    29.418] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.418] (II) Module radeon: vendor="X.Org Foundation"
[    29.418]     compiled for 1.14.3, module version = 7.2.0
[    29.418]     Module class: X.Org Video Driver
[    29.418]     ABI class: X.Org Video Driver, version 14.1
[    29.418] (II) LoadModule: "vesa"
[    29.419] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.419] (II) Module vesa: vendor="X.Org Foundation"
[    29.419]     compiled for 1.14.1, module version = 2.3.2
[    29.419]     Module class: X.Org Video Driver
[    29.419]     ABI class: X.Org Video Driver, version 14.1
[    29.419] (II) LoadModule: "modesetting"
[    29.419] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.419] (II) Module modesetting: vendor="X.Org Foundation"
[    29.419]     compiled for 1.14.1, module version = 0.8.0
[    29.419]     Module class: X.Org Video Driver
[    29.419]     ABI class: X.Org Video Driver, version 14.1
[    29.419] (II) LoadModule: "fbdev"
[    29.419] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.419] (II) Module fbdev: vendor="X.Org Foundation"
[    29.419]     compiled for 1.14.1, module version = 0.4.3
[    29.419]     Module class: X.Org Video Driver
[    29.419]     ABI class: X.Org Video Driver, version 14.1
[    29.419] (==) Matched fglrx as autoconfigured driver 0
[    29.419] (==) Matched ati as autoconfigured driver 1
[    29.419] (==) Matched fglrx as autoconfigured driver 2
[    29.419] (==) Matched ati as autoconfigured driver 3
[    29.419] (==) Matched fglrx as autoconfigured driver 4
[    29.419] (==) Matched ati as autoconfigured driver 5
[    29.419] (==) Matched vesa as autoconfigured driver 6
[    29.419] (==) Matched modesetting as autoconfigured driver 7
[    29.419] (==) Matched fbdev as autoconfigured driver 8
[    29.419] (==) Assigned the driver to the xf86ConfigLayout
[    29.419] (II) LoadModule: "fglrx"
[    29.420] (WW) Warning, couldn't open module fglrx
[    29.420] (II) UnloadModule: "fglrx"
[    29.420] (II) Unloading fglrx
[    29.420] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    29.420] (II) LoadModule: "ati"
[    29.421] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    29.421] (II) Module ati: vendor="X.Org Foundation"
[    29.421]     compiled for 1.14.3, module version = 7.2.0
[    29.421]     Module class: X.Org Video Driver
[    29.421]     ABI class: X.Org Video Driver, version 14.1
[    29.421] (II) LoadModule: "vesa"
[    29.421] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.421] (II) Module vesa: vendor="X.Org Foundation"
[    29.421]     compiled for 1.14.1, module version = 2.3.2
[    29.421]     Module class: X.Org Video Driver
[    29.421]     ABI class: X.Org Video Driver, version 14.1
[    29.421] (II) UnloadModule: "vesa"
[    29.421] (II) Unloading vesa
[    29.421] (II) Failed to load module "vesa" (already loaded, 0)
[    29.421] (II) LoadModule: "modesetting"
[    29.421] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.421] (II) Module modesetting: vendor="X.Org Foundation"
[    29.421]     compiled for 1.14.1, module version = 0.8.0
[    29.421]     Module class: X.Org Video Driver
[    29.421]     ABI class: X.Org Video Driver, version 14.1
[    29.421] (II) UnloadModule: "modesetting"
[    29.421] (II) Unloading modesetting
[    29.421] (II) Failed to load module "modesetting" (already loaded, 0)
[    29.421] (II) LoadModule: "fbdev"
[    29.421] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.421] (II) Module fbdev: vendor="X.Org Foundation"
[    29.421]     compiled for 1.14.1, module version = 0.4.3
[    29.421]     Module class: X.Org Video Driver
[    29.421]     ABI class: X.Org Video Driver, version 14.1
[    29.421] (II) UnloadModule: "fbdev"
[    29.421] (II) Unloading fbdev
[    29.421] (II) Failed to load module "fbdev" (already loaded, 0)
[    29.421] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    29.424] (II) VESA: driver for VESA chipsets: vesa
[    29.424] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.424] (II) FBDEV: driver for framebuffer: fbdev
[    29.424] (++) using VT number 7

[    29.430] (II) [KMS] Kernel modesetting enabled.
[    29.430] (II) [KMS] Kernel modesetting enabled.
[    29.430] (WW) Falling back to old probe method for vesa
[    29.430] (WW) Falling back to old probe method for modesetting
[    29.431] (WW) Falling back to old probe method for fbdev
[    29.431] (II) Loading sub module "fbdevhw"
[    29.431] (II) LoadModule: "fbdevhw"
[    29.431] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.431] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.431]     compiled for 1.14.3, module version = 0.0.2
[    29.431]     ABI class: X.Org Video Driver, version 14.1
[    29.431] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.431] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    29.431] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.431] (==) RADEON(0): Default visual is TrueColor
[    29.431] (==) RADEON(0): RGB weight 888
[    29.431] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    29.431] (--) RADEON(0): Chipset: "ARUBA" (ChipID = 0x9900)
[    29.431] (II) Loading sub module "dri2"
[    29.431] (II) LoadModule: "dri2"
[    29.431] (II) Module "dri2" already built-in
[    29.431] (II) Loading sub module "exa"
[    29.431] (II) LoadModule: "exa"
[    29.431] (II) Loading /usr/lib/xorg/modules/libexa.so
[    29.432] (II) Module exa: vendor="X.Org Foundation"
[    29.432]     compiled for 1.14.3, module version = 2.6.0
[    29.432]     ABI class: X.Org Video Driver, version 14.1
[    29.432] (II) RADEON(0): KMS Color Tiling: enabled
[    29.432] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    29.432] (II) RADEON(0): KMS Pageflipping: enabled
[    29.432] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    29.471] (II) RADEON(0): Output LVDS has no monitor section
[    29.638] (II) RADEON(0): Output VGA-0 has no monitor section
[    29.641] (II) RADEON(0): Output HDMI-0 has no monitor section
[    29.679] (II) RADEON(0): EDID for output LVDS
[    29.679] (II) RADEON(0): Manufacturer: LGD  Model: 2d9  Serial#: 0
[    29.679] (II) RADEON(0): Year: 2010  Week: 0
[    29.679] (II) RADEON(0): EDID Version: 1.4
[    29.679] (II) RADEON(0): Digital Display Input
[    29.679] (II) RADEON(0): 6 bits per channel
[    29.679] (II) RADEON(0): Digital interface is undefined
[    29.679] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    29.679] (II) RADEON(0): Gamma: 2.20
[    29.679] (II) RADEON(0): No DPMS capabilities specified
[    29.679] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.679] (II) RADEON(0): First detailed timing is preferred mode
[    29.679] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[    29.679] (II) RADEON(0): redX: 0.617 redY: 0.349   greenX: 0.313 greenY: 0.595
[    29.679] (II) RADEON(0): blueX: 0.151 blueY: 0.056   whiteX: 0.313 whiteY: 0.329
[    29.679] (II) RADEON(0): Manufacturer's mask: 0
[    29.679] (II) RADEON(0): Supported detailed timing:
[    29.679] (II) RADEON(0): clock: 139.5 MHz   Image Size:  344 x 194 mm
[    29.679] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2096 h_border: 0
[    29.680] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    29.680] (II) RADEON(0): Supported detailed timing:
[    29.680] (II) RADEON(0): clock: 93.0 MHz   Image Size:  344 x 194 mm
[    29.680] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2096 h_border: 0
[    29.680] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    29.680] (II) RADEON(0):  MC6JN156WF1
[    29.680] (II) RADEON(0): Unknown vendor-specific block 0
[    29.680] (II) RADEON(0): EDID (in hex):
[    29.680] (II) RADEON(0):     00ffffffffffff0030e4d90200000000
[    29.680] (II) RADEON(0):     00140104902213780a15d59e59509826
[    29.680] (II) RADEON(0):     0e505400000001010101010101010101
[    29.680] (II) RADEON(0):     0101010101017e3680b070381f403020
[    29.680] (II) RADEON(0):     350058c210000018542480b070381f40
[    29.680] (II) RADEON(0):     3020350058c210000018000000fe004d
[    29.680] (II) RADEON(0):     43364a4e813135365746310a00000000
[    29.680] (II) RADEON(0):     000041319e0000000002010a20200030
[    29.680] (II) RADEON(0): Printing probed modes for output LVDS
[    29.680] (II) RADEON(0): Modeline "1920x1080"x59.9  139.50  1920 1968 2000 2096  1080 1083 1088 1111 -hsync -vsync (66.6 kHz eP)
[    29.680] (II) RADEON(0): Modeline "1920x1080"x39.9   93.00  1920 1968 2000 2096  1080 1083 1088 1111 -hsync -vsync (44.4 kHz e)
[    29.680] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    29.680] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    29.680] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[    29.680] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    29.680] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[    29.680] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    29.680] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    29.680] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    29.680] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    29.680] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    29.680] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    29.680] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    29.680] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    29.680] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    29.850] (II) RADEON(0): EDID for output VGA-0
[    29.853] (II) RADEON(0): EDID for output HDMI-0
[    29.853] (II) RADEON(0): Output LVDS connected
[    29.853] (II) RADEON(0): Output VGA-0 disconnected
[    29.853] (II) RADEON(0): Output HDMI-0 disconnected
[    29.853] (II) RADEON(0): Using exact sizes for initial modes
[    29.853] (II) RADEON(0): Output LVDS using initial mode 1920x1080
[    29.853] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.853] (II) RADEON(0): mem size init: gart size :1fdde000 vram size: s:20000000 visible:1f7d7000
[    29.853] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    29.853] (==) RADEON(0): DPI set to (96, 96)
[    29.853] (II) Loading sub module "fb"
[    29.853] (II) LoadModule: "fb"
[    29.853] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.853] (II) Module fb: vendor="X.Org Foundation"
[    29.853]     compiled for 1.14.3, module version = 1.0.0
[    29.853]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.853] (II) Loading sub module "ramdac"
[    29.853] (II) LoadModule: "ramdac"
[    29.853] (II) Module "ramdac" already built-in
[    29.853] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[    29.853] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.853] (==) RADEON(G0): Default visual is TrueColor
[    29.853] (==) RADEON(G0): RGB weight 888
[    29.853] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[    29.853] (--) RADEON(G0): Chipset: "VERDE" (ChipID = 0x682f)
[    29.853] (II) Loading sub module "dri2"
[    29.853] (II) LoadModule: "dri2"
[    29.853] (II) Module "dri2" already built-in
[    29.853] (II) Loading sub module "glamoregl"
[    29.853] (II) LoadModule: "glamoregl"
[    29.854] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    29.854] (II) Module glamoregl: vendor="X.Org Foundation"
[    29.854]     compiled for 1.14.2.901, module version = 0.5.1
[    29.854]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.854] (II) glamor: OpenGL accelerated X.org driver based.
[    29.872] (II) glamor: EGL version 1.4 (DRI2):
[    29.886] (II) RADEON(G0): glamor detected, initialising EGL layer.
[    29.886] (II) RADEON(G0): KMS Color Tiling: disabled
[    29.886] (II) RADEON(G0): KMS Color Tiling 2D: disabled
[    29.886] (II) RADEON(G0): KMS Pageflipping: enabled
[    29.886] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[    29.886] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.886] (II) RADEON(G0): mem size init: gart size :1fbde000 vram size: s:80000000 visible:7fcc0000
[    29.886] (==) RADEON(G0): DPI set to (96, 96)
[    29.886] (II) Loading sub module "fb"
[    29.886] (II) LoadModule: "fb"
[    29.886] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.886] (II) Module fb: vendor="X.Org Foundation"
[    29.886]     compiled for 1.14.3, module version = 1.0.0
[    29.886]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.886] (II) Loading sub module "ramdac"
[    29.886] (II) LoadModule: "ramdac"
[    29.886] (II) Module "ramdac" already built-in
[    29.886] (II) UnloadModule: "vesa"
[    29.886] (II) Unloading vesa
[    29.886] (II) UnloadModule: "modesetting"
[    29.886] (II) Unloading modesetting
[    29.886] (II) UnloadModule: "fbdev"
[    29.886] (II) Unloading fbdev
[    29.886] (II) UnloadSubModule: "fbdevhw"
[    29.886] (II) Unloading fbdevhw
[    29.886] (--) Depth 24 pixmap format is 32 bpp
[    29.886] (II) RADEON(G0): [DRI2] Setup complete
[    29.886] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[    29.886] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[    29.887] (II) RADEON(G0): Front buffer size: 3072K
[    29.887] (II) RADEON(G0): VRAM usage limit set to 1881590K
[    29.887] (==) RADEON(G0): Backing store disabled
[    29.887] (II) RADEON(G0): Direct rendering enabled
[    29.996] (II) RADEON(G0): Use GLAMOR acceleration.
[    29.996] (II) RADEON(G0): Acceleration enabled
[    29.996] (==) RADEON(G0): DPMS enabled
[    29.996] (==) RADEON(G0): Silken mouse enabled
[    29.996] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.996] (II) RADEON(0): [DRI2] Setup complete
[    29.996] (II) RADEON(0): [DRI2]   DRI driver: r600
[    29.996] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    29.996] (II) RADEON(0): Front buffer size: 8160K
[    29.996] (II) RADEON(0): VRAM usage limit set to 456937K
[    29.996] (==) RADEON(0): Backing store disabled
[    29.996] (II) RADEON(0): Direct rendering enabled
[    29.996] (II) EXA(0): Driver allocated offscreen pixmaps
[    29.996] (II) EXA(0): Driver registered support for the following operations:
[    29.996] (II)         Solid
[    29.996] (II)         Copy
[    29.996] (II)         Composite (RENDER acceleration)
[    29.996] (II)         UploadToScreen
[    29.996] (II)         DownloadFromScreen
[    29.996] (II) RADEON(0): Acceleration enabled
[    29.996] (==) RADEON(0): DPMS enabled
[    29.996] (==) RADEON(0): Silken mouse enabled
[    29.996] (II) RADEON(0): Set up textured video
[    29.996] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    29.996] (II) RADEON(0): [XvMC] Extension initialized.
[    29.996] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.996] (--) RandR disabled
[    30.002] (II) SELinux: Disabled on system
[    30.004] (EE) AIGLX error: Calling driver entry point failed
[    30.004] (EE) AIGLX: reverting to software rendering
[    30.004] (II) AIGLX: Screen 0 is not DRI capable
[    30.004] (EE) 
[    30.004] (EE) Backtrace:
[    30.005] (EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7f9d26fba02d]
[    30.005] (EE) 1: /usr/bin/X (0x7f9d26e18000+0x1a5d99) [0x7f9d26fbdd99]
[    30.005] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f9d25ef8000+0xfbb0) [0x7f9d25f07bb0]
[    30.005] (EE) 3: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (radeon_drm_winsys_create+0xb9) [0x7f9d1f947579]
[    30.005] (EE) 4: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (0x7f9d1f920000+0x9b79) [0x7f9d1f929b79]
[    30.005] (EE) 5: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (0x7f9d1f920000+0x22a02) [0x7f9d1f942a02]
[    30.005] (EE) 6: /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so (0x7f9d20560000+0xd1bd) [0x7f9d2056d1bd]
[    30.005] (EE) 7: /usr/lib/xorg/modules/extensions/libglx.so (0x7f9d20e58000+0x3ba11) [0x7f9d20e93a11]
[    30.005] (EE) 8: /usr/lib/xorg/modules/extensions/libglx.so (0x7f9d20e58000+0x3b00a) [0x7f9d20e9300a]
[    30.005] (EE) 9: /usr/bin/X (InitExtensions+0x41) [0x7f9d26ede341]
[    30.005] (EE) 10: /usr/bin/X (0x7f9d26e18000+0x443a0) [0x7f9d26e5c3a0]
[    30.005] (EE) 11: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f9d24b19de5]
[    30.005] (EE) 12: /usr/bin/X (0x7f9d26e18000+0x448af) [0x7f9d26e5c8af]
[    30.005] (EE) 
[    30.005] (EE) Segmentation fault at address 0x0
[    30.005] (EE) 
Fatal server error:
[    30.005] (EE) Caught signal 11 (Segmentation fault). Server aborting
[    30.005] (EE) 
[    30.005] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    30.005] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    30.005] (EE) 
[    30.041] (EE) Server terminated with error (1). Closing log file.
```

Here is the output of [SIZE=4]**lspci**[/SIZE]
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 9900
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Chelsea LP [Radeon HD 7730M]
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
```

Here is the output of [SIZE=4]**lsmod**[/SIZE]
```
Module                  Size  Used by
dm_crypt               22728  0 
joydev                 17377  0 
arc4                   12608  2 
ath9k                 151173  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath3k                  13318  0 
btusb                  28267  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
kvm_amd                59958  0 
snd_hda_codec_realtek    51465  1 
kvm                   431315  1 kvm_amd
uvcvideo               80885  0 
snd_hda_codec_hdmi     41276  1 
asus_nb_wmi            16990  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_intel          48171  0 
videobuf2_core         40469  1 uvcvideo
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
videodev              133390  2 uvcvideo,videobuf2_core
cfg80211              479757  3 ath,ath9k,mac80211
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
snd_hwdep              13602  1 snd_hda_codec
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_seq_midi           13324  0 
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
rtsx_pci_ms            18151  0 
microcode              23518  0 
psmouse                97626  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
memstick               16760  1 rtsx_pci_ms
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13413  0 
snd_timer              29433  2 snd_pcm,snd_seq
k10temp                13126  0 
ohci_pci               13561  0 
snd                    69141  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_piix4              22106  0 
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rfcomm                 69070  0 
bluetooth             371874  12 bnep,ath3k,btusb,rfcomm
mac_hid                13205  0 
squashfs               47663  1 
overlayfs              27858  1 
nls_iso8859_1          12713  1 
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
usb_storage            62062  1 
rtsx_pci_sdmmc         23527  0 
radeon               1402449  1 
i2c_algo_bit           13413  1 radeon
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
ahci                   25819  2 
libahci                31898  1 ahci
r8169                  67341  0 
drm                   296739  3 ttm,drm_kms_helper,radeon
mii                    13934  1 r8169
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
wmi                    19070  1 asus_wmi
video                  19318  1 asus_wmi
```

---

