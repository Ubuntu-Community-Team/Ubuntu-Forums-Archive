---
title: "apt-get dist-uprade ERRORS"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Lazrum on 2008-08-26
upgrades with apt were successful at one point until the below packages were attempted to be upgraded. I've tried researching some of the random error messages throughout the output but couldn't find much of anything. Maybe someone can give me a better search criteria? 

Also, maybe unrelated but "ping" doesn't work anymore:

root@(none):~# ping 192.168.0.1
Illegal instruction (core dumped)


apt errors:


jason@(none):~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-headers-2.6.22-15 linux-headers-2.6.22-15-generic linux-image-2.6.22-15-generic linux-libc-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 27.6MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-image-2.6.22-15-generic 2.6.22-15.58 [18.5MB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-headers-2.6.22-15 2.6.22-15.58 [7777kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-headers-2.6.22-15-generic 2.6.22-15.58 [582kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-libc-dev 2.6.22-15.58 [654kB]
Fetched 27.6MB in 19m52s (23.1kB/s)
(Reading database ... 132233 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-15-generic 2.6.22-15.56 (using .../linux-image-2.6.22-15-generic_2.6.22-15.58_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-15-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
dpkg: --compare-versions takes three arguments: <version> <relation> <version>

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
User postrm hook script [/sbin/update-grub] exited with value 139
Preparing to replace linux-headers-2.6.22-15 2.6.22-15.56 (using .../linux-headers-2.6.22-15_2.6.22-15.58_all.deb) ...
Unpacking replacement linux-headers-2.6.22-15 ...
Preparing to replace linux-headers-2.6.22-15-generic 2.6.22-15.56 (using .../linux-headers-2.6.22-15-generic_2.6.22-15.58_i386.deb) ...
Unpacking replacement linux-headers-2.6.22-15-generic ...
Preparing to replace linux-libc-dev 2.6.22-15.56 (using .../linux-libc-dev_2.6.22-15.58_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-image-2.6.22-15-generic (2.6.22-15.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Segmentation fault (core dumped)
/usr/sbin/mkinitramfs: 279: cannot create : Directory nonexistent
update-initramfs: failed for /boot/initrd.img-2.6.22-15-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-15-generic:
 linux-ubuntu-modules-2.6.22-15-generic depends on linux-image-2.6.22-15-generic; however:
  Package linux-image-2.6.22-15-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.22-15-generic; however:
  Package linux-image-2.6.22-15-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.22-15-generic; however:
  Package linux-ubuntu-modules-2.6.22-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-15-generic:
 linux-restricted-modules-2.6.22-15-generic depends on linux-image-2.6.22-15-generic; however:
  Package linux-image-2.6.22-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.22-15-generic; however:
  Package linux-restricted-modules-2.6.22-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Setting up openssh-server (1:4.6p1-5ubuntu0.5) ...
Segmentation fault (core dumped)
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 139
Setting up linux-headers-2.6.22-15 (2.6.22-15.58) ...
Setting up linux-headers-2.6.22-15-generic (2.6.22-15.58) ...

Setting up linux-libc-dev (2.6.22-15.58) ...
Errors were encountered while processing:
 linux-image-2.6.22-15-generic
 linux-ubuntu-modules-2.6.22-15-generic
 linux-image-generic
 linux-restricted-modules-2.6.22-15-generic
 linux-restricted-modules-generic
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

