---
title: "LVM boot problem with Ubuntu 16.04.1 LTS"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by domriordan on 2016-07-26
Hi,

I've just installed Ubuntu 16.04.1 LTS on a brand new laptop with LVM with encryption enabled. I was able to boot into it a couple of times, I then installed docker and then went to reboot and could not, I received this message repeatedly
**Volume group "ubuntu-vg" not found**
**Can not prcoess volume group ubuntu-vg**
**Warning failed to connect to lvmetad. Falling back to internal scanning**
[B]/run/lvm/lvmetad.socket: connect failed: No such file or directory
[/B]
After about 5 minutes it drops into a BusyBox shell for me to presumably fix the issue... I also tried to re-install via USB but it could not see the hard drive to install on, only the USB. 

Does anyone know how to fix this?

---

