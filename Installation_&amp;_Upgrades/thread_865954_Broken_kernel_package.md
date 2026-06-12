---
title: "Broken kernel package"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by mtinston on 2008-07-21
I've got a problem removing the packages associated with an old kernel. Upgrading the kernel I found that my /boot partition was full, so I removed a few of my old kernels.  Doing that seems to have hosed things up, I now have a broken package that will not finish removing, nor re-install.  Synaptic doesn't report its files and won't allow me to perform any other package updates while it detects this is broken.  Specifically, I can not complete the removal of: linux-ubuntu-modules-2.6.22-14-generic. Status yields:

>>>> sudo dpkg -s linux-ubuntu-modules-2.6.22-14-generic


Package: linux-ubuntu-modules-2.6.22-14-generic
Status: deinstall ok half-installed
Priority: optional
Section: base
Installed-Size: 10992
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-ubuntu-modules-2.6.22
Version: 2.6.22-14.37
Config-Version: 2.6.22-14.37
Provides: ndiswrapper-modules-1.9, apparmor-modules-2.1
Depends: linux-image-2.6.22-14-generic
Pre-Depends: dpkg (>= 1.10.24)
Description: Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64
This package contains modules supplied by Ubuntu for Linux kernel 2.6.22 on
x86/x86_64.
.
You likely do not want to install this package directly. Instead, install
the linux-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed.

And trying to remove with dpkg or apt-get (even with the force options) yields:

>>>> sudo dpkg --force-remove-reinstreq -r linux-ubuntu-modules-2.6.22-14-generic


(Reading database ... 274152 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
linux-ubuntu-modules-2.6.22-14-generic

I've tried re-installing the dependencies of the package but the version is out of date. Ideas would be appreciated.

Thanks
Mike

---

### Post by mtinston on 2008-08-06
I decidd to try giving it blank copies of the files and directories it said were missing.  Once those line didn't generate errors things seem to work.

---

