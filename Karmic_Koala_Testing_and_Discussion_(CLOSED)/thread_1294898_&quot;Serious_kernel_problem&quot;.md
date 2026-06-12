---
title: "&quot;Serious kernel problem&quot;"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NJC on 2009-10-18
How to debug this more completely? See attached kernel problem first.

---

### Post by 23meg on 2009-10-18
Is this a self-compiled kernel, or a non-Ubuntu kernel package? Please post the output of ```
apt-cache show linux-image-`uname -r`
```.

---

### Post by rtalcott on 2009-10-18
I have also been getting this error on two machines.
rt

```
apt-cache show linux-image-`uname -r`
Package: linux-image-2.6.31-14-generic
Priority: optional
Section: admin
Installed-Size: 110768
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 2.6.31-14.48
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), coreutils | fileutils (>= 4.0), module-init-tools (>= 3.3-pre11-4ubuntu3), wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-2.6.31 | linux-source-2.6.31
Conflicts: hotplug (<< 0.0.20040105-1)
Filename: pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_amd64.deb
Size: 28915168
MD5sum: dba0339398ab4f57186b0e2863ee0296
SHA1: 688faaf4a87e5980c7f8bb7e457cf57207ddc88b
SHA256: a20ab1064193b10388dbab1725d00ecf3f949c0a9ff10e8f95822366db83732d
Description: Linux kernel image for version 2.6.31 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.31 on
 x86/x86_64.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
```

---

### Post by NJC on 2009-10-18
As far as I know it's the regular kernel.

------------------------

Package: linux-image-2.6.31-11-generic
Status: install ok installed
Priority: optional
Section: base
Installed-Size: 87928
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 2.6.31-11.36
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), coreutils | fileutils (>= 4.0), module-init-tools (>= 3.3-pre11-4ubuntu3), wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-2.6.31 | linux-source-2.6.31
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 2.6.31 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.31 on
 x86/x86_64.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

---

### Post by VMC on 2009-10-18
> **NJC said:**
> As far as I know it's the regular kernel.

------------------------

Package: linux-image-2.6.31-11-generic

We are up to 14 now. Why not try an update the kernel and see if that fixes things.

```
$ apt-cache show linux-image-`uname -r`
Package: linux-image-2.6.31-14-generic
Priority: optional
Section: admin
Installed-Size: 88104
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 2.6.31-14.48
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), coreutils | fileutils (>= 4.0), module-init-tools (>= 3.3-pre11-4ubuntu3), wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-2.6.31 | linux-source-2.6.31
Conflicts: hotplug (<< 0.0.20040105-1)
Filename: pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb
Size: 28822776
MD5sum: f137823bd0858d2016a9291bfeb3a959
SHA1: 8c1522ee630d534cdfabc556b449fe4f47d06c10
SHA256: 2b158e4c65a1afff8f9e115f0a7b3e9821fa63ec41682a296f0554895dfca19d
...

```

---

### Post by NJC on 2009-10-18
I had been avoided the "Partial Upgrade" warning by 23meg. I updated to 2.6.31-14 and it seems faster. I'll post back if I receive any similar errors as per above. Thanks for the help guys.

EDIT: My machine is issuing a crash report upon restarting after Suspend. I was able to finish the crash report this time and filed bug accordingly:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417842)

---

