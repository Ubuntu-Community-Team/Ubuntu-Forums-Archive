---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by troseph on 2007-06-30
Whenever I install any application I get this:

```

Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1

```

I am running kernel version 2.6.20-15-generic. Can anyone help?

---

### Post by troseph on 2007-06-30
So should I just re-install Ubuntu??

---

### Post by bapoumba on 2007-07-01
The current feisty kernel is 2.6.20-16-generic. Why are you running the -15?
Please try:
```
sudo aptitude update
suso aptitude dist-upgrade
```

---

### Post by troseph on 2007-07-02
That did nothing. It returned that it was up to date. But it's still showing I'm running 15. That is the problem. The updater is broken, like it says in the first post.

---

### Post by bapoumba on 2007-07-03
Hmm. Do you have the option to boot on the -16 kernel from grub menu?

From the -15 kernel, have you tried:
```
sudo dpkg --configure -a
```

---

### Post by troseph on 2007-07-03
Nope. The problem occurred while I was trying to upgrade to -16. :)

---

### Post by troseph on 2007-07-03
I ran the command you gave me, it returned nothing. I tried running automatic updates and nothing showed up. I checked grub and there is only the option for -15 and I double checked, I am running -15. I think something is broken with automatic update. Is there a manual way to get updates working?

---

### Post by bapoumba on 2007-07-04
Hmm...
Could you please post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by troseph on 2007-07-04
Sure thing. Thanks for all the help btw.. 
```

# 
# deb cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main

# deb cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# The Ubuntu Studio Repository

deb http://archive.ubuntustudio.org/ubuntustudio feisty main

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://soulmachine.net/breezy/ unstable/
deb http://ubuntu.davromaniak.eu feisty-depomaniak all
deb-src http://ubuntu.davromaniak.eu feisty-depomaniak all

```

---

### Post by bapoumba on 2007-07-04
You have a breezy repo in your sources.list.
Please comment that line:
```
sudo nano -B /etc/apt/sources.list
```
nano is a small text editor.

