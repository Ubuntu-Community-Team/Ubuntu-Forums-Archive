---
title: "ubuntu does not boot anymore"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by ubuhauke on 2010-04-17
On my office pc I installed Kubuntu 10.04 beta 1 amd64 onto the second hard drive. There is already Kubuntu 8.04 on another partition. I used it for a few days, configured some things an installed VMware Player 3.01. Everything was fine until last Monday, when the system simply did not boot.

It happens nothing, just a little bit (1 sec) hard drive activity and then a black screen. There is nothing new in any log file (inside /var/log). I can turn off the computer by a short press on the power button, which is not possible when linux really is booted. 

This affects all 3 kernels that are installed on that partition. The old installation (8.04) on the same hard drive still works fine. 

It seems not related to grub, since I reinstalled grub 1 and made an entry for the new system. It still freezes on boot attempt. 

Any idea what might have happened or how I can debug this is appreciated.

---

