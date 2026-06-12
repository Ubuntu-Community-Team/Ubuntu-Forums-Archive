---
title: "[SOLVED] Debootstrap questions"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by absolutezero1287 on 2008-06-26
I'm trying to create a minimal build using debootstrap.
(Minimal CD and cli install from Alternative isn't an option, don't ask why)

I used debootstrap --arch i386 hardy and ran some problems installing X and other essentials. It kept saying that /dev/pts isn't mounted and upon further inspection neither is /proc. What am I missing?

---

### Post by absolutezero1287 on 2008-06-27
Bump? Please help.

---

### Post by absolutezero1287 on 2008-06-28
Solved my own problem.
> It kept saying that /dev/pts isn't mounted and upon further inspection neither is /proc. What am I missing?
I'm working from within a chroot environment. The error messages are normal and can be ignored.

However, I've come across a new problem. [http://pastebin.com/m220513d7](http://pastebin.com/m220513d7)

---

### Post by absolutezero1287 on 2008-07-03
Problem solved. I didn't bind mount /dev /proc and /sys.

---

### Post by absolutezero1287 on 2008-07-03
My minimal install is almost done. I can boot into fluxbox. However, I don't know how to configure it for internet access. I'm using a wireless G usb adapter (WUSB54GC). The needed driver rt73usb.bin comes installed with the linux-generic metapackage. I just don't know how to get it working.

I have an exisisting full install on another partition that I used to create the minimal install. I was guessing that there are some configuration files that I could copy over to get it working but I wouldn't know where to begin. Also, I would like to configure Ubuntu to use my ethernet card. Please help.

wireless: WUSB54GC wireless G usb adapter
ethernet: 01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

