---
title: "How to install Ubuntu from hard drive (booting ISO?) ?"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by brynjarh on 2006-02-28
Anyone know how I can install Ubuntu without using a CD, floppy or USB stick? I got an ISO, two hard drives, GRUB and Ubuntu running and an urge to install Ubuntu Dapper Flight CD4. If it's possible we should have a howto somewhere if we don't already.

Some info on how Debian does it:
[http://www.us.debian.org/releases/stable/i386/ch02s02.html.en#id2465634]("http://www.us.debian.org/releases/stable/i386/ch02s02.html.en#id2465634")
[http://www.us.debian.org/releases/stable/i386/ch04s05.html.en]("http://www.us.debian.org/releases/stable/i386/ch04s05.html.en")
[http://www.us.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd]("http://www.us.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd")

---

### Post by lha on 2006-02-28
[QUOTE=brynjarh]Anyone know how I can install Ubuntu without using a CD, floppy or USB stick? I got an ISO, two hard drives, GRUB and Ubuntu running and an urge to install Ubuntu Dapper Flight CD4. If it's possible we should have a howto somewhere if we don't already.

Some info on how Debian does it:
[http://www.us.debian.org/releases/stable/i386/ch02s02.html.en#id2465634]("http://www.us.debian.org/releases/stable/i386/ch02s02.html.en#id2465634")
[http://www.us.debian.org/releases/stable/i386/ch04s05.html.en]("http://www.us.debian.org/releases/stable/i386/ch04s05.html.en")
[http://www.us.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd]("http://www.us.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd")[/QUOTE]

The procedure is almost identical to that of Debian. You need an internet connection to do this.

Copy files initrd.gz and linux to your /boot. Grab them from install/netboot/ubuntu-installer/i386 on install cd or [online.]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/ubuntu-installer/i386/") Add following lines to menu.lst:
Code:

title Install Ubuntu root (hd0,0) kernel /boot/linux vga=normal ramdisk_size=16384 root=/dev/rd/0 rw -- initrd /boot/initrd.gz

Change (hd0,0) to correct device. Restart and start installer.

---

### Post by brynjarh on 2006-03-01
Okay cool, I'm going to try this out then.

---

