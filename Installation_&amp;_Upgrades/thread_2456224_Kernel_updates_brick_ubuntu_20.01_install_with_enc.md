---
title: "Kernel updates brick ubuntu 20.01 install with encrypted file system"
date: 2021-01-07
forum: Installation &amp; Upgrades
---

### Post by dogfoobar on 2021-01-07
Hi 

I have done a clean install of ubuntu 20.01 onto an encrypted disk using the default setup options. It bricks itself when updating the kernel as it can no longer boot the encrypted filesystem.

The specific error in apt update appears to be:

```
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-59-generic
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.
E: /usr/share/initramfs-tools/hooks/cryptkeyctl failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.4.0-59-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.4.0-59-generic (--configure):
 installed linux-image-5.4.0-59-generic package post-installation script subproc
ess returned error exit status 1

```
The full outtput below

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool linux-headers-generic-hwe-20.04
  thermald
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  linux-headers-5.8.0-34-generic linux-hwe-5.8-headers-5.8.0-34
  linux-image-5.8.0-34-generic linux-modules-5.8.0-34-generic
  linux-modules-nvidia-450-5.8.0-34-generic
The following packages will be upgraded:
  libwavpack1 linux-headers-generic-hwe-20.04
  linux-modules-nvidia-450-generic-hwe-20.04
3 to upgrade, 5 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
Need to get 48.7 MB of archives.
After this operation, 205 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libwavpack1 amd64 5.2.0-1ubuntu0.1 [77.3 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-hwe-5.8-headers-5.8.0-34 all 5.8.0-34.37~20.04.2 [11.3 MB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-headers-5.8.0-34-generic amd64 5.8.0-34.37~20.04.2 [1,236 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-headers-generic-hwe-20.04 amd64 5.8.0.34.37~20.04.20 [2,556 B]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-modules-5.8.0-34-generic amd64 5.8.0-34.37~20.04.2 [15.0 MB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-image-5.8.0-34-generic amd64 5.8.0-34.37~20.04.2 [9,499 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 linux-modules-nvidia-450-5.8.0-34-generic amd64 5.8.0-34.37~20.04.2 [11.5 MB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 linux-modules-nvidia-450-generic-hwe-20.04 amd64 5.8.0-34.37~20.04.2 [5,488 B]
Fetched 48.7 MB in 7s (7,389 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 209856 files and directories currently installed.)
Preparing to unpack .../0-libwavpack1_5.2.0-1ubuntu0.1_amd64.deb ...
Unpacking libwavpack1:amd64 (5.2.0-1ubuntu0.1) over (5.2.0-1) ...
Selecting previously unselected package linux-hwe-5.8-headers-5.8.0-34.
Preparing to unpack .../1-linux-hwe-5.8-headers-5.8.0-34_5.8.0-34.37~20.04.2_all
.deb ...
Unpacking linux-hwe-5.8-headers-5.8.0-34 (5.8.0-34.37~20.04.2) ...
Selecting previously unselected package linux-headers-5.8.0-34-generic.
Preparing to unpack .../2-linux-headers-5.8.0-34-generic_5.8.0-34.37~20.04.2_amd
64.deb ...
Unpacking linux-headers-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
Preparing to unpack .../3-linux-headers-generic-hwe-20.04_5.8.0.34.37~20.04.20_a
md64.deb ...
Unpacking linux-headers-generic-hwe-20.04 (5.8.0.34.37~20.04.20) over (5.4.0.59.
62) ...
Selecting previously unselected package linux-modules-5.8.0-34-generic.
Preparing to unpack .../4-linux-modules-5.8.0-34-generic_5.8.0-34.37~20.04.2_amd
64.deb ...
Unpacking linux-modules-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
Selecting previously unselected package linux-image-5.8.0-34-generic.
Preparing to unpack .../5-linux-image-5.8.0-34-generic_5.8.0-34.37~20.04.2_amd64
.deb ...
Unpacking linux-image-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
Selecting previously unselected package linux-modules-nvidia-450-5.8.0-34-generi
c.
Preparing to unpack .../6-linux-modules-nvidia-450-5.8.0-34-generic_5.8.0-34.37~
20.04.2_amd64.deb ...
Unpacking linux-modules-nvidia-450-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
Preparing to unpack .../7-linux-modules-nvidia-450-generic-hwe-20.04_5.8.0-34.37
~20.04.2_amd64.deb ...
Unpacking linux-modules-nvidia-450-generic-hwe-20.04 (5.8.0-34.37~20.04.2) over 
(5.4.0-59.65) ...
Setting up linux-hwe-5.8-headers-5.8.0-34 (5.8.0-34.37~20.04.2) ...
Setting up linux-firmware (1.187.7) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-58-generic
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.
E: /usr/share/initramfs-tools/hooks/cryptkeyctl failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.4.0-58-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned e
rror exit status 1
Setting up linux-headers-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.8.0-34-generic

Kernel preparation unnecessary for this kernel.  Skipping...
applying patch disable_fstack-clash-protection_fcf-protection.patch...patching f
ile Kbuild
Hunk #1 succeeded at 84 (offset 13 lines).


Building module:
cleaning build area...
unset ARCH; [ ! -h /usr/bin/cc ] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'ma
ke' -j4 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=5.8.0-34-generic IGNORE_XEN_PRE
SENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/5.8.0-34-generic/build LD=/usr/
bin/ld.bfd modules...................
cleaning build area...

DKMS: build completed.

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.8.0-34-generic/updates/dkms/

nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.8.0-34-generic/updates/dkms/

nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.8.0-34-generic/updates/dkms/

nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.8.0-34-generic/updates/dkms/

depmod...

DKMS: install completed.
   ...done.
Setting up linux-headers-generic-hwe-20.04 (5.8.0.34.37~20.04.20) ...
Setting up linux-modules-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
Setting up libwavpack1:amd64 (5.2.0-1ubuntu0.1) ...
Setting up linux-image-5.4.0-59-generic (5.4.0-59.65) ...
Setting up linux-image-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.4.0-58-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.4.0-58-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.8.0-34-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.8.0-34-generic
Setting up linux-modules-nvidia-450-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
linux-image-nvidia-5.8.0-34-generic: constructing .ko files
Setting up linux-modules-nvidia-450-generic-hwe-20.04 (5.8.0-34.37~20.04.2) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
Processing triggers for linux-image-5.4.0-59-generic (5.4.0-59.65) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-59-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-59-generic
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.
E: /usr/share/initramfs-tools/hooks/cryptkeyctl failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.4.0-59-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.4.0-59-generic (--configure):
 installed linux-image-5.4.0-59-generic package post-installation script subproc
ess returned error exit status 1
Processing triggers for linux-image-5.8.0-34-generic (5.8.0-34.37~20.04.2) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.8.0-34-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.8.0-34-generic
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.
E: /usr/share/initramfs-tools/hooks/cryptkeyctl failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.8.0-34-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.8.0-34-generic (--configure):
 installed linux-image-5.8.0-34-generic package post-installation script subproc
ess returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-5.4.0-59-generic
 linux-image-5.8.0-34-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dogfoobar on 2021-01-07
Fixed it - It seems the package keyutils is not installed by default.
apt-get install keyutils

Seems to have fixed it

---

