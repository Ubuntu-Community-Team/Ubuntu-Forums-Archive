---
title: "Upgraded to Hardy -&gt; does not boot with distribution kernel"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by mmmmmm on 2008-03-08
Hello. I just upgraded to Hardy to test it. It looks to be working BUT only with the kernel 2.6.24.3 i have compiled on my own from kernel.org. If i try to boot with distro kernel it does not write down into logs, stops at message "loading, please wait" , if i switch off the quiet+splash it stops on message /bild/*bildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c v2.6:USB core driver, however no kernel panic or stuck, it responds to keys and it reboots with message stopping all devices, reboot. Anyone else who is testing it for presonal interest and experiences similar behavior?

PS:edited to fix some typos, sorry for the others i did not notice

---

### Post by Vermind on 2008-04-25
Hello,
I just upgraded to the released version of Hardy. For me, neither Gutsy nor Hardy kernels boot. Behaviour is similar as in Your case. The boot process stalls after "waiting for root file system" and detecting my disks, USB and CDROM stuff.

---

