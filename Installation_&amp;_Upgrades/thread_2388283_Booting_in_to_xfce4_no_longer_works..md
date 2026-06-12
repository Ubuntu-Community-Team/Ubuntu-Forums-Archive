---
title: "Booting in to xfce4 no longer works."
date: 2018-03-31
forum: Installation &amp; Upgrades
---

### Post by atomicspin2 on 2018-03-31
Tried to open up the dual boot and got this:

```
[COLOR=#000000]Entering /mnt/stateful_partition/crouton/chroots/precise...[/COLOR]/usr/bin/startxfce4: Starting X server

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-75-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.8.11 #1 SMP Tue Mar 27 22:37:59 PDT 2018 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2539520 verity payload=PARTUUID=f6d5bfaa-5295-054e-bbb8-3fb89b8b1e34/PARTNROFF=1 hashtree=PARTUUID=f6d5bfaa-5295-054e-bbb8-3fb89b8b1e34/PARTNROFF=1 hashstart=2539520 alg=sha1 root_hexdigest=71cdb03f55a65d0c15b5cae218325004984865ab salt=bc08fa947d3ca1cfe948d0fc2fc6ad89da4bbb24e0049cb7dc9ac750b2271115" noinitrd vt.global_cursor_default=0 kern_guid=f6d5bfaa-5295-054e-bbb8-3fb89b8b1e34 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic iTCO_vendor_support.vendorsupport=3  
Build Date: 12 February 2015  03:37:52PM
xorg-server 2:1.15.1-0ubuntu2~precise5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Fri Mar 30 23:43:55 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
setversion 1.4 failed: Permission denied
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
Error org.freedesktop.DBus.Error.UnknownMethod: Method "ReleaseDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist

xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
Error org.freedesktop.DBus.Error.UnknownMethod: Method "ReleaseDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist

xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
Unable to set master
(EE) 
Fatal server error:
(EE) AddScreen/ScreenInit failed for driver 0
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.
(EE) 
Error org.freedesktop.DBus.Error.UnknownMethod: Method "TakeDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist

(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: No such file or directory
/usr/bin/xinit: server error [COLOR=#000000]Unmounting /mnt/stateful_partition/crouton/chroots/precise...[/COLOR]
```

---

### Post by ajgreeny on 2018-03-31
We don't have much info in order for us to help you.

What two OSs in your dual boot; I assume Xubuntu with ?, but tell us all that you can.
I also see mention of crouton in your output so are we dealing with a chromebook?  If so I am right out of my depths.

---

