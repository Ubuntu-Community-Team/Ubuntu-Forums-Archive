---
title: "ubuntu 8.04 installation problem: black screen."
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by liyu on 2008-04-27
Hi,

I tried to install ubuntu 8.04 amd64 by grub4dos and casper means, but this try failed.

The GNOME in Live CD can startup without any problem, but LCD screen will be turned black suddenly after running some periods(this time interval vary from some seconds to two or three minutes). I ever used google to search some sites, someone said it is possible to due to splash, but there is no any splash kernel parameter in grub configuation.

When the screen is black, the leds on PS/2 keyboard show that the system still did not hangup *sometime* (I can switch them), but the led of my optical USB mouse is be turned off. And in this time, I can not switch virtual terminal too. Also, I can not  reboot by press Ctrl-Alt-Del, so I must press that Big-Red-Button to reset *_*

I tried below some means:

1. add kernel parameter noapic, noapictimer, pci=noacpi.
2. replace digital cable with old VGA cable.
3. change some BIOS setups.
4. Ubuntu 8.04 am64 server can install (by CDROM) on my PC successfully.

My PC configuration is:

1. SOYO A-780+ (AMD 780G chipset)
2. AMD Athlon 64x2 5000+ (blackbox), no overclocking.
3. No other display adapter.

That is all.

Any suggestion is welcome.

Thanks in advanced.

- Yu

---

### Post by liyu on 2008-04-27
Wubi also failed for me. The attachment is wubi installation log.

---

### Post by Rallg on 2008-04-27
One possibility: Is the UUID of your Ubuntu partition correct, in the Grub menu.lst? It could be incorrect if your bootloader was installed at a different time or place, but not automatically updated duing fresh install.

---

### Post by liyu on 2008-04-28
Thanks, however, it seem this is not due to UUID parameter in menu.lst. In fact, there even has no any UUID parameter, and I guest the casper installation use a ramdisk like as root filesystem.

---

