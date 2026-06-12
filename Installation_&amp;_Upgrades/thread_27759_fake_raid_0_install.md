---
title: "fake raid 0 install"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by flipy on 2005-04-17
Hi, I'm trying to install ubuntu on a fake-raid (via on-board raid), however I guess the install cd it's not using dmraid to catch the raid metadata and map the partitions. So, is there any way to do it?

---

### Post by colo on 2005-04-17
Kernel-Level RAID is always an option. Though I've been running into [problems]("http://www.ubuntuforums.org/showthread.php?p=136548#post136548") with it today.

---

### Post by flipy on 2005-04-18
well, maybe some more specs will help here.
motherboard: asus a8v deluxe
cpu: amd64 3000+winchester
chipset: via k8t800pro
raid: via vt8237 and promise 20378 (using via only)
hdd: 2xmaxtor 120Gb
vga: nvidia fx5900xt
ram: 2x512ddr400 kingston

so mdadm it's failing, cannot detect the raid partitinos (obviously), and i see that device-mapper is not active.
the reason why I need to have dual-boot is just university stuff and gaming, I'll be glad to switch to linux whenever I finish my career.

Is there any way to stop the installer at one point, then map manually the partitions with dmsetup and resume the installation?
If it is possible, how can I tweak the initrd file to map my partitons at boot?

Thanks anyway for your time!!!

---

