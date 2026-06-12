---
title: "upgrade to allow teamviewer"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by tonymoloney on 2014-08-12
My friend has just been told to upgrade his system so that he can run TeamViewer.
However, when he tries to do so he gets the following message:

Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-24-generic
 linux-image-3.13.0-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-All-Series:~$ 

Can anyone help me on this please?

His specs are Ubuntu 14.04 on a 64bit desktop. Dual booted with Windows7 and running on a ASUS H87M-E motherboard with 16Gb RAM. The motherboard has EUFI but has been able to install Linux on it.

---

### Post by plucky on 2014-08-12
What is the current version of kernel being used? ```
uname -a
```

Open a terminal and run ```
sudo apt-get clean
sudo apt-get install -f
``` and post the output.

The first command will remove all the .deb files in /var/cache/apt/archives and the system will have to download a fresh version when you run the second command.

Good Luck

---

### Post by Johncharles on 2014-08-12
Thanks for your response. Unfortunately, living in Western Australia makes foir a big delay in answering.

When I run the first command uname -a I get the following:

john@john-All-Series:~$ uname -a
Linux john-All-Series 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
john@john-All-Series:~$

So it looks like 3.13.0-24-generic was not removed as can be seen from the output of the second two commands sudo apt-get clean and sudo apt-get install -f

These commands gave (at the last few lines) the following:
john@john-All-Series:~$ uname -a
Linux john-All-Series 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
john@john-All-Series:~$

dpkg: error processing package linux-image-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-24-generic
 linux-image-3.13.0-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Sorry - I don't know how to include the full output from these commands.

What can I do next, please?

---

### Post by plucky on 2014-08-13
> john@john-All-Series:~$ uname -a
Linux john-All-Series 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

As you are running a later kernel,you can try using dpkg to remove the broken kernel.
```
sudo dpkg -r linux-image-3.13.0-24-generic
```

How many kernels do you have installed? ```
ls /boot
``` and cut and paste output to forum.


Good Luck

---

### Post by Johncharles on 2014-08-14
Thanks. When I tried to remove the broken kernel I get:

Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.13.0-24-generic
john@john-All-Series:~$ 


. Here's the output from ls /boot

john@john-All-Series:~$ ls /boot
abi-3.11.0-15-generic         initrd.img-3.13.0-33-generic
abi-3.13.0-27-generic         initrd.img-3.8.0-31-generic
abi-3.13.0-29-generic         memtest86+.bin
abi-3.13.0-33-generic         memtest86+.elf
abi-3.8.0-31-generic          memtest86+_multiboot.bin
config-3.11.0-15-generic      System.map-3.11.0-15-generic
config-3.13.0-27-generic      System.map-3.13.0-27-generic
config-3.13.0-29-generic      System.map-3.13.0-29-generic
config-3.13.0-33-generic      System.map-3.13.0-33-generic
config-3.8.0-31-generic       System.map-3.8.0-31-generic
extlinux                      vmlinuz-3.11.0-15-generic
grub                          vmlinuz-3.13.0-27-generic
initrd.img-3.11.0-15-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-27-generic  vmlinuz-3.13.0-33-generic
initrd.img-3.13.0-29-generic  vmlinuz-3.8.0-31-generic
john@john-All-Series:~$ 

You might notice I've changed my user name. That's because I got my mate who has the problem to sign up to the forum and we're now using his signup.

---

### Post by sp40140 on 2014-08-14
Is your main issue : to run teamviewer or to upgrade kernel?
I have been using TV for past 2+ years. and so it's been running without any issue on lots of recent versions.
What error do you get when you try to install or run TV?

---

### Post by plucky on 2014-08-15
> Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-24-generic (--remove):
subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
linux-image-3.13.0-24-generic

From your ls /boot output you don't seem to have that kernel installed.

Open a terminal and run ```
gedit /var/lib/dpkg/status
``` and from within gedit search for **linux-image-3.13.0-24-generic** and cut and paste the output for that package if it is there.

It should look like ```
Package: linux-image-3.5.0-54-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 153987
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-lts-quantal
Version: 3.5.0-54.81~precise1
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-lts-quantal-doc-3.5.0 | linux-lts-quantal-source-3.5.0, linux-lts-quantal-tools, linux-headers-3.5.0-54-generic
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 64 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 64 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.
``` except it will be the 3.13.0-24 kernel.

This is for my kernel on 12.04.5

If it is there,see what the ```
Status: install ok installed
``` says.

---

