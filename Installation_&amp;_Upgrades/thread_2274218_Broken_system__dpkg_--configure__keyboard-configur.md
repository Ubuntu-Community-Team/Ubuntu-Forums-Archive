---
title: "Broken system : dpkg --configure  keyboard-configuration ERROR"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by allaf on 2015-04-18
Hi,


My system got broken after i tried a 'do-release-update'  : I got some errors during the upgrade, and now the system is broken.

After reboot , xorg ids all ****ed up, i got a ****** definition etc..


'dpkg --configure -a' FAILS and i don't know what I can do.

Here is the trace : 
```

root@xxxx:/etc/apt# dpkg --configure  -a
[B]Setting up keyboard-configuration (1.108ubuntu4) ...
git: 'LC_CTYPE=en_US.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.108ubuntu4); however:
  Package keyboard-configuration is not configured yet.[/B]

dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-openchrome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-wacom:
 xserver-xorg-input-wacom depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-wacom depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-wacom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-radeon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-qxl:
 xserver-xorg-video-qxl depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-qxl depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-qxl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on xserver-xorg-core (>= 2:1.15.0.901); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.

dpkg: error processing package xserver-xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux; however:
  Package console-setup-linux is not configured yet.
 console-setup depends on keyboard-configuration (= 1.108ubuntu4); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sisusb:
 xserver-xorg-video-sisusb depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-sisusb depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-sisusb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tdfx:
 xserver-xorg-video-tdfx depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-tdfx depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-tdfx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cirrus:
 xserver-xorg-video-cirrus depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-r128:
 xserver-xorg-video-r128 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-r128 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-r128 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kbd:
 kbd depends on console-setup | console-setup-mini; however:
  Package console-setup is not configured yet.
  Package console-setup-mini is not installed.

dpkg: error processing package kbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-neomagic:
 xserver-xorg-video-neomagic depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-neomagic depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-neomagic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-modesetting:
 xserver-xorg-video-modesetting depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-modesetting depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-modesetting (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mga:
 xserver-xorg-video-mga depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mga depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-trident:
 xserver-xorg-video-trident depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-trident depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-trident (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mach64:
 xserver-xorg-video-mach64 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mach64 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mach64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-synaptics; however:
  Package xserver-xorg-input-synaptics is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-wacom; however:
  Package xserver-xorg-input-wacom is not configured yet.

dpkg: error processing package xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-mouse:
 xserver-xorg-input-mouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-mouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-mouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-331-updates:
 nvidia-331-updates depends on xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19; however:
  Package xorg-video-abi-11 is not installed.
  Package xorg-video-abi-12 is not installed.
  Package xorg-video-abi-13 is not installed.
  Package xorg-video-abi-14 is not installed.
  Package xorg-video-abi-15 is not installed.
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
  Package xorg-video-abi-19 is not installed.
 nvidia-331-updates depends on xserver-xorg-core; however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package nvidia-331-updates (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
 ubuntu-minimal depends on kbd; however:
  Package kbd is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ati:
 xserver-xorg-video-ati depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-r128; however:
  Package xserver-xorg-video-r128 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-mach64; however:
  Package xserver-xorg-video-mach64 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-radeon; however:
  Package xserver-xorg-video-radeon is not configured yet.

dpkg: error processing package xserver-xorg-video-ati (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-siliconmotion:
 xserver-xorg-video-siliconmotion depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-siliconmotion depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-siliconmotion (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-input-mouse; however:
  Package xserver-xorg-input-mouse is not configured yet.

dpkg: error processing package xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.7+7ubuntu2); however:
  Package xserver-xorg is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-331-updates-uvm:
 nvidia-331-updates-uvm depends on nvidia-331-updates (>= 331.113); however:
  Package nvidia-331-updates is not configured yet.

dpkg: error processing package nvidia-331-updates-uvm (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 keyboard-configuration
 console-setup-linux
 xserver-xorg-core
 xserver-xorg-video-openchrome
 xserver-xorg-video-vmware
 xserver-xorg-input-wacom
 xserver-xorg-video-radeon
 xserver-xorg-video-qxl
 xserver-xorg-video-savage
 xserver-xorg-video-fbdev
 xserver-xorg-input-evdev
 xserver-xorg
 console-setup
 xserver-xorg-input-synaptics
 xserver-xorg-video-vesa
 xserver-xorg-video-sisusb
 xserver-xorg-video-tdfx
 xserver-xorg-video-cirrus
 xserver-xorg-video-r128
 kbd
 xserver-xorg-video-neomagic
 xserver-xorg-video-modesetting
 xserver-xorg-video-mga
 xserver-xorg-video-s3
 xserver-xorg-video-trident
 xserver-xorg-video-intel
 xserver-xorg-video-mach64
 xserver-xorg-input-all
 xserver-xorg-input-mouse
 nvidia-331-updates
 ubuntu-minimal
 xserver-xorg-video-ati
 xserver-xorg-video-siliconmotion
 xserver-xorg-input-vmmouse
 xorg
 kubuntu-desktop
 nvidia-331-updates-uvm


```

apt-cache show keyboard-configuration
```

root@xxx:/etc/apt# apt-cache show keyboard-configuration
Package: keyboard-configuration
Priority: important
Section: utils
Installed-Size: 2587
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Original-Maintainer: Debian Install System Team <debian-boot@lists.debian.org>
Architecture: all
Source: console-setup
Version: 1.108ubuntu4
Replaces: console-setup (<< 1.47), console-setup-mini (<< 1.47)
Depends: debconf (>= 1.5.34), lsb-base (>= 4.1+Debian11ubuntu7), liblocale-gettext-perl, initscripts
Breaks: console-setup (<< 1.71), console-setup-mini (<< 1.47)
Filename: pool/main/c/console-setup/keyboard-configuration_1.108ubuntu4_all.deb
Size: 763548
MD5sum: 8ae479b717e4357e7c5dd9fd22c5646c
SHA1: 24ba81dd5ff4fbdca210e2b855a5a59459bbc360
SHA256: 948cc93019a78eb83b5a8bb0098e758e2f6c31c4e31599a3b80695d971e2879d
Description-en: system-wide keyboard preferences
 This package maintains the keyboard preferences in
 /etc/default/keyboard.  Other packages can use the information
 provided by this package in order to configure the keyboard on the
 console or in X Window.
Description-md5: 85ee5b58c8d635ba9041b52f81058494
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: minimal

```

Can anyone help me please ?

Thanks.

---

