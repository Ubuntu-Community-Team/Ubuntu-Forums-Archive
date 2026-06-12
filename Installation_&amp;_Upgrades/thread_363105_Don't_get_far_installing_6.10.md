---
title: "Don't get far installing 6.10"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by cknittle on 2007-02-16
This is my first attempt at installing Linux on a PC.  I'm trying to install Ubuntu 6.10 on a new Dell Optiplex 320.  Pentium D, 3.4 GHz.

I've tried a CD version, then also burned a DVD, but nothing works.  After booting from disk and reaching the main menu, I select "Start or install Ubuntu".  after a popup that indicates "Loading Linux Kernel", within a few seconds I get

"PCI: Cannot allocate resource region 1 of device 0000:00:14.0.  

Googling has not yielded anything helpful.

Hope you can help.

C

---

### Post by milton1 on 2007-02-16
have you tried the alternate install cd? it runs without X, and is often easier.

---

### Post by zgoda on 2007-02-28
No way. I succeeded installing Debian Etch, following instructions found on 'net (just google for "dell optiplex 320 linux"). I found also, that the kernel 2.6.20 has the workaround for this Dell bug, but afaik no distribution supplies this kernel version...

---

### Post by janz84 on 2007-02-28
> **cknittle said:**
> This is my first attempt at installing Linux on a PC.  I'm trying to install Ubuntu 6.10 on a new Dell Optiplex 320.  Pentium D, 3.4 GHz.

I've tried a CD version, then also burned a DVD, but nothing works.  After booting from disk and reaching the main menu, I select "Start or install Ubuntu".  after a popup that indicates "Loading Linux Kernel", within a few seconds I get

"PCI: Cannot allocate resource region 1 of device 0000:00:14.0.  

Googling has not yielded anything helpful.

Hope you can help.

C

try disabling the usb 2.0 controller in your bios

---

