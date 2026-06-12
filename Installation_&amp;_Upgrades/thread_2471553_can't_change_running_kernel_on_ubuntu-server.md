---
title: "can't change running kernel on ubuntu-server"
date: 2022-02-02
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2022-02-02
I am trying to switch from the -raspi kernel to a generic one.
I've removed all -raspi packages and reinstalled the generic kernel but it still boots a -raspi kernel. :-(


```
$ uname -a
Linux media-server 5.13.0-1016-raspi #18-Ubuntu SMP PREEMPT Thu Jan 20 08:53:01 UTC 2022 aarch64 aarch64 aarch64 GNU/Linux
```


```

$ sudo apt list --installed | grep linux | cut -d  '/'  -f1

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

binutils-aarch64-linux-gnu
console-setup-linux
libselinux1
linux-base
linux-firmware
linux-headers-5.13.0-27-generic
linux-headers-5.13.0-27
linux-headers-5.13.0-28-generic
linux-headers-5.13.0-28
linux-headers-generic
linux-image-5.13.0-27-generic
linux-image-5.13.0-28-generic
linux-image-generic
linux-libc-dev
linux-modules-5.13.0-27-generic
linux-modules-5.13.0-28-generic
linux-modules-extra-5.13.0-27-generic
linux-modules-extra-5.13.0-28-generic
linux-sound-base
pptp-linux
util-linux
```

```
$ ls /boot
System.map-5.13.0-27-generic  dtb-5.13.0-28-generic         initrd.img.old
System.map-5.13.0-28-generic  dtbs                          vmlinuz
config-5.13.0-27-generic      firmware                      vmlinuz-5.13.0-27-generic
config-5.13.0-28-generic      initrd.img                    vmlinuz-5.13.0-28-generic
dtb                           initrd.img-5.13.0-27-generic  vmlinuz.old
dtb-5.13.0-27-generic         initrd.img-5.13.0-28-generic
```

---

### Post by bjlockie on 2022-02-03
It has something to do with uboot and dtbs:
[https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)

I'm going to leave it alone. :-)

---

