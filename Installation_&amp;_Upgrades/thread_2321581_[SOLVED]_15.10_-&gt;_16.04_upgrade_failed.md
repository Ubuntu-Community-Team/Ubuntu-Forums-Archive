---
title: "[SOLVED] 15.10 -&gt; 16.04 upgrade failed"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by nikaberidze on 2016-04-23
I tried automatic upgrade from Ubuntu 15.10 to 16.04, but it failed. When the upgrade was finished, I received a warning that my system might not be working. 

I rebooted, and in the upper right corner was a red circle with a white horizontal bar. When I clicked on it, it said: 

> An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Error Broken Count > 0' 
This usually means that your installed packages have unmet dependencies.

I have no idea what "the right-click menu" is or how to run Package Manager from it, and what exact command should I run with apt-get? I tried: 

```
 sudo dpkg --configure -a
```

and it told me that there were dependency problems with many packages and it could not repair these. Here is the output:


```
<Xubuntu box>~$ sudo dpkg --configure -a 
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 229-4ubuntu4); however:
  Version of systemd on system is 225-1ubuntu9.1.

dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udisks2:
 udisks2 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package udisks2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.
 network-manager depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing package network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of colord:
 colord depends on policykit-1 (>= 0.103); however:
  Package policykit-1 is not configured yet.

dpkg: error processing package colord (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd:
 systemd depends on libsystemd0 (= 225-1ubuntu9.1); however:
  Version of libsystemd0:amd64 on system is 229-4ubuntu4.
 initscripts (2.88dsf-59.3ubuntu2) breaks systemd (<< 228-5ubuntu3) and is installed.
  Version of systemd to be configured is 225-1ubuntu9.1.
 xserver-xorg-core (2:1.18.3-1ubuntu2) breaks systemd (<< 226-4~) and is installed.
  Version of systemd to be configured is 225-1ubuntu9.1.
 ifupdown (0.8.10ubuntu1) breaks systemd (<< 228-3~) and is installed.
  Version of systemd to be configured is 225-1ubuntu9.1.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on policykit-1; however:
  Package policykit-1 is not configured yet.
 update-manager depends on update-notifier; however:
  Package update-notifier is not configured yet.

dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpolkit-qt-1-1:amd64:
 libpolkit-qt-1-1:amd64 depends on libpam-systemd | consolekit; however:
  Package libpam-systemd:amd64 is not configured yet.
  Package consolekit is not installed.

dpkg: error processing package libpolkit-qt-1-1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing package software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rfkill:
 rfkill depends on systemd (>= 215-5ubuntu2); however:
  Package systemd is not configured yet.

dpkg: error processing package rfkill (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing package hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on rfkill; however:
  Package rfkill is not configured yet.
 xubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.

dpkg: error processing package xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-daemons:
 gvfs-daemons depends on udisks2; however:
  Package udisks2 is not configured yet.

dpkg: error processing package gvfs-daemons (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.16.3+repack0-1); however:
  Package hplip is not configured yet.

dpkg: error processing package printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd-sysv:
 systemd-sysv depends on systemd; however:
  Package systemd is not configured yet.

dpkg: error processing package systemd-sysv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra-pulse:amd64:
 libcanberra-pulse:amd64 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package libcanberra-pulse:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 1.1); however:
  Package network-manager is not configured yet.

dpkg: error processing package network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio (= 1:8.0-0ubuntu3); however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:amd64:
 gvfs:amd64 depends on gvfs-daemons (>= 1.28.1-1ubuntu1); however:
  Package gvfs-daemons is not configured yet.
 gvfs:amd64 depends on gvfs-daemons (<< 1.28.1-1ubuntu1.1~); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-sound:
 indicator-sound depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package indicator-sound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-core:
 xubuntu-core depends on rfkill; however:
  Package rfkill is not configured yet.

dpkg: error processing package xubuntu-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gvfs; however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on gvfs (= 1.28.1-1ubuntu1); however:
  Package gvfs:amd64 is not configured yet.
 gvfs-backends depends on gvfs-daemons (= 1.28.1-1ubuntu1); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of init:
 init depends on systemd-sysv | upstart-sysv; however:
  Package systemd-sysv is not configured yet.
  Package upstart-sysv is not installed.

dpkg: error processing package init (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on gvfs (= 1.28.1-1ubuntu1); however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpam-systemd:amd64
 policykit-1
 udisks2
 network-manager
 colord
 update-notifier
 systemd
 update-manager
 libpolkit-qt-1-1:amd64
 software-center
 rfkill
 ubuntu-standard
 hplip
 pulseaudio
 xubuntu-desktop
 ubuntu-release-upgrader-gtk
 gvfs-daemons
 printer-driver-postscript-hp
 systemd-sysv
 libcanberra-pulse:amd64
 network-manager-gnome
 pulseaudio-module-x11
 gvfs:amd64
 indicator-sound
 xubuntu-core
 brasero
 gvfs-backends
 init
 gvfs-fuse
```

From [another thread]("http://ubuntuforums.org/showthread.php?t=2148529") it seems I should next try: 

```
sudo apt-get install -f
```

I tried this command, and it seems that this fixed the broken dependencies. After rebooting, the red warning sign ("no entry" sign) was no longer shown. It would be nice to have it confirmed that this is sufficient, and that I don't need to do anything else now. It would also be nice to know the reason for this. Presumably something with software sources.

---

