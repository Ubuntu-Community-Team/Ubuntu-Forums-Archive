---
title: "Failure to upgrade ubuntu 8.04: broken dpkg/apt : cannot configure initramfs-tools"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by konstant@mail.ntua.gr on 2008-11-06
Problem was finally solved. Although the solution is very particular to my system's configuration, I still post it in case it can be of use to others. It boils down to the fact that in my system there was a 
/usr/local/bin/readlink
program different than the system's /bin/readlink (from an old latex distribution which I need to use)
Since /usr/local/bin was higher in my (root's) path, dpkg and subsequent scripts were using it istead of the intended one. The old readlink was not accepting the -f flag needed in the mkinitramfs script.

Solution:
=========
cd /usr/local/bin
mv readlink readlink.old
ln -s /bin/readlink .     (not necessary)

After that running dpkg --configure was smooth and now everything is OK for apt.
===========================================================================
Ubuntu 8.04 Linux kna2 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

hardware: 
Laptop DELL XPS M1330 IntelCore2 Duo T7250  @ 2.00GHz 
and 
Desktop with Pentium Intel Core2 Duo E8400  @ 3.00GHz
----------------------------------------------------------------------
After updating suddenly (2.6.24-16 -> 2.6.24-21) all my packages 
apt-get complains 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a'
that I have to run
 dpkg --configure -a
which I do (see output below). I tried to manually configure all misconfigured packages in the list below by downloading the .deb packages. It boils down that the dependencies point out to the configuration of the initramfs-tools package. Since the packages involved have to do with the kernel, I am afraid uninstalling e.g. linux-image-generic fearing of breaking the basic OS function.

I have not been able to fix dpkg/aptitude and I cannot install/upgrade any package anymore :-(

Is there any way fixing it without making a fresh installation?

------------------------------------------------------------------------------------
[root@kna2 dpkg]# dpkg --configure initramfs-tools
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
readlink: Need exactly one argument.
Try `access --help' for more information.
/usr/sbin/mkinitramfs: line 279: : No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

-------------------------------------------------------------------------------------------------
[root@kna2 dpkg]# dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 winbind service to resolve user and group information from Window
 smbclient a LanManager-like simple client for Unix
 linux-image-generic Generic Linux kernel image
 linux-image-2.6.24-21-generic Linux kernel image for version 2.6.24 on x86/x86
 linux-restricted-modules-generic Restricted Linux modules for generic kernels
 linux-generic Complete Generic Linux kernel

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools tools for generating an initramfs
 samba-common Samba common files used by both the server and the client
 foomatic-filters OpenPrinting printer support - filters
 ufw program for managing a netfilter firewall

The following packages are only half installed, due to problems during
installation. The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-ubuntu-modules-2.6.24-21-generic Ubuntu supplied Linux modules for versi
---------------------------------------------------------------
[root@kna2 dpkg]# ls -l /boot
total 21548
-rw-r--r-- 1 root root 422607 2008-04-10 19:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root 422781 2008-08-26 00:00 abi-2.6.24-21-generic
-rw-r--r-- 1 root root 79964 2008-04-10 19:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root 80073 2008-08-26 00:00 config-2.6.24-21-generic
drwxr-xr-x 2 root root 4096 2008-09-03 18:26 grub/
-rw-r--r-- 1 root root 7886746 2008-09-03 23:59 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7349268 2008-04-22 21:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 103204 2007-09-28 13:06 memtest86+.bin
-rw-r--r-- 1 root root 899892 2008-04-10 19:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 905365 2008-08-26 00:00 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 19:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1920376 2008-08-26 00:00 vmlinuz-2.6.24-21-generic
-------------------------------------------------------------------------
[root@kna2 dpkg]# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Setting up samba-common (3.0.28a-1ubuntu4.5) ...
readlink: Need exactly one argument.
Try `access --help' for more information.
ucf: Unable to determine The new file
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2.1) ...
readlink: Need exactly one argument.
Try `access --help' for more information.
ucf: Unable to determine The new file
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ufw (0.16.2.3) ...
readlink: Need exactly one argument.
Try `access --help' for more information.
ucf: Unable to determine The new file
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not installed.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
readlink: Need exactly one argument.
Try `access --help' for more information.
/usr/sbin/mkinitramfs: line 279: : No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
------------------------------------------------------------------------------------------------------
[root@kna2 dpkg]# apt-get update
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy Release.gpg
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy Release
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [64.2kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [14.9kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [38.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [6773B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8261B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 199kB in 1s (188kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
------------------------------------
[root@kna2 dpkg]# dpkg -i ~konstant/initramfs-tools_0.85eubuntu39.2_all.deb
(Reading database ... 211725 files and directories currently installed.)
Preparing to replace initramfs-tools 0.85eubuntu36 (using .../initramfs-tools_0.85eubuntu39.2_all.deb) ...
Unpacking replacement initramfs-tools ...
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
readlink: Need exactly one argument.
Try `access --help' for more information.
/usr/sbin/mkinitramfs: line 279: : No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
-----------------------------------------
[root@kna2 dpkg]# dpkg --configure linux-image-2.6.24-21-generic
dpkg: dependency problems prevent configuration of linux-image-2.6.24-21-generic:
 linux-image-2.6.24-21-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic

-------------------------------------------------------
[root@kna2 dpkg]# cd /var/lib/dpkg/
[root@kna2 dpkg]# ls parts triggers
parts:

triggers:
ldconfig  Lock  Unincorp  update-grub  update-initramfs
[root@kna2 dpkg]# ls parts triggers updates/
parts:

triggers:
ldconfig  Lock  Unincorp  update-grub  update-initramfs

updates/:
0000  0001  0002  0003  tmp.i

-------------------------------------------------------
Relevant lines of mkinitramfs, which I also attach
[root@kna2 dpkg]# cat -n /usr/sbin/mkinitramfs | tail -n 22 | head -n 15
   271	fi
   272	
   273	# Apply DSDT to initramfs
   274	if [ -e "${CONFDIR}/DSDT.aml" ]; then
   275		copy_exec "${CONFDIR}/DSDT.aml" /
   276	fi
   277	
   278	[ "${verbose}" = y ] && echo "Building cpio ${outfile} initramfs"
   279	(cd "${DESTDIR}" && find . | cpio --quiet --dereference -o -H newc | gzip >"${outfile}") || exit 1
   280	
   281	if [ -s "${__TMPCPIOGZ}" ]; then
   282		cat "${__TMPCPIOGZ}" >>"${outfile}" || exit 1
   283	fi
   284	
   285	if [ "${keep}" = "y" ]; then

-------------------------------------------------------
[7] 10:03am kna2:/etc/apt> ls /etc/apt/sources.list.d/
medibuntu.list
[10] 10:04am kna2:/etc/apt> grep ^deb sources.list
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
-------------------------------------------------------
[11] 10:04am kna2:/etc/apt> grep ^deb sources.list.d/medibuntu.list 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

-------------------------------------------------------

---

