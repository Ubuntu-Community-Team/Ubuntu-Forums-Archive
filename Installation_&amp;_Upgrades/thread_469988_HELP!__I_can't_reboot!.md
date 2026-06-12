---
title: "HELP!  I can't reboot!"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by jtgd on 2007-06-10
I can't reboot because my kernel image (linux-image-generic) is gone.
I'm running now, and I need to reboot but if I do, I will not be able
to and will have to install from disk.  There must be a way to repair
this!

Upgrading from Edgy to Feisty broke a few things.  One was that usbmgr
does not work -- I can no longer plug in a device and have it
auto-recognized.  The more troublesome problem is that if I try to
install it, it has a number of "dependencies" that it must satisfy
which includes ***deleting the kernel!***

So I am stuck now without a kernel, fearing a reboot which will leave me screwed.

When I now do **dpkg --configure -a** I get the following:
[INDENT]~ : dpkg --configure -a
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
frontend: cannot connect to X server
debconf: unable to initialize frontend: Kde
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.20-16.28 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.20-16.28 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
~ :  [/INDENT]

So I remove the existing linux-image-generic and try again with **apt-get install linux-image-generic**:

[INDENT]
~ : sudo apt-get install linux-image-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lockfile-progs
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.20-16-generic
Suggested packages:
  linux-doc-2.6.20 linux-source-2.6.20
Recommended packages:
  lilo grub
The following NEW packages will be installed:
  linux-image-2.6.20-16-generic linux-image-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.1MB of archives.
After unpacking 82.7MB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.20-16-generic.
(Reading database ... 177998 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.29_amd64.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.20.16.28.1_amd64.deb) ...
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
~ :  
[/INDENT]

Any ideas how I can get my system back?

(this is a dual Opteron system running 2.6.20-15-generic #2 SMP  x86_64 GNU/Linux)

---

