---
title: "problems building kernel"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by ARhere on 2010-06-03
Hey Everyone,

I am compiling the latest kernel for a project I am working on following [_this guide_]("http://www.crashcourse.ca/wiki/index.php/New_kernel_on_Ubuntu_10.04") and I ran into what I *hope* is a simple issue.

In the section "**Installing the new kernel and modules, and updating GRUB **" he stated to do...
```
$ sudo update-initramfs -c -k 2.6.34-rc7

```
When I look in /lib/modules the kernel folder I just built is 2.6.35-rc1+, but when I run his command with the new kernel name it says the path cannot be found... (*I added the bold*)
```
jabil@jabilU1:/media/dump1/linux-2.6$ **ls /lib/modules/2.6.35-rc1+/**
build              modules.builtin.bin  modules.inputmap   modules.seriomap
kernel             modules.ccwmap       modules.isapnpmap  modules.symbols
modules.alias      modules.dep          modules.ofmap      modules.symbols.bin
modules.alias.bin  modules.dep.bin      modules.order      modules.usbmap
modules.builtin    modules.ieee1394map  modules.pcimap     source
jabil@jabilU1:/media/dump1/linux-2.6$ sudo update-initramfs -c -k 2.6.35-rcl+
update-initramfs: Generating /boot/initrd.img-2.6.35-rcl+
**Cannot find /lib/modules/2.6.35-rcl+**
update-initramfs: failed for /boot/initrd.img-2.6.35-rcl+

```

WTF?  Does the new kernel name have an illegal character in the folder name?

-AR

---

### Post by ARhere on 2010-06-03
WOW!!  After typing this  Ijust realizes a "1" looks a lot like a "l".

I feel like a dumb@ss.

Sorry everyone,
-AR

---

