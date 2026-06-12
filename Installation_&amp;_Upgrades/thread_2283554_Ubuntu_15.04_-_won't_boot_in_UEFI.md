---
title: "Ubuntu 15.04 - won't boot in UEFI"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by Pawel_Kolano on 2015-06-22
Hello

I have tried multiple Linux distros to install on my PC, i always have the installer on USB pendrive, and it will boot fine but not if i choose UEFI,
whether i select "try linux" or "install" option, im getting either black screen or "no signal" on my monitor.

My GPU: Evga GTX 970
MOBO: MSI Z97 Gaming 3

PC is connected to monitor via HDMI.

Thanks in advance

---

### Post by Vladlenin5000 on 2015-06-22
Hi and welcome.

It has nothing to do with UEFI.
GTX970 isn't supported by the open source driver for nvidia cards. You need to press F6 and select *nomodeset* when you're at the "try... install..." menu in order to use generic video. This will allow you to install or simply run a live session.
Later, after installing, you need to add the same option by editing GRUB (again, in order to have video), install the proprietary drivers in System Settings > Software & Updates, reboot and edit Grub again to remove the edited option that's no longer needed.

---

