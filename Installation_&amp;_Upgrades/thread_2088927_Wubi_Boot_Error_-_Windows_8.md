---
title: "Wubi Boot Error - Windows 8"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Kazeken on 2012-11-27
Recently I obtained a new thinkpad T530 and wanted to put ubuntu on it, the thing at the moment has Windows 8 Installed. So wubi ran installed, did its stuff and said to reboot. Came up with this.[IMG]http://i48.tinypic.com/21a5if.jpg[/IMG] I was still able to boot into window 8 however unable to boot in ubuntu..

---

### Post by bcbc on 2012-11-29
Wubi doesn't work with UEFI. If you bought a new computer with Windows 8 preinstalled it likely has secure boot, which means UEFI and GPT disks. And wubi needs a MBR partition table disk.

So the answer is, you should uninstall Ubuntu (from Add or remove programs in the Control Panel) and then install a normal dual boot using a 64-bit Ubuntu desktop disk.

---

