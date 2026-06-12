---
title: "dist-upgrade broke boot and nvidia"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by genjix on 2007-10-07
Hello,

Everytime I do a dist-upgrade in aptitude, it seems my system breaks again. This time I thought I'd try some luck with it again... with bad results :(

> # aptitude update
# aptitude dist-upgrade

Is that correct? Now the default boot target just hangs, and if I change the boot line to nosplah it is just stopped at "Starting ..."
This is 2.6.20-16-generic

If I try the next one 2.6.17-11-generic, it stops at [Finding cpu acpiid] (or so, can't remember exact line), and the last kernel 2.6.17-10-generic boots!

But then my X doesn't work with nvidia driver (only nv)

> root@amir:/home/genjix# modprobe nvidia
FATAL: Error running install command for nvidia

What's going on?? How can I fix nvidia (important since I work with 3D!) and then get my kernel(s) booting?

Thank you for your time :)

---

### Post by pbcartwright on 2007-10-07
change /etc/X11/xorg.conf to driver nv, instead of nvidia. then install envy. once booted, run envy to setup your nvidia driver.
or just boot to the console text login and install the latest nvidia driver, nvidia-linux-x86....run go to nvidia, download the latest, read the README and install it.
every time you update your kernel you need to rerun teh nvidia setup..
every time...

---

### Post by genjix on 2007-10-08
But it is the old kernel that doesn't work with the nvidia driver, and I've purged nvidia-glx and nvidia-kernel-common and reinstalled.

---

### Post by genjix on 2007-10-08
Since I have done that, the first 2 kernels now go 2 steps extra...

> **2.6.20-16-generic** and **2.6.15-386**
Starting up...
Loading, please wait
[   4.832000] usb 1-1: device not accepting address 2, error -71

> **2.6.17-11-generic**
Starting up...
Loading, please wait
[17179575.228000] ACPI: Getting cpuindex for acpiid 0x1

The last kernel 2.6.17-10-generic boots, but I am stuck without the nvidia driver.

---

### Post by genjix on 2007-10-09
no one? :(

---

