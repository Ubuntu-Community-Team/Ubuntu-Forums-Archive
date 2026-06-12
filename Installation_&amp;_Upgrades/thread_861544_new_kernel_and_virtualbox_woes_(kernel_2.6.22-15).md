---
title: "new kernel and virtualbox woes (kernel 2.6.22-15)"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by |{urse on 2008-07-16
mmk lol I know virtualbox is universe and isn't directly supported or maintained by canonical but isn't this a bit of a showstopper? I have a few things that were pretty dependent on vbox. I know i can simply use the .14 kernel in grub but seriously what a pain. Okay done fuming :lolflag: the problem of course is there are no virtualbox-ose-modules-2.6.22-15-generic packages. So i figured mk lol w/e and went about the (usually easy) task of using module-assistant. (if anyone has a .deb for .15 modules pls hit me up now).

> kurse@kurse-desktop:~$ sudo module-assistant auto-install virtualbox-ose
Updated infos about 1 packages
Getting source for kernel version: 2.6.22-15-generic
Kernel headers available in /usr/src/linux-headers-2.6.22-15-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
download 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-ose-modules-2.6.22-14-generic
The following NEW packages will be installed:
  virtualbox-ose virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 5695kB/6012kB of archives.
After unpacking 19.3MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe virtualbox-ose 1.5.0-dfsg2-1ubuntu3 [5695kB]
Fetched 5695kB in 17s (329kB/s)                                                
Selecting previously deselected package virtualbox-ose-modules-2.6.22-14-generic.
(Reading database ... 185132 files and directories currently installed.)
Unpacking virtualbox-ose-modules-2.6.22-14-generic (from .../virtualbox-ose-modules-2.6.22-14-generic_6_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.0-dfsg2-1ubuntu3_i386.deb) ...
Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...


Updated infos about 1 packages
unpack 
Extracting the package tarball, /usr/src/virtualbox-ose.tar.bz2, please wait...
Target package file 
/usr/src/virtualbox-ose-modules-2.6.22-15-generic_1.5.0-dfsg2-1ubuntu3+2.6.22-1
5.56_i386.deb already exists, not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/virtualbox-ose-modules-2.6.22-15-generic_1.5.0-dfsg2-1ubuntu3+2.6.22-15.56_i386.deb 
dpkg: regarding .../virtualbox-ose-modules-2.6.22-15-generic_1.5.0-dfsg2-1ubuntu3+2.6.22-15.56_i386.deb containing virtualbox-ose-modules-2.6.22-15-generic:
 virtualbox-ose-modules-2.6.22-14-generic conflicts with virtualbox-ose-modules
  virtualbox-ose-modules-2.6.22-15-generic provides virtualbox-ose-modules and is to be installed.
dpkg: error processing /usr/src/virtualbox-ose-modules-2.6.22-15-generic_1.5.0-dfsg2-1ubuntu3+2.6.22-15.56_i386.deb (--install):
 conflicting packages - not installing virtualbox-ose-modules-2.6.22-15-generic
Errors were encountered while processing:
 /usr/src/virtualbox-ose-modules-2.6.22-15-generic_1.5.0-dfsg2-1ubuntu3+2.6.22-15.56_i386.deb

I: Direct installation failed, trying to post-install the dependencies

apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Anyone had luck with this?

---

### Post by sdennie on 2008-07-16
You could instead use the PUEL version from [www.virtualbox.org](www.virtualbox.org) (uninstall the OSE version first) and then use this to automatically build the driver on kernel updates: [http://ubuntuforums.org/showpost.php?p=5271094&postcount=7](http://ubuntuforums.org/showpost.php?p=5271094&postcount=7)

---

### Post by |{urse on 2008-07-18
Oh JOY! thx so much for that, ur a lifesaver.

---

### Post by |{urse on 2008-07-18
Oh man, this works beautifully..

---

### Post by dpinho on 2008-08-20
> **|{urse said:**
> mmk lol I know virtualbox is universe and isn't directly supported or maintained by canonical but isn't this a bit of a showstopper? I have a few things that were pretty dependent on vbox. I know i can simply use the .14 kernel in grub but seriously what a pain. Okay done fuming :lolflag: the problem of course is there are no virtualbox-ose-modules-2.6.22-15-generic packages. So i figured mk lol w/e and went about the (usually easy) task of using module-assistant. (if anyone has a .deb for .15 modules pls hit me up now).



Anyone had luck with this?


I had the same problem after updating the kernel and solved doing:

sudo dpkg --force-depends -r virtualbox-ose-modules-2.6.22-14-generic

before the module-assistant

---

