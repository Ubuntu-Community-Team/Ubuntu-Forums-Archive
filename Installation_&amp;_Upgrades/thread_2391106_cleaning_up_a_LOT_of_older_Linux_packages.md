---
title: "cleaning up a LOT of older Linux packages"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-05
i've noticed that a LOT of older Linux packages remain installed of various types, mostly images.  the oldest appears to be 4.4.0-20 and the most recent appears to be 4.4.0-122.  is there some tool to remove all but the latest two versions and do all the necessary rebuilds (like grub config) or do i need to write my own (if so, what all should it do?).

---

### Post by Bashing-om on 2018-05-05
Skaperen; Hello -

> 
 there some tool to remove all but the latest two versions

Yep, that is the function of autoremove:
```

sudo apt autoremove

```

autoremove is also a part of the unattended-upgrade package and can be configured .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Skaperen on 2018-05-06
_sudo apt -y autoremove_ removed 7 of them but left most of them.  the ones it removed were recent one.

---

### Post by oldfred on 2018-05-06
Are the old files from before an upgrade?
Is so, they may not even be in dpkg to be removed. Generally you only want to use dpkg to remove installed files as then you get it out of sync. And bits of files may be in various places. Part of why I prefer clean installs as then you have done the equivalent of a major houseclean.

Some things & places to check.

 # What's present in /boot?
ls /boot 
   # What's in the grub menu?
grep initrd /boot/grub/grub.cfg | uniq 
   # What's installed according to the package manager? ii installed
dpkg -l linux-image* 
   # Which kernels is initramfs-tools aware of?
ls /var/lib/initramfs-tools 
   Use dpkg -S to see which .dkms files were not placed by the package manager
dpkg -S /full/path/to/file
Only use rm on files not in dpkg
dpkg -S /lib/modules | sed s/:.\*//
uname --kernel-release
 Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 ll /var/cache/apt/archives
kernel house clean
ll /usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)
in /boot by version: abi, config, initrd.img, vmlinuz

---

### Post by Skaperen on 2018-05-07
what i did was "_apt-get update && apt-get -y upgrade_" about every week or so for the past couple years.  i suspect every time there was a kernel upgrade, one of these packges was added.  i used dpkg only to run a "_dpkg -l_" to list packages.  i discovered all these Linux packages this way. there are about 80 .deb files in _/var/cache/apt/archives_ but none of the Linux .deb files are there.

```
lt1/forums /home/forums 3> al /var/lib/initramfs-tools
total 16
-rw-r--r-- 1 root root 77 Apr 13 01:56 4.4.0-119-generic
-rw-r--r-- 1 root root 77 Apr 23 19:25 4.4.0-121-generic
-rw-r--r-- 1 root root 76 Mar 10 00:45 4.4.0-28-generic
-rw-r--r-- 1 root root 76 Mar 10 00:44 4.4.0-36-generic
```

i have 2 commands i list files with: al = "ls -Al" and dl = "ls -dl". for a multi-column list i just use "ls".  so it looks like there are 4 versions that _initramfs-tools_ knows about. a closer look at the output of "_dpkg -l_" and i see most of them are "rc" instead of "ii".  so i think i should get all those names and do a purge to clear out leftover config files.

```
dpkg -l|egrep '^rc '|field 2|egrep '^linux'|wc -l
80
lt1/root /root 6# 
```

so ...

