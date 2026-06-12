---
title: "Cannot install bcmwl package on new 10.04 USB install"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by edbas on 2010-08-03
I'm getting errors trying to install bcmwl (to get my wireless card to work).  This is a brand new install of 10.04 on a USB flash drive.  Any suggestions greatly appreciated 

See sequence below:

-- New 10.04 USB install created by Universal USB Installer
-- Booted, got message saying I should install proprietary drivers
-- Clicked on Hardware Drivers icon, selected Broadcom STA wireless driver
-- Received "SystemError: installArchives() failed"

Crash report said both "bcmwl-kernel-source" and "initramfs-tools" failed.

Attempted a manual install of the package:

ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 265 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.60.48.36+bdcom
Kernel:  2.6.32-21-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-21-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$

---

### Post by edbas on 2010-08-03
Update - I have now replicated this on two different USB sticks and two different computers.  I've also tried starting with the manual install (rather than the GUI tool).  Same results.  This is happening on a fresh install.  

Any suggestions greatly appreciated!

---

### Post by edbas on 2010-08-03
> **edbas said:**
> Update - I have now replicated this on two different USB sticks and two different computers.  I've also tried starting with the manual install (rather than the GUI tool).  Same results.  This is happening on a fresh install.  

Any suggestions greatly appreciated!
Update - this was solved with the workaround identified in Bug#557023 at [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023)

The issue was a broken link to the vmlinuz on persistent USB installs of 10.04.  The original link points to boot/vmlinuz, which does not exist in a USB installation.  By recreating a link to /cdrom/casper where vmlinuz actually exists, all is fine.

Fix is:

sudo rm /vmlinuz
sudo ln -s /cdrom/casper/vmlinuz vmlinuz

Then everything installs fine!

---

### Post by mejoe2 on 2010-11-25
I tried the following with no luck:

sudo rm /vmlinuz
sudo ln -s /cdrom/casper/vmlinuz vmlinuz
sudo apt-get install bcmwl-kernel-source

should I restart or something?

---

### Post by timbounceback on 2010-12-08
I think that should be:
```
sudo ln -s /cdrom/casper/vmlinuz /vmlinuz
```

---

