---
title: "Ubuntu-server, new kernel crashes!"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by icc on 2008-02-19
Hi,

I installed ubuntu-server 7.10 on a HP Proliant ML370 G3, fetched the bash stuff++ from the rehl4 rpm at hp.com and got fan adjustment and everything to work. Now the real problem comes, I fetched the .config from kernel-headers-2.6.22-14-server, compiled a new kernel(2.6.24.2) with grsec++, disabled VSDO, EFI, irda, sound and a bunch of stuff I really won't need on a server. At boot the kernel loads for a while then something like this pops out:

```
check root= bootarg cat /proc/cmdline or missing modules, devices cat /proc/modules ls /dev/
ALERT! /dev/disk/by-uuid/a99bdda0-44a3-4811-8cc4-2d315ff97756 does not exist.
Dropping to shell!
```

I keep thinking there's something I've forgotten, cause the old 2.6.22-14-server kernel boots perfectly and I used almost the same .config. 

btw. the server uses HP Smart Array 6402 controller (scsi ultra320) and the modules should be loaded.

Sorry for my bad english!

Here's link to my [.config]("http://itth.net/~icc/.config")

---

### Post by icc on 2008-02-20
Update:

I added cciss to /etc/modules and the error went away, but now the box hangs on Loading linux...

Without the quiet splash the last pices I see is that he finds the cciss0 device and prints some info and then nothing happens.

How could the last kernel boot without the cciss module in /etc/modules? Does it have the module in initramfs? Sorry, but don't know alot about how the default server kernel is built in ubuntu, is the modules built into the kernel?

Help appreciated...

---

