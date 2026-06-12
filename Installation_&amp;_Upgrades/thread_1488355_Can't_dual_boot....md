---
title: "Can't dual boot..."
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by olwe on 2010-05-20
Just installed Kubutu 10.04 on my Toshiba laptop. Smooth install. Chose default install for partitioning (it took 50 gb of 130 gb free). But when I tried to boot into the original Windows 7, the Win7 boot screen (swirling Win symbol) goes for a second or two, then a blinking crash screen, then reboot.

The Grub offers me 3 options for Windows booting: Win7 on sda1, Win7 on sda2, and Vista on sda3. Both Win7s crash after "swirling" for a few seconds, and the Vista option wants to do a Win repair. Any ideas how I can get into my old Win7?

---

### Post by olwe on 2010-05-20
I tried Grub choice "Windows 7 on sda1" and I got a screen saying "Start Win normally" or "Repair..." I chose to repair. It futzed around "fixing damaged files," then it rebooted to Grub. I chose Win7 on sda1 again -- and it booted into Win7 just fine. Tested booting into ku10.04, then Win7 again. Everything fine. Problem solved.

But why did I have this problem?

---

### Post by oldfred on 2010-05-20
win7 does not like to be resized and has to run repairs to adjust to its new size. It is usually better to use the windows tools in MMC to adjust Vista or 7 partitions, but even then you need to reboot several times for it to adjust.

---

