---
title: "prob removing package with broken dependencies"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by glennoph on 2008-06-21
I am using xubuntu and was trying out xen.  I wanted to remove xen, but had problems doing so.

the packages that i am trying to remove are:
linux-image-2.6.24-18-xen 
linux-image-2.6.24-19-xen

I noticed that there is a similar thread about problems removing a package.  I did not want to post in that thread.

note that i had updated the status for the linux*-18-xen package to "install ok installed"


I had done the clean and autoremove, results below:

glennop@ua64:/var/lib/dpkg$ sudo apt-get clean
glennop@ua64:/var/lib/dpkg$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to these.
The following packages have unmet dependencies:
  linux-ubuntu-modules-2.6.24-18-xen: Depends: linux-image-2.6.24-18-xen but it is not installed
  linux-ubuntu-modules-2.6.24-19-xen: Depends: linux-image-2.6.24-19-xen but it is not installed
E: Unmet dependencies. Try using -f.

please help.  I will try the autoremove -f next.

--glenn

---

### Post by glennoph on 2008-06-21
I see that the sibling post is solved.  that is a good sign.

[SOLVED] Can't get rid of package

---

### Post by glennoph on 2008-06-21
status file changes:

Package: linux-ubuntu-modules-2.6.24-18-xen
Status: install ok installed
Priority: optional
Section: universe/base
Installed-Size: 10292
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-ubuntu-modules-2.6.24
Version: 2.6.24-18.26
Config-Version: 2.6.24-18.26
Depends: linux-image-2.6.24-18-xen
Pre-Depends: dpkg (>= 1.10.24)
Description: Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
 This package contains modules supplied by Ubuntu for Linux kernel 2.6.24 on
 x86/x86_64.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-xen meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.



Package: linux-restricted-modules-2.6.24-18-xen
Status: deinstall ok config-files
Priority: optional
Section: restricted/misc
Installed-Size: 26648
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-restricted-modules-2.6.24
Version: 2.6.24.13-18.41
Config-Version: 2.6.24.13-18.41
Provides: nvidia-kernel-169.12, nvidia-kernel-71.86.04, nvidia-kernel-96.43.05
Depends: linux-image-2.6.24-18-xen, linux-restricted-modules-common (>= 2.6.24)$
Suggests: avm-fritz-firmware-2.6.24-18, nvidia-glx | nvidia-glx-legacy | nvidia$



Package: linux-image-2.6.24-18-xen
Status: deinstall ok config-files
Priority: optional
Section: universe/base
Installed-Size: 78504
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 2.6.24-18.32
Config-Version: 2.6.24-18.32
Provides: fuse-module, kvm-api-4, linux-image, linux-image-2.6, redhat-cluster-$
Depends: coreutils | fileutils (>= 4.0), initramfs-tools (>= 0.36ubuntu6), modu$
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub
Suggests: fdutils, linux-doc-2.6.24 | linux-source-2.6.24
Conflicts: hotplug (<< 0.0.20040105-1)



Package: linux-xen
Status: purge ok not-installed
Priority: optional
Section: restricted/metapackages


Package: linux-image-xen
Status: purge ok not-installed
Priority: optional
Section: metapackages


Package: ubuntu-xen-server
Status: purge ok not-installed
Priority: optional
Section: base



Package: linux-image-2.6.24-19-xen
Status: deinstall ok config-files
Priority: optional
Section: universe/base
Installed-Size: 78512



Package: linux-restricted-modules-2.6.24-19-xen
Status: deinstall ok config-files
Priority: optional
Section: restricted/misc



Package: linux-restricted-modules-xen
Status: purge ok not-installed
Priority: optional
Section: restricted/metapackages

...

hmm this goes on and on.

---

### Post by glennoph on 2008-06-21
Below are the records from status with Package: linux.*xen.  two lines of context are included.

Package: linux-image-2.6.24-19-xen
Status: deinstall ok config-files
Priority: optional
--
Package: linux-restricted-modules-2.6.24-19-xen
Status: deinstall ok config-files
Priority: optional
--
Package: linux-restricted-modules-xen
Status: purge ok not-installed
Priority: optional
--
Package: linux-ubuntu-modules-2.6.24-19-xen
Status: deinstall ok half-installed
Priority: optional
--
Package: linux-ubuntu-modules-2.6.24-18-xen
Status: install ok installed
Priority: optional
--
Package: linux-restricted-modules-2.6.24-18-xen
Status: deinstall ok config-files
Priority: optional
--
Package: linux-image-2.6.24-18-xen
Status: deinstall ok config-files
Priority: optional
--
Package: linux-xen
Status: purge ok not-installed
Priority: optional
--
Package: linux-image-xen
Status: purge ok not-installed
Priority: optional

---

### Post by mtinston on 2008-07-15
I've got a similar problem removing the packages associated with an old kernel.  Specificially, I can not complete the removal of: linux-ubuntu-modules-2.6.22-14-generic.  Status yields:

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

I've tried re-installing the dependencies of the package but the version is out of date.  Ideas would be appreciated.

Thanks
Mike

---

### Post by glennoph on 2008-07-16
I wish I could give you a good answer.  I ended up reinstalling ubuntu. 
I also went through a painfull situation where the wireless and wired network adapters would not start.  That has been resolved.  But the memories of corrupted os fixes lingers. :-(

---

