---
title: "Dapper: Upgrading (or Downgrading) from Server to Desktop"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by vprasad on 2006-07-20
For whatever reason, the system administrators at my company would like to place a GUI on some of their underutilized Dapper Servers... preferrably with all of the amenities of the Dapper Desktop edition.  Any advice on how to accomplish this if they have the Servers installed and have a copy of the Desktop's ISO (but no CD burner) floating around?

---

### Post by geco on 2006-07-20
do you have an internet connection from the machine?
try
```

sudo apt-get install kubuntu-desktop

```
instead of kubuntu-desktop you can install
desktop-base
or edubuntu-desktop
or ubuntu-desktop
or xubuntu-desktop

---

### Post by vprasad on 2006-07-20
These boxes are not allowed on the internet... is there a workaround that uses mounting the Desktop ISO file to loopback (there's confusion as to how to access packages from Casper's filesystem.squashfs... or is there another file we should be investigating?)

---

### Post by geco on 2006-07-20
Ok, I think you will be able to install - for example ubuntu-desktop - mounting the iso
```

sudo mount -oloop /path/to/iso/ubuntu.iso /media/cdrom

```
and installing the deb package
```

dpkg -i /media/cdrom/path/to/packages/ubuntu-desktop_0.119_i386.deb

```

packages are in "pool" directory... but you have to find it because I don't remember its position, sorry!

to unmout simply do
```

sudo umount /media/cdrom

```

---

### Post by vprasad on 2006-07-20
Searching through the Desktop ISO yields only the following packages:

[INDENT]-r--r--r-- 12 root root 1406406 2006-02-25 10:04 binutils_2.16.1cvs20060117-1ubuntu2_i386.deb
-r--r--r-- 12 root root 20534 2005-11-11 10:20 bpalogin_2.0.2-6ubuntu1_i386.deb
-r--r--r-- 12 root root 6826 2005-07-21 11:40 build-essential_11.1_i386.deb
-r--r--r-- 36 root root 163130 2006-05-05 14:10 dpkg-dev_1.13.11ubuntu6_all.deb
-r--r--r-- 37 root root 421094 2005-04-17 21:15 eagle-usb-data_2.1.1-2_all.deb
-r--r--r-- 12 root root  87180 2005-04-17 21:15 eagle-usb-utils_2.1.1-2_i386.deb
-r--r--r-- 12 root root 93794 2006-03-16 12:05 fakeroot_1.5.6ubuntu2_i386.deb
-r--r--r-- 12 root root 1986820 2006-04-20 19:08 cpp-4.0_4.0.3-1ubuntu5_i386.deb
-r--r--r-- 12 root root 2271092 2006-04-20 19:08 g++-4.0_4.0.3-1ubuntu5_i386.deb
-r--r--r-- 12 root root  512640 2006-04-20 19:08 gcc-4.0_4.0.3-1ubuntu5_i386.deb
-r--r--r-- 12 root root 1470508 2006-04-20 19:08 libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb
-r--r--r-- 12 root root 30970 2006-03-16 04:04 cpp_4.0.3-1_i386.deb
-r--r--r-- 12 root root  1386 2006-03-16 04:04 g++_4.0.3-1_i386.deb
-r--r--r-- 12 root root  5048 2006-03-16 04:04 gcc_4.0.3-1_i386.deb
-r--r--r-- 12 root root 2821696 2006-05-21 15:08 libc6-dev_2.3.6-0ubuntu20_i386.deb
-r--r--r-- 12 root root  75278 2006-04-26 11:08 capiutils_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 12 root root 153702 2006-04-26 11:08 ipppd_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 12 root root 149216 2006-04-26 11:08 isdnutils-base_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 12 root root  49166 2006-04-26 11:08 isdnutils-xtools_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 12 root root  38584 2006-04-26 11:08 libcapi20-3_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 12 root root  27606 2006-04-26 11:08 libcapi20-dev_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 12 root root 102920 2006-04-26 11:08 pppdcapiplugin_3.8.2005-12-06-2ubuntu4_i386.deb
-r--r--r-- 13 root root 67932 2005-04-14 01:45 libatm1_2.4.1-17_i386.deb
-r--r--r-- 12 root root 1039142 2006-05-22 01:09 linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb
-r--r--r-- 11 root root 23310 2006-05-18 16:11 linux-headers-386_2.6.15.22_i386.deb
-r--r--r-- 12 root root 6894676 2006-05-23 14:08 linux-headers-2.6.15-23_2.6.15-23.39_i386.deb
-r--r--r-- 11 root root  852488 2006-05-23 14:08 linux-headers-2.6.15-23-386_2.6.15-23.39_i386.deb
-r--r--r-- 12 root root 132248 2006-03-07 19:04 linux-wlan-ng_0.2.3-1ubuntu7_i386.deb
-r--r--r-- 12 root root 286334 2005-12-16 22:05 make_3.80+3.81.b4-1_i386.deb
-r--r--r-- 12 root root 27650 2006-02-02 01:15 ndiswrapper-utils_1.8-0ubuntu2_i386.deb
-r--r--r-- 12 root root 40804 2005-11-16 19:15 pptp-linux_1.7.0-1ubuntu1_i386.deb
-r--r--r-- 13 root root 57832 2005-12-04 16:25 setserial_2.17-43_i386.deb
-r--r--r-- 12 root root 26864 2005-08-15 05:55 drdsl_1.2.0-0ubuntu1_i386.deb
-r--r--r-- 12 root root 23348 2006-05-18 16:11 avm-fritz-firmware_2.6.15.22_i386.deb
-r--r--r-- 12 root root 1204322 2006-05-29 09:09 avm-fritz-firmware-2.6.15-23_3.11+2.6.15.11-1_i386.deb[/INDENT]


Searching through the casper/filesystem.squashfs folder yields no .deb packages.



Is the **ubuntu-desktop_0.119_i386.deb** package hidden somewhere on the desktop CD? Is it compressed in another file or does it have a different name?

---

### Post by geco on 2006-07-20
I'm sorry, I have no idea :(

---

### Post by az on 2006-07-20
No.  The Desktop cd is a live filesystem, not a package repository.  You want to use the alternate cd.  You will be able to install the packages from there.

Also install linux-386.  The linux-server kernel does not support all desktop hardware.  Perhaps your mouse will not work otherwise.

---

