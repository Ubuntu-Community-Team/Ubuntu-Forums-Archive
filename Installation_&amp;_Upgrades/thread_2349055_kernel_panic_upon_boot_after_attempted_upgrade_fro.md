---
title: "kernel panic upon boot after attempted upgrade from 14.04 to 16.04"
date: 2017-01-10
forum: Installation &amp; Upgrades
---

### Post by gobstopper2 on 2017-01-10
Hello Everyone,
I was following the other 14.04->16.04 upgrade problem thread ([https://ubuntuforums.org/showthread.php?t=2348948](https://ubuntuforums.org/showthread.php?t=2348948)),
but my problem occurs earlier on that in that post. If I let the machine try to boot normally with kernel 4.4.0-57 generic, I get an the following errors:
```

dump_stack+0x63/0x90
panic+0xd3/0x215
mount_block_root+0x201/0x294
mount_root+0x65/0x68
prepare_namespace+0x16a/0x1a2
kernel_init_freeable+0x1e9/0x212
? rest_init+0x80/0x80
kernel_init+0xe/0xe0
ret_from_fork+0x3f/0x70
? rest_init+0x80/0x80
Kernel Offset: disable
--[ end Kernel Panic - not synching: VFS: unable to mount root fs on unknown-block(0,0)

```
If I open the grub2 menu upon booting I can boot to the command line using an older kernel (e.g. 3.13.0-106-generic)

I booted off the liveCD (on USB), then mounted the drives and attempted what was suggested in the forum above:

sudo apt-get update:
```
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Ign:2 http://dl.google.com/linux/talkplugin/deb stable InRelease                       
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                             
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial InRelease                             
Hit:5 http://dl.google.com/linux/talkplugin/deb stable Release                         
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]            
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]             
Hit:8 http://archive.canonical.com/ubuntu xenial InRelease                             
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]         
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [449 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.0 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [441 kB]  
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [69.3 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [37.9 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [186 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [376 kB]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [25.4 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [31.8 kB]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [371 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [138 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [7,384 B]
Get:29 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [6,180 B]
Get:30 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:31 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:32 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:33 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 3,128 kB in 2s (1,266 kB/s)              
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done

```

I'm having troubles posting all my error messages in one post, so will attempt to spread out.

---

### Post by gobstopper2 on 2017-01-10
More:

sudo apt-get upgrade (not all of it was saved in Konsole buffer) but
```
 upstart depends on initscripts; however:
  Package initscripts is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.
 upstart depends on ifupdown (>= 0.6.10ubuntu5); however:
  Package ifupdown is not configured yet.

dpkg: error processing package upstart (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Setting up uuid-runtime (2.27.1-6ubuntu3.1) ...
insserv: warning: script 'S50shk_usb' missing LSB tags and overrides
insserv: There is a loop between service minidlna and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service minidlna if started
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service shk_usb and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service shk_usb if started
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: Starting load_daemon.sh depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package uuid-runtime (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of cmake:
 cmake depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cmake (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cmake-curses-gui:
 cmake-curses-gui depends on cmake (= 3.5.1-1ubuntu3); however:
  Package cmake is not configured yet.

dpkg: error processing package cmake-curses-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cmake-qt-gui:
 cmake-qt-gui depends on cmake (= 3.5.1-1ubuntu3); however:
  Package cmake is not configured yet.

dpkg: error processing package cmake-qt-gui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached alreadySetting up cups-browsed (1.8.3-2ubuntu3.1) ...

```

---

### Post by gobstopper2 on 2017-01-10
sudo apt-get upgrade (continued in part)
```

dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-36ubuntu3.6); however:
  Package grub-common is not configured yet.

No apport report written because MaxReports is reached alreadydpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured

No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-36ubuntu3.6); however:
  Package grub-common is not configured yet.


dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-36ubuntu3.6); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.02~beta2-36ubuntu3.6); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-36ubuntu3.6); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.3.11+dfsg-0ubuntu0.16.04.3); however:
  Package samba is not configured yet.

dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.3); however:
  Package winbind is not configured yet.

dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
 libpam-winbind:amd64 depends on winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.3); however:
  Package winbind is not configured yet.
...

```

---

### Post by gobstopper2 on 2017-01-10
some more info:
uname-r
```
 4.4.0-31-generic 
```

ls -l /boot
```
total 103708
-rw-r--r-- 1 root root  1166834 Dec  2 10:33 abi-3.13.0-105-generic
-rw-r--r-- 1 root root  1166834 Dec  6 09:22 abi-3.13.0-106-generic
-rw-r--r-- 1 root root  1243800 Dec  9 20:04 abi-4.4.0-57-generic
-rw-r--r-- 1 root root   166061 Dec  2 10:33 config-3.13.0-105-generic
-rw-r--r-- 1 root root   166061 Dec  6 09:22 config-3.13.0-106-generic
-rw-r--r-- 1 root root   189991 Dec  9 20:04 config-4.4.0-57-generic
drwxr-xr-x 3 root root     4096 Jan 10 11:55 efi
drwxr-xr-x 3 root root     4096 Dec 20 07:50 extlinux
drwxr-xr-x 5 root root     4096 Jan 10 12:15 grub
-rw-r--r-- 1 root root 31201892 Jan  6 15:43 initrd.img-3.13.0-105-generic
-rw-r--r-- 1 root root 31208176 Jan 10 11:19 initrd.img-3.13.0-106-generic
-rw-r--r-- 1 root root  9642719 Jan 10 11:25 initrd.img-4.4.0.57.60
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3399540 Dec  2 10:33 System.map-3.13.0-105-generic
-rw------- 1 root root  3399674 Dec  6 09:22 System.map-3.13.0-106-generic
-rw------- 1 root root  3875329 Dec  9 20:04 System.map-4.4.0-57-generic
-rw------- 1 root root  5849488 Dec  2 10:33 vmlinuz-3.13.0-105-generic
-rw------- 1 root root  5849616 Dec  6 09:22 vmlinuz-3.13.0-106-generic
-rw------- 1 root root  7067152 Dec  9 20:04 vmlinuz-4.4.0-57-generic


```

dpkg -l | grep linux-image
```
rc  linux-image-3.11.0-12-generic                   3.11.0-12.19                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-13-generic                   3.11.0-13.20                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-14-generic                   3.11.0-14.21                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-15-generic                   3.11.0-15.25                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-100-generic                  3.13.0-100.147                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-101-generic                  3.13.0-101.148                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-103-generic                  3.13.0-103.150                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-105-generic                  3.13.0-105.152                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic                   3.13.0-27.50                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                   3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic                   3.13.0-30.55                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-33-generic                   3.13.0-33.58                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-34-generic                   3.13.0-34.60                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic                   3.13.0-35.62                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-generic                   3.13.0-36.63                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-37-generic                   3.13.0-37.64                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic                   3.13.0-39.66                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                   3.13.0-40.69                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                   3.13.0-43.72                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                   3.13.0-44.73                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-45-generic                   3.13.0-45.74                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                   3.13.0-46.79                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                   3.13.0-48.80                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                   3.13.0-49.83                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-51-generic                   3.13.0-51.84                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-52-generic                   3.13.0-52.86                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-53-generic                   3.13.0-53.89                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-54-generic                   3.13.0-54.91                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                   3.13.0-55.94                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                   3.13.0-57.95                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                   3.13.0-58.97                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                   3.13.0-59.98                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                   3.13.0-61.100                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                   3.13.0-62.102                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-63-generic                   3.13.0-63.103                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-65-generic                   3.13.0-65.106                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-66-generic                   3.13.0-66.108                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-67-generic                   3.13.0-67.110                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-68-generic                   3.13.0-68.111                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-70-generic                   3.13.0-70.113                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-71-generic                   3.13.0-71.114                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-73-generic                   3.13.0-73.116                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-74-generic                   3.13.0-74.118                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-76-generic                   3.13.0-76.120                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-77-generic                   3.13.0-77.121                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic                   3.13.0-79.123                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-83-generic                   3.13.0-83.127                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic                   3.13.0-85.129                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic                   3.13.0-86.131                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-87-generic                   3.13.0-87.133                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-88-generic                   3.13.0-88.135                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-91-generic                   3.13.0-91.138                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-92-generic                   3.13.0-92.139                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-95-generic                   3.13.0-95.142                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-96-generic                   3.13.0-96.143                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-98-generic                   3.13.0-98.145                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-30-generic                    3.8.0-30.44                                   amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-31-generic                    3.8.0-31.46                                   amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
iU  linux-image-4.4.0-57-generic                    4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic             3.11.0-12.19 
rc  linux-image-extra-3.11.0-13-generic             3.11.0-13.20                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-14-generic             3.11.0-14.21                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-15-generic             3.11.0-15.25                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-100-generic            3.13.0-100.147                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-101-generic            3.13.0-101.148                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-103-generic            3.13.0-103.150                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-105-generic            3.13.0-105.152                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic            3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic             3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic             3.13.0-27.50                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic             3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic             3.13.0-30.55                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic             3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic             3.13.0-33.58                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic             3.13.0-34.60                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic             3.13.0-35.62                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic             3.13.0-36.63                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-37-generic             3.13.0-37.64                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic             3.13.0-39.66                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic             3.13.0-40.69                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic             3.13.0-43.72                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic             3.13.0-44.73                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic             3.13.0-45.74                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic             3.13.0-46.79                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic             3.13.0-48.80                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic             3.13.0-49.83                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic             3.13.0-51.84                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-52-generic             3.13.0-52.86                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic             3.13.0-53.89                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-54-generic             3.13.0-54.91                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic             3.13.0-55.94                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic             3.13.0-57.95                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic             3.13.0-58.97                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic             3.13.0-59.98                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic             3.13.0-61.100                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic             3.13.0-62.102                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic             3.13.0-63.103                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic             3.13.0-65.106                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic             3.13.0-66.108                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic             3.13.0-67.110                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic             3.13.0-68.111                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-70-generic             3.13.0-70.113                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-71-generic             3.13.0-71.114                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-73-generic             3.13.0-73.116                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic             3.13.0-74.118                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic             3.13.0-76.120                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-77-generic             3.13.0-77.121                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic             3.13.0-79.123                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic             3.13.0-83.127                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-85-generic             3.13.0-85.129                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-86-generic             3.13.0-86.131                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-87-generic             3.13.0-87.133                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-88-generic             3.13.0-88.135                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-91-generic             3.13.0-91.138                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-92-generic             3.13.0-92.139                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-93-generic             3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-95-generic             3.13.0-95.142                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-96-generic             3.13.0-96.143                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-98-generic             3.13.0-98.145                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-30-generic              3.8.0-30.44                                   amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-31-generic              3.8.0-31.46                                   amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-57-generic              4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                             4.4.0.57.60                                   amd64        Generic Linux kernel image

```

---

### Post by gobstopper2 on 2017-01-10
I will end with last bit, 

if I try:

sudo dpkg -P linux-headers-3.13.0-93-generic
```
dpkg: warning: ignoring request to remove linux-headers-3.13.0-93-generic which isn't installed

```

ls -al /usr/src/
```

total 44
drwxr-xr-x 11 root root 4096 Jan 10 10:05 .
drwxr-xr-x 16 root root 4096 Jan  6 14:29 ..
drwxr-xr-x  2 root root 4096 Jan  6 14:45 bbswitch-0.8
drwxr-xr-x 24 root root 4096 Dec  6 07:47 linux-headers-3.13.0-105
drwxr-xr-x  7 root root 4096 Dec  6 07:47 linux-headers-3.13.0-105-generic
drwxr-xr-x 24 root root 4096 Dec 20 07:48 linux-headers-3.13.0-106
drwxr-xr-x  7 root root 4096 Dec 20 07:48 linux-headers-3.13.0-106-generic
drwxr-xr-x 27 root root 4096 Jan  6 15:26 linux-headers-4.4.0-57
drwxr-xr-x  7 root root 4096 Jan  6 15:26 linux-headers-4.4.0-57-generic
drwxr-xr-x  4 root root 4096 Jan  6 14:32 nvidia-340-340.98
drwxr-xr-x 12 root root 4096 Jan  6 15:05 virtualbox-5.0.24

```

ls -al /lib/modules/
```
 drwxr-xr-x 12 root root 4096 Jan 10 10:07 .
drwxr-xr-x 29 root root 4096 Jan 10 10:05 ..
drwxr-xr-x  2 root root 4096 Apr 18  2014 3.11.0-12-generic
drwxr-xr-x  2 root root 4096 Apr 18  2014 3.11.0-13-generic
drwxr-xr-x  2 root root 4096 Apr 18  2014 3.11.0-17-generic
drwxr-xr-x  2 root root 4096 Apr 18  2014 3.11.0-18-generic
drwxr-xr-x  2 root root 4096 Apr 18  2014 3.11.0-19-generic
drwxr-xr-x  5 root root 4096 Jan  6 15:05 3.13.0-105-generic
drwxr-xr-x  5 root root 4096 Jan  6 15:05 3.13.0-106-generic
drwxr-xr-x  3 root root 4096 Aug 27  2014 3.13.0-24-generic
drwxr-xr-x  3 root root 4096 Aug 27  2014 3.13.0-32-generic
drwxr-xr-x  5 root root 4096 Jan  6 15:26 4.4.0-57-generic

```

ls -al /boot/
```
drwxr-xr-x  5 root root    16384 Jan 10 11:55 .
drwxr-xr-x 28 root root     4096 Jan 10 12:27 ..
-rw-r--r--  1 root root  1166834 Dec  2 10:33 abi-3.13.0-105-generic
-rw-r--r--  1 root root  1166834 Dec  6 09:22 abi-3.13.0-106-generic
-rw-r--r--  1 root root  1243800 Dec  9 20:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root   166061 Dec  2 10:33 config-3.13.0-105-generic
-rw-r--r--  1 root root   166061 Dec  6 09:22 config-3.13.0-106-generic
-rw-r--r--  1 root root   189991 Dec  9 20:04 config-4.4.0-57-generic
drwxr-xr-x  3 root root     4096 Jan 10 11:55 efi
drwxr-xr-x  3 root root     4096 Dec 20 07:50 extlinux
drwxr-xr-x  5 root root     4096 Jan 10 12:15 grub
-rw-r--r--  1 root root 31201892 Jan  6 15:43 initrd.img-3.13.0-105-generic
-rw-r--r--  1 root root 31208176 Jan 10 11:19 initrd.img-3.13.0-106-generic
-rw-r--r--  1 root root  9642719 Jan 10 11:25 initrd.img-4.4.0.57.60
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3399540 Dec  2 10:33 System.map-3.13.0-105-generic
-rw-------  1 root root  3399674 Dec  6 09:22 System.map-3.13.0-106-generic
-rw-------  1 root root  3875329 Dec  9 20:04 System.map-4.4.0-57-generic
-rw-------  1 root root  5849488 Dec  2 10:33 vmlinuz-3.13.0-105-generic
-rw-------  1 root root  5849616 Dec  6 09:22 vmlinuz-3.13.0-106-generic
-rw-------  1 root root  7067152 Dec  9 20:04 vmlinuz-4.4.0-57-generic

```

dpkg -l | grep linux-   (output is too long to include here)

If anyone has an idea of where to start(keeping in mind I'm following the other 14.04 to 16.04 thread), I'd be very appreciative!

---

