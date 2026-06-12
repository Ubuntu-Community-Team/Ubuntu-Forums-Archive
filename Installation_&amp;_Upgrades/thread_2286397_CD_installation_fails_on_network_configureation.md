---
title: "CD installation fails on network configureation"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by joe135 on 2015-07-11
Hi, I'm rather new to Ubuntu.  I had a ubuntu 14.04 partition installed on my computer, but the windowing environment never worked quite well.   So, I figured I'd reinstall it.   I don't have a DVD handy, but I did have a CD, so I burnt the mini.iso to CD, booted from it, and tried to install 14.04 LTS.   However, after it asks for my wireless ESSID, Ubuntu complains no network can be found:

[FONT=courier new]Your network is probably not using the DCHP protocol.   Alternatively, the DHCP server may be slow or some network hardware is not working properly.[/FONT]

  I am guessing the problem is there is no driver for my wireless dongle, a Linksys compact wireless-G USB adapter.   The network has worked find with Ubuntu and Fedora in the past.

Any suggestions on what should I try next?   I'm guessing I need to burn an installation DVD rather than use the mini.iso.

---

### Post by Vladlenin5000 on 2015-07-11
> **joe135 said:**
> I'm guessing I need to burn an installation DVD rather than use the mini.iso.

Exactly. The minimal CD should be used with Ethernet - the vast majority of Ethernet cards are supported - or with a known good and supported WiFi device.

---

### Post by Bucky Ball on 2015-07-12
> **Vladlenin5000 said:**
> Exactly. The minimal CD should be used with Ethernet - the vast majority of Ethernet cards are supported - or with a known good and supported WiFi device.

^^^
This. Unless you can get an ethernet cable to the machine. A mini install much lighter, depending on what you shovel on top of the base kernel, of course. ;)

---

### Post by joe135 on 2015-07-13
Thanks all, I'll try and find a DVD to burn.

---

### Post by Bucky Ball on 2015-07-13
You can use a USB dongle if you have one instead of a disk.

---

