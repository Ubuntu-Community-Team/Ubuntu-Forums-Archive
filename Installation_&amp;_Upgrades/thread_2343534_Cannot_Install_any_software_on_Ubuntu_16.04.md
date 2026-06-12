---
title: "Cannot Install any software on Ubuntu 16.04"
date: 2016-11-17
forum: Installation &amp; Upgrades
---

### Post by Mohan_Yadav on 2016-11-17
I am trying to install mongodb but getting this error.

```
prince@trimax:~$ sudo apt-get install mongodb-org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mongodb-org is already the newest version (3.2.10).
The following packages were automatically installed and are no longer required:
  libcdaudio1 libdirectfb-1.2-9 libenca0 libmbim-glib4 libmbim-proxy libmpcdec6 libqmi-glib1 libqmi-proxy libslv2-9 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-image-4.4.0-31-generic linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic linux-image-4.4.0-43-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-43-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up dbus (1.10.6-1ubuntu3.1) ...
A reboot is required to replace the running dbus-daemon.
Please reboot the system when convenient.
insserv: warning: script 'K10runlcactivator' missing LSB tags and overrides
insserv: warning: script 'runlcactivator' missing LSB tags and overrides
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service plymouth and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service cups-browsed at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service runlcactivator and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service runlcactivator if started
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up udev (229-4ubuntu12) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
insserv: warning: script 'K10runlcactivator' missing LSB tags and overrides
insserv: warning: script 'runlcactivator' missing LSB tags and overrides
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service plymouth and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service cups-browsed at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service runlcactivator and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service runlcactivator if started
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bluez:i386:
 bluez:i386 depends on udev (>= 170-1); however:
  Package udev is not configured yet.
 bluez:i386 depends on dbus; however:
  Package dbus is not configured yet.


dpkg: error processing package bluez:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up whoopsie (0.2.52.2) ...
insserv: warning: script 'K10runlcactivator' missing LSB tags and overrides
insserv: warning: script 'runlcactivator' missing LSB tags and overrides
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service plymouth and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service cups-browsed at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service runlcactivator and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service runlcactivator if started
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting runlcactivator depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of accountsservice:
 accountsservice depends on dbus; however:
  Package dbus is not configured yet.


dpkg: error processing package accountsservice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on dbus; however:
  Package dbus is not configured yet.


dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.


dpkg: error processing package dbus-x11 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
No apport report written because MaxReports is reached already
                                                              update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
Errors were encountered while processing:
 dbus
 udev
 bluez:i386
 whoopsie
 accountsservice
 libpam-systemd:amd64
 dbus-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
prince@trimax:~$ 



```

---

### Post by ian-weisser on 2016-11-17
Please show us the output of the following command:
```
dpkg -S /etc/init.d/runlcactivator
```

That will tell you which package is causing the problem.
If it's not an essential package, uninstall it.

---

