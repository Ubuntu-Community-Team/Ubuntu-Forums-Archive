---
title: "Trying to get syslinux to work with preseed"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by sportman1280 on 2008-07-11
We use syslinux to boot debian-installer.  which then uses a preseed to automatically install ubuntu, and the unique packages we use on our systems.

I am trying to create a menu system that allows you to pick with preseed you want to use.  I have followed the instructions i could find, but after a day of struggling it just doesn't seem to be working the way everyone describes it.

Here is the syslinux.cfg
```
MENU TITLE LOUD v6

LABEL lcsee
	menu label ^LCSEE
	menu default
	kernel linux
	append debian-installer/locale=en_US console-setup/layout=USA console-setup/ask_detect=false console-setup/variant=USA debconf/priority=critical preseed/file=/cdrom/preseed/lcsee.seed initrd=/initrd.gz ramdisk_size=16432 root=/dev/ram rw quiet --

LABEL hd
 	MENU LABEL ^Boot from first hard disk
	localboot 0x80
	append -

DISPLAY syslinux.txt
PROMPT 1
TIMEOUT 300
ONTIMEOUT lcsee

F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
```

I have also uploaded the cd image in a bz2 file  onto my server:
[http://www.petederemer.com/lbm.tar.bz2](http://www.petederemer.com/lbm.tar.bz2)

Can anyone help me?

---

### Post by sportman1280 on 2008-07-14
Can anyone help?

---