Go to that line:
**deb [http://soulmachine.net/breezy/](http://soulmachine.net/breezy/) unstable/**
and add a # at the beginning, it should look like this:
**# deb [http://soulmachine.net/breezy/](http://soulmachine.net/breezy/) unstable/**
That should be enough. I would also **comment all the non-ubuntu repos** you have, just for now and until your system is up to date. You can put them back after.

Save the file with CTRL-O and exit nano with CTRL-X

```
run sudo aptitude update
```

if no more errors are present, run:
```
sudo aptitude dist-upgrade
```

---

### Post by troseph on 2007-07-07
Now I am not getting the error when I install apps, but I still am unable to get that newer kernel version.

---

### Post by bapoumba on 2007-07-08
Could you please post the error to the dist-upgrade, and the output to:
```
uname -a
```

---

### Post by troseph on 2007-07-10
When I do dist-upgrade it doesn't give the error anymore. It says: 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```


uname -a returns:

```

Linux troseph-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

---

### Post by bapoumba on 2007-07-10
Hmm, could you post the output to:
```
cat /boot/grub/menu.lst
```

---

### Post by troseph on 2007-07-11
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5f025a68-7b27-4a35-bae9-1fd474aab192 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash noapic acpi=off

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5f025a68-7b27-4a35-bae9-1fd474aab192 ro quiet splash noapic acpi=off
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5f025a68-7b27-4a35-bae9-1fd474aab192 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I know for 100% sure that the -16 kernel is not on my install. I know quite a bit about Linux.

---

### Post by bapoumba on 2007-07-12
> **troseph said:**
> 
I know for 100% sure that the -16 kernel is not on my install. I know quite a bit about Linux.
No problem, you probably know more than I do ;)

I really do not understand why the dist-upgrade does not pick up the -16 kernel...

I looked in ubuntustudio. Even if you are running the generic kernel, is there anything you or someone else can make of this?
> Also the linux-image-lowlatency kernel will be installed by default but will not be a depend of the meta. So you can remove it if you use a custom kernel and wont break the meta.

[https://wiki.ubuntu.com/UbuntuStudio/PackageList]("https://wiki.ubuntu.com/UbuntuStudio/PackageList")

You have all the default repos, the -16 kernel came up as a security update, so ubuntustudio is the only repo I see that could prevent you from getting it.
 ```
~$ apt-cache madison linux-image-2.6.20-16-generic
linux-image-2.6.20-16-generic | 2.6.20-16.29 | http://security.ubuntu.com feisty-security/main Packages
linux-source-2.6.20 | 2.6.20-16.29 | http://security.ubuntu.com feisty-security/main Sources

```

Edit: what does return:
```
~$ aptitude show linux-image-2.6.20-16-generic
```

---

### Post by troseph on 2007-07-16
That returns 
```

Package: linux-image-2.6.20-16-generic
State: not installed
Version: 2.6.20-16.29
Priority: optional
Section: base
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 71.3M
Depends: initramfs-tools (>= 0.36ubuntu6), coreutils | fileutils (>= 4.0),
         module-init-tools (>= 3.2.1-0ubuntu1)
Recommends: lilo (>= 19.1) | grub
Suggests: fdutils, linux-doc-2.6.20 | linux-source-2.6.20
Conflicts: hotplug (< 0.0.20040105-1)
Provides: fuse-module, ivtv-modules, kvm-modules-2, linux-image,
          linux-image-2.6, ndiswrapper-modules-1.9, rhcs-modules2-1
Description: Linux kernel image for version 2.6.20 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.20 on x86/x86_64. 
 
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update. 
 
 Supports Generic processors. 
 
 Geared toward desktop systems. 
 
 You likely do not want to install this package directly. Instead, install the
 linux-generic meta-package, which will ensure that upgrades work correctly, and
 that supporting packages are also installed.


```

---

### Post by troseph on 2007-07-16
When I try this:
```

troseph@troseph-laptop:~$ sudo apt-get install linux-image-2.6.20-16-generic

```

I get this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  linux-doc-2.6.20 linux-source-2.6.20
Recommended packages:
  lilo grub
The following NEW packages will be installed:
  linux-image-2.6.20-16-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.8MB of archives.
After unpacking 71.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-image-2.6.20-16-generic
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.20-16-generic.
(Reading database ... 106634 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
Done.
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bapoumba on 2007-07-17
Please install **linux-image-generic** and **linux-headers-generic** (if you need the headers), or more simply **linux-generic**.
I did not instal linux-generic myself because I do not want the restricted modules, so I got the two previous ones.

Sorry I did not think of this previously...

---

### Post by troseph on 2007-07-17
I'm right back where i was in the beginning. :(

This is what it returned: when I try to install any of those previously mentioned.


```

Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.20-16-generic.
(Reading database ... 106672 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.20.16.28.1_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.20-16-generic.
Unpacking linux-restricted-modules-2.6.20-16-generic (from .../linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-generic.
Unpacking linux-restricted-modules-generic (from .../linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb) ...
Selecting previously deselected package linux-generic.
Unpacking linux-generic (from .../linux-generic_2.6.20.16.28.1_i386.deb) ...
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bapoumba on 2007-07-17
Hmm...
Did you comment the davromaniac repos?
And may be the ubuntustudio ones, in the mean time.

Try to comment them out, and run
```
sudo aptitude update
```
Before you try to install the generic packages again.

---

### Post by troseph on 2007-07-18
No change. I am beginning to think that I might just reinstall. It still returns the same error even after cleaning up my sources.list. Something about Ubuntu 7.04 doesn't like my macbook. In 6.10 it ran great. With 7.04 my mouse and keyboard never work (I already have a thread open about those so don't worry. :) ) and updates are borked.

---

### Post by bapoumba on 2007-07-18
Just try 
```
sudo aptitude update
sudo aptitude dist-upgrade
```
One more time (sometimes, kernel packages need a dist-upgrade). But I'm not quite convinced now...

---

### Post by Pstevens on 2007-07-20
Hi, Troseph and Bapoumba.  Did you ever solve this one?  We have the same problem (my son and I - both newbies).  I have been searching Ubuntu forums and finally found your thread.  

Richard

---

### Post by troseph on 2007-07-21
I'm still getting the same error. :'( How messed up is that?

---

### Post by troseph on 2007-07-21
Oh no. I tried installing vmware-player and now I am getting the same error...

```

E: Sub-process /usr/bin/dpkg returned an error code (1

```

---

### Post by bapoumba on 2007-07-22
Hmm.. Not good :/
Have you looked in the Mac sub-forums ?

---

### Post by troseph on 2007-07-22
Yeah... I'm going to back up my documents and re-install 6.10 then upgrade... 7.04 doesn't play well with first generation MacBooks I guess.

---

### Post by cbaumann on 2007-07-24
Hey,

I kind of had the same problem. Wasn't quite the same packages though, but still the same error code.

Here's what I did:

I removed the corrupted packages, in your case >  linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic using synaptic, and then reinstalled them, using synaptic as well.

You might try that.

---

