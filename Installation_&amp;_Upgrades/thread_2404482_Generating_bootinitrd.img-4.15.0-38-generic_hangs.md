---
title: "Generating /boot/initrd.img-4.15.0-38-generic hangs"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by tdiguy2 on 2018-10-24
I have an issue trying to upgrade. When it gets to: [h=1][SIZE=1][FONT=Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]Generating /boot/initrd.img-4.15.0-38-generic it hangs and never completes.[/COLOR][/FONT][/SIZE][/h]
I have done the following from another board:
[COLOR=#333333][FONT=Ubuntu]4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Distributor ID: Ubuntu
Description: Ubuntu 18.04.1 LTS
Release: 18.04
Codename: bionic[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]df: /home/heath/thinclient_drives: Transport endpoint is not connected
/dev/sda2 455G 37G 395G 9% /
/dev/loop0 88M 88M 0 100% /snap/core/5548
/dev/loop2 128M 128M 0 100% /snap/yakyak/25
/dev/loop3 13M 13M 0 100% /snap/gnome-characters/124
/dev/loop4 15M 15M 0 100% /snap/gnome-logs/43
/dev/loop5 3.8M 3.8M 0 100% /snap/gnome-system-monitor/57
/dev/loop7 2.3M 2.3M 0 100% /snap/gnome-calculator/238
/dev/loop6 43M 43M 0 100% /snap/gtk-common-themes/701
/dev/loop1 128M 128M 0 100% /snap/yakyak/17
/dev/loop8 141M 141M 0 100% /snap/gnome-3-26-1604/70
/dev/loop9 15M 15M 0 100% /snap/gnome-logs/45
/dev/loop11 88M 88M 0 100% /snap/core/5328
/dev/loop10 128M 128M 0 100% /snap/yakyak/28
/dev/loop12 102M 102M 0 100% /snap/ubuntu-social-kit/3
/dev/sda1 511M 6.1M 505M 2% /boot/efi
/dev/sdc 2.7T 1.5T 1.1T 58% /media/emby
/dev/loop14 88M 88M 0 100% /snap/core/5662
/dev/loop13 141M 141M 0 100% /snap/gnome-3-26-1604/74[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]-rw-r--r-- 1 root root 1537610 Aug 27 10:45 abi-4.15.0-34-generic
-rw-r--r-- 1 root root 1537821 Sep 24 10:08 abi-4.15.0-36-generic
-rw-r--r-- 1 root root 1537997 Oct 10 05:20 abi-4.15.0-38-generic
-rw-r--r-- 1 root root 216905 Aug 27 10:45 config-4.15.0-34-generic
-rw-r--r-- 1 root root 216954 Sep 24 10:08 config-4.15.0-36-generic
-rw-r--r-- 1 root root 216983 Oct 10 05:20 config-4.15.0-38-generic
drwx------ 3 root root 4096 Dec 31 1969 efi
drwxr-xr-x 5 root root 4096 Oct 22 06:30 grub
-rw-r--r-- 1 root root 55565944 Sep 28 07:51 initrd.img-4.15.0-34-generic
-rw-r--r-- 1 root root 55577140 Oct 7 09:08 initrd.img-4.15.0-36-generic
-rw-r--r-- 1 root root 0 Oct 23 20:52 initrd.img-4.15.0-38-generic.new
-rw-r--r-- 1 root root 182704 Jan 28 2016 memtest86+.bin
-rw-r--r-- 1 root root 184380 Jan 28 2016 memtest86+.elf
-rw-r--r-- 1 root root 184840 Jan 28 2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root 0 Aug 27 10:45 retpoline-4.15.0-34-generic
-rw-r--r-- 1 root root 0 Sep 24 10:08 retpoline-4.15.0-36-generic
-rw-r--r-- 1 root root 0 Oct 10 05:20 retpoline-4.15.0-38-generic
-rw------- 1 root root 4044038 Aug 27 10:45 System.map-4.15.0-34-generic
-rw------- 1 root root 4046393 Sep 24 10:08 System.map-4.15.0-36-generic
-rw------- 1 root root 4046910 Oct 10 05:20 System.map-4.15.0-38-generic
-rw------- 1 root root 8269560 Aug 27 11:06 vmlinuz-4.15.0-34-generic
-rw------- 1 root root 8277752 Sep 24 11:54 vmlinuz-4.15.0-36-generic
-rw------- 1 root root 8277752 Oct 10 06:43 vmlinuz-4.15.0-38-generic

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]dpkg: error: need an action option[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

etc/apt/sources.list.d$ sudo dpkg --configure -a
Setting up linux-image-4.15.0-38-generic (4.15.0-38.41) ...
Processing triggers for linux-image-4.15.0-38-generic (4.15.0-38.41) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-38-generic
^Cdpkg: error processing package linux-image-4.15.0-38-generic
(--configure):
 installed linux-image-4.15.0-38-generic package post-installation script
subprocess was interrupted
Errors were encountered while processing:
 linux-image-4.15.0-38-generic[/FONT][/COLOR]

---

