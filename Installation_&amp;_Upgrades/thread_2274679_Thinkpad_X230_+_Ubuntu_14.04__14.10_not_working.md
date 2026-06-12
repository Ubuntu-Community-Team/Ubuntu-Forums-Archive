---
title: "Thinkpad X230 + Ubuntu 14.04 / 14.10 not working"
date: 2015-04-21
forum: Installation &amp; Upgrades
---

### Post by finni on 2015-04-21
I tried to install ubuntu 64bit 14.04 and 14.10 to Lenovo Thinkpad X230 with Kingston SSDNow 300 240GB SSD drive. Installation goes smoothly but I'm greeted with busybox when trying to boot to system. It seems harddrive is not recognized for some reason. "ls /dev" do not show any sda* drives there. Funny though that with live USB the system recognizes the hard drive. I use ext3 for root partition's file system.

Is there some setting/parameter that I'm missing at the boot? Maybe something to do with ACPI?

In BIOS changing SATA setting (to not AHCI) makes system boot (14.04) but it's pretty much in-usable as the only thing that works is the laptop's keyboard...

Latest Linux Mint Cinnamon worked perfectly with this machine.

---

### Post by finni on 2015-04-22
Ubuntu 12.04 works also perfectly.

---

### Post by finni on 2015-04-28
Anyone got 14.04 or 14.10 working on X230?

---

### Post by Klaster on 2015-06-09
Haven't upgraded my x230 yet since 12.04 runs smoothly. Would like to hear some experiences, too! Anyone?

---