```
lt1/root /root 6# apt-get purge -y $(dpkg -l|egrep '^rc '|field 2|egrep '^linux')
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-101-generic* linux-image-4.4.0-103-generic* linux-image-4.4.0-104-generic* linux-image-4.4.0-108-generic* linux-image-4.4.0-109-generic*
  linux-image-4.4.0-112-generic* linux-image-4.4.0-116-generic* linux-image-4.4.0-21-generic* linux-image-4.4.0-22-generic* linux-image-4.4.0-24-generic*
  linux-image-4.4.0-31-generic* linux-image-4.4.0-34-generic* linux-image-4.4.0-38-generic* linux-image-4.4.0-42-generic* linux-image-4.4.0-45-generic*
  linux-image-4.4.0-47-generic* linux-image-4.4.0-51-generic* linux-image-4.4.0-53-generic* linux-image-4.4.0-57-generic* linux-image-4.4.0-59-generic*
  linux-image-4.4.0-62-generic* linux-image-4.4.0-63-generic* linux-image-4.4.0-64-generic* linux-image-4.4.0-66-generic* linux-image-4.4.0-70-generic*
  linux-image-4.4.0-71-generic* linux-image-4.4.0-72-generic* linux-image-4.4.0-75-generic* linux-image-4.4.0-78-generic* linux-image-4.4.0-79-generic*
  linux-image-4.4.0-81-generic* linux-image-4.4.0-83-generic* linux-image-4.4.0-87-generic* linux-image-4.4.0-89-generic* linux-image-4.4.0-91-generic*
  linux-image-4.4.0-92-generic* linux-image-4.4.0-93-generic* linux-image-4.4.0-96-generic* linux-image-4.4.0-97-generic* linux-image-4.4.0-98-generic*
  linux-image-extra-4.4.0-101-generic* linux-image-extra-4.4.0-103-generic* linux-image-extra-4.4.0-104-generic* linux-image-extra-4.4.0-108-generic*
  linux-image-extra-4.4.0-109-generic* linux-image-extra-4.4.0-112-generic* linux-image-extra-4.4.0-116-generic* linux-image-extra-4.4.0-21-generic*
  linux-image-extra-4.4.0-22-generic* linux-image-extra-4.4.0-24-generic* linux-image-extra-4.4.0-31-generic* linux-image-extra-4.4.0-34-generic*
  linux-image-extra-4.4.0-38-generic* linux-image-extra-4.4.0-42-generic* linux-image-extra-4.4.0-45-generic* linux-image-extra-4.4.0-47-generic*
  linux-image-extra-4.4.0-51-generic* linux-image-extra-4.4.0-53-generic* linux-image-extra-4.4.0-57-generic* linux-image-extra-4.4.0-59-generic*
  linux-image-extra-4.4.0-62-generic* linux-image-extra-4.4.0-63-generic* linux-image-extra-4.4.0-64-generic* linux-image-extra-4.4.0-66-generic*
  linux-image-extra-4.4.0-70-generic* linux-image-extra-4.4.0-71-generic* linux-image-extra-4.4.0-72-generic* linux-image-extra-4.4.0-75-generic*
  linux-image-extra-4.4.0-78-generic* linux-image-extra-4.4.0-79-generic* linux-image-extra-4.4.0-81-generic* linux-image-extra-4.4.0-83-generic*
  linux-image-extra-4.4.0-87-generic* linux-image-extra-4.4.0-89-generic* linux-image-extra-4.4.0-91-generic* linux-image-extra-4.4.0-92-generic*
  linux-image-extra-4.4.0-93-generic* linux-image-extra-4.4.0-96-generic* linux-image-extra-4.4.0-97-generic* linux-image-extra-4.4.0-98-generic*
0 upgraded, 0 newly installed, 80 to remove and 53 not upgraded.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 444759 files and directories currently installed.)
Removing linux-image-4.4.0-101-generic (4.4.0-101.124) ...
Purging configuration files for linux-image-4.4.0-101-generic (4.4.0-101.124) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
...
```
and now most of them are gone.
```
lt1/root /root 7# dpkg -l|fgrep linux
ii  console-setup-linux                 1.108ubuntu15.3        all                    Linux specific part of console-setup
ii  libselinux1:amd64                   2.4-3build2            amd64                  SELinux runtime shared libraries
ii  libv4l-0:amd64                      1.10.0-1               amd64                  Collection of video4linux support libraries
ii  libv4lconvert0:amd64                1.10.0-1               amd64                  Video4linux frame format conversion library
ii  linux-base                          4.0ubuntu1             all                    Linux image base package
ii  linux-firmware                      1.157.17               all                    Firmware for Linux kernel drivers
ii  linux-generic                       4.4.0.121.127          amd64                  Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-119             4.4.0-119.143          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-119-generic     4.4.0-119.143          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-121             4.4.0-121.145          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-121-generic     4.4.0-121.145          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28              4.4.0-28.47            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic      4.4.0-28.47            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36              4.4.0-36.55            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic      4.4.0-36.55            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic               4.4.0.121.127          amd64                  Generic Linux kernel headers
ii  linux-image-4.4.0-119-generic       4.4.0-119.143          amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-121-generic       4.4.0-121.145          amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic        4.4.0-28.47            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic        4.4.0-36.55            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-119-generic 4.4.0-119.143          amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-121-generic 4.4.0-121.145          amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic  4.4.0-28.47            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic  4.4.0-36.55            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                 4.4.0.121.127          amd64                  Generic Linux kernel image
ii  linux-libc-dev:amd64                4.4.0-122.146          amd64                  Linux Kernel Headers for development
ii  linux-sound-base                    1.0.25+dfsg-0ubuntu5   all                    base package for ALSA and OSS sound systems
ii  linuxvnc                            0.9.10-2               amd64                  VNC server to allow remote access to a tty
ii  pptp-linux                          1.8.0-1                amd64                  Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                            3:6.03+dfsg-11ubuntu1  amd64                  collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                     3:6.03+dfsg-11ubuntu1  all                    collection of bootloaders (common)
ii  syslinux-legacy                     2:3.63+dfsg-2ubuntu8   amd64                  Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                          2.27.1-6ubuntu3.4      amd64                  miscellaneous system utilities
lt1/root /root 8#
```

---

