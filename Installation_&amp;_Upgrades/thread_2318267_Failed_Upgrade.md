---
title: "Failed Upgrade?"
date: 2016-03-24
forum: Installation &amp; Upgrades
---

### Post by theglamourgroup123 on 2016-03-24
I tried upgrading from 12.04 LTS to 14.04 LTS. Its says that the upgrade finished but errors were encountered with printer-driver-gutenprint or something. Now I rebooted my Chromebook and went in the crosh shell and did sudo startunity, but says this: 

```
chronos@localhost / $ sudo startunityEntering /mnt/stateful_partition/crouton/chroots/precise...
A chroot setup script still exists inside the chroot.
The chroot may not be fully set up.
Would you like to finish the setup? [Y/n/d] y
Preparing chroot environment...
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:
printer-driver-gutenprint depends on libgutenprint2 (>= 5.2.10~pre2); however:
Version of libgutenprint2 on system is 5.2.8~pre1-0ubuntu2.1.
dpkg: error processing package printer-driver-gutenprint (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
printer-driver-gutenprint
Failed to complete chroot setup.
The chroot setup script may be broken. Your chroot is not fully configured.
Removing the chroot setup script. You may want to update your chroot again.
_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.10.18 [#1]("https://github.com/dnschneid/crouton/issues/1") SMP Thu Mar 10 05:45:38 PST 2016 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=1bafbe4d-a93e-3d41-be36-ea940fdb11e9/PARTNROFF=1 hashtree=PARTUUID=1bafbe4d-a93e-3d41-be36-ea940fdb11e9/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=0f5340f74cd923b0d348939e445ed16762560183 salt=a2b9f363ce95098ff7c8c444935eb0548b4a07cd3c08fe9bd826c96d21a6fce1" noinitrd vt.global_cursor_default=0 kern_guid=1bafbe4d-a93e-3d41-be36-ea940fdb11e9 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic

Build Date: 12 February 2015 02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Thu Mar 24 12:02:48 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
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
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
crouton: version unknown
release: unknown
architecture: unknown
xmethod: xorg
targets: unity
host: version 7834.60.0 (Official Build) stable-channel quawks 
kernel: Linux localhost 3.10.18 [#1]("https://github.com/dnschneid/crouton/issues/1") SMP Thu Mar 10 05:45:38 PST 2016 x86_64 x86_64 x86_64 GNU/Linux
freon: yes
No Chromium OS X server is available.
Running exit commands...
/usr/bin/xinit: connection to X server lost
waiting for X server to shut down Hangup
(EE) Server terminated successfully (0). Closing log file.
Unmounting /mnt/stateful_partition/crouton/chroots/precise...
```

Then I tried updating crouton: 

```
chronos@localhost / $ sudo sh -e ~/Downloads/crouton -n precise -u
Downloading latest crouton installer...
######################################################################## 100.0%
/usr/local/chroots/precise already exists; updating it...
Preparing chroot environment...
Installing brightness into the chroot...
Installing croutonpowerd into the chroot...
Installing croutonversion into the chroot...
Installing host-dbus into the chroot...
Installing host-x11 into the chroot...
Installing volume into the chroot... 
Installing pulseaudio-default.pa into the chroot...
Installing croutoncycle into the chroot...
Installing croutontriggerd into the chroot...
Installing croutonxinitrc-wrapper into the chroot...
Installing setres into the chroot...
Installing xinit into the chroot...
Installing xbindkeysrc.scm into the chroot...
Installing xorg-intel-sna.conf into the chroot...
Installing xserverrc into the chroot...
Installing xserverrc-xorg into the chroot...
Installing xserverrc-local.example into the chroot...
Installing startunity into the host...
Installing crouton-noroot into the chroot...
Installing startunity into the chroot...
Installing gnome-session-wrapper into the chroot...
Installing crouton-unity-autostart into the chroot...
Installing unity-autostart.desktop into the chroot...
Installing unity-profiled into the chroot...
Installing enter-chroot into the host...
Installing delete-chroot into the host...
Installing edit-chroot into the host...
Installing mount-chroot into the host...
Installing unmount-chroot into the host...
Installing crash_reporter_wrapper into the host...
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:
printer-driver-gutenprint depends on libgutenprint2 (>= 5.2.10~pre2); however:
Version of libgutenprint2 on system is 5.2.8~pre1-0ubuntu2.1.
dpkg: error processing package printer-driver-gutenprint (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
printer-driver-gutenprint
Failed to complete chroot setup.
Unmounting /mnt/stateful_partition/crouton/chroots/precise...
```

I'm really frustrated, help?

---

