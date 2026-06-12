---
title: "kernel with switcheroo"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by padab on 2012-01-13
Hi all.
I have laptop asus k53t with two graphics card radeon.
Need to switch between them.
I build kernle 2.6.39.4 with vgaswitcheroo on ubuntu 10.4 x64.
But switcheroo don't work. Help please.
Info:
lspci | grep VGA
> 00:01.0 VGA compatible controller: ATI Technologies Inc Device 9647
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6741
grep -i switcheroo /boot/config-2.6.*
> /boot/config-2.6.39.4-custom:CONFIG_VGA_SWITCHEROO=y
grub
> ...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
..

cat sys/kernel/debug/vgaswitcheroo/switch
> cat: sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
in rc.local

> chown padab:padab /sys/kernel/debug/vgaswitcheroo/switch

 in /etc/fstab 

> none /sys/kernel/debug debugfs defaults 0 0

installed AMD Catalyst 11.11 Proproetary Linux x86 display driver
in /etc/modprobe.d/radeon-kms.conf
> options radeon modeset=1

don't have radeon in modprobe blacklist's
debugfs mounted
xorg.conf don't exist, maybe this is a problem?
Sorry my bad English. Thanks.

---

### Post by dE_logics on 2012-01-13
I'm not sure, but unlike with Nvidia, you must have a physical switch or a Bios option to change between graphics cards -- this this very simple comparatively.

---

### Post by padab on 2012-01-13
no function in the BIOS to switch the cards :(
and button too(

---

### Post by padab on 2012-01-13
I generated xorg.conf he normal? may be change driver to radion?
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSectio

**UPD**
when i change fglrx to radion ubuntu run with low graphics mode

---

