---
title: "kernel update to 2.6.19 produces unbootable kernel"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by martinko01 on 2007-01-08
I work with 6.10 desktop, and need a kernel upgrade to 2.6.19 for a 3ware hardware.

So this is my first time to try a kernel update, I downloaded the 2.6.19.1 sources from kernel.org and strictly followed the howto in  [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Making the kernel seems to work fine, but when I try to boot the safemode-kernel, it hangs while booting. console output hangs with ... USB HID core driver.

when I unplug the mouse, it says 
USB disconnect .... 
 and hangs again.

when I unplug the mouse completely and reboot, the output hangs at
Begin: Waiting for root file system ...
 and then 
ALERT! /dev/sda1 does not exist. Dropping to a shell!

with my restricted knowledge this seems like  USB and SATA support are not loaded ? but I wonder how that can happen, because I used the config of the running kernel for compiling the new one: 

cp /boot/config-`uname -r` ./.config
make menuconfig (with this .config file.)

how can I debug what's going on here ?

---

### Post by hal10000 on 2007-01-08
If you use the kernel config of the running kernel, then you better use the [COLOR="Red"]make oldconfig[/COLOR] command. Do as follows:

```

cp /boot/config-2.6.17-10-generic /usr/src/linux/.config (presuming you have 2.6.17-generic kernel)
cd /usr/src/linux
make oldconfig

```
You will then be asked only for new features of the 2.6.19 kernel to activate or deactivate or to cmpile things as a module.

---

