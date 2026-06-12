---
title: "Kernel upgrades; safe?"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2008-01-14
After reading so many tails of woe, I wonder if it's safe to update to kernel 2.6.22-14.47?

Also, how can I see the date of an update? Update mana&#609;er doesn't seem to tell me the date that an update became available,

Also, how can I see the "revision" number of my installed kernel?


```
$ uname -a
Linux Saturn 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

$ apt-cache search ^linux-headers.*
linux-headers-generic - Generic Linux kernel headers
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-rt - Linux kernel headers on realtime kernel
linux-headers-xen - Linux kernel headers on Xen
linux-headers-2.6.22-14 - Header files related to Linux kernel version 2.6.22
linux-headers-2.6.22-14-generic - Linux kernel headers for version 2.6.22 on x86/x86_64
linux-headers-2.6.22-14-rt - Linux kernel headers for version 2.6.22 on RT kernel
linux-headers-2.6.22-14-server - Linux kernel headers for version 2.6.22 on x86/x86_64
linux-headers-2.6.22-14-xen - Linux kernel headers for version 2.6.22 on This kernel can be used for Xen dom0 and domU
```

Beef

---

### Post by jocheem67 on 2008-01-14
Well, actually I'm a nOOb regarding kernel stuff, nevertheless I decided to do an upgrade. Used the excellent howto from the "master kernel thread"...besides some recompiling my rt61 wifi chip, no harm done here!
Used envy to recompile my nvidia drivers. Running 2.6.23.13 now, the latest stable kernel from kernel.org.

Actually there's a nifty little proggie called kernelcheck that you could use. It displays your kernel-version and can do an upgrade for you!
The author is around the forum too, the program is at sourceforge...

---

### Post by Partyboi2 on 2008-01-14
To check your kernel
```
uname -r
```
to check the date of updates you can go to Synaptic (System>Admin>Synaptic Package Manager) Click on "file" and choose "history"

---

