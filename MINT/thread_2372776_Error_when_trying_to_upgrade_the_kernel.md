---
title: "Error when trying to upgrade the kernel"
date: 2017-09-28
forum: MINT
---

### Post by pchokola on 2017-09-28
First of all, no problem on other computers, just a T470 Thinkpad on a new install where I am trying to upgrade the kernel.  All other software updates work fine, and the OS is working OK.

I am trying to upgrade from:

4.10.0-32

to

4.10.0-35

However the upgrade fails.  Here is the log of the install:

```
Selecting previouslyunselected package linux-headers-4.10.0-35.
(Reading database... 235675 files and directories currently installed.)
Preparing to unpack.../linux-headers-4.10.0-35_4.10.0-35.39~16.04.1_all.deb ...
Unpackinglinux-headers-4.10.0-35 (4.10.0-35.39~16.04.1) ...
dpkg: errorprocessing archive/var/cache/apt/archives/linux-headers-4.10.0-35_4.10.0-35.39~16.04.1_all.deb(--unpack):
 unable to open'/usr/src/linux-headers-4.10.0-35/arch/score/kernel/Makefile.dpkg-new':Operation not permitted
Selecting previouslyunselected package linux-headers-4.10.0-35-generic.
Preparing to unpack.../linux-headers-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb...
Unpackinglinux-headers-4.10.0-35-generic (4.10.0-35.39~16.04.1) ...
Selecting previouslyunselected package linux-image-4.10.0-35-generic.
Preparing to unpack.../linux-image-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb ...
Done.
Unpackinglinux-image-4.10.0-35-generic (4.10.0-35.39~16.04.1) ...
dpkg: errorprocessing archive/var/cache/apt/archives/linux-image-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb(--unpack):
 unable to createnew file '/var/lib/dpkg/info/linux-image-4.10.0-35-generic.list-new':Operation not permitted
Selecting previouslyunselected package linux-image-extra-4.10.0-35-generic.
Preparing to unpack.../linux-image-extra-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb...
Unpackinglinux-image-extra-4.10.0-35-generic (4.10.0-35.39~16.04.1) ...
dpkg: errorprocessing archive/var/cache/apt/archives/linux-image-extra-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb(--unpack):
 unable to open'/lib/modules/4.10.0-35-generic/kernel/drivers/gpu/drm/virtio/virtio-gpu.ko.dpkg-new':Operation not permitted
Errors wereencountered while processing:
/var/cache/apt/archives/linux-headers-4.10.0-35_4.10.0-35.39~16.04.1_all.deb
/var/cache/apt/archives/linux-image-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb
/var/cache/apt/archives/linux-image-extra-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb
E: Sub-process/usr/bin/dpkg returned an error code (1)
A package failed toinstall.  Trying to recover:
dpkg: dependencyproblems prevent configuration of linux-headers-4.10.0-35-generic:
linux-headers-4.10.0-35-generic depends on linux-headers-4.10.0-35;however:
  Packagelinux-headers-4.10.0-35 is not installed.


dpkg: errorprocessing package linux-headers-4.10.0-35-generic (--configure):
 dependency problems- leaving unconfigured

```

Also, this is regarding Linux Mint 18, which for all intents and purposes is Ubuntu; just not getting any headway elsewhere.

My configuration is as follows:

1) Centos 7 was installed first on partiitions 1 & 2.  This GRUB is used to select which Linux to load.
2) Linux Mint was then installed on partition 4.

I uninstalled the failing kernel and cleaned up all updates, but I get the same result when trying to re-install the kernel.

---

### Post by oldos2er on 2017-09-28
Moved to Mint.

---

### Post by pchokola on 2017-09-29
SOLVED:  Sophos-Antivirus prevented the kernel update.  Removed it and everything is OK now.

---

