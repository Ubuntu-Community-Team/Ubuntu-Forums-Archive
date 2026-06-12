---
title: "Upgrade from 9.04 (64bit) to 9.10 (32bit)"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by HansS on 2009-12-01
Hi,
I need to install the 32 bit version of 9.10. Currently I have installed 9.04 64 bit, but found out that a lot of applications I use (also for my work) are not available in 64bit.

My laptop is multibooted (windows XP en Windows 7 and Ubuntu 9.04) and I use GRUB to select the appropiate OS.

How can I perform the installation on 9.10 32 bit, without destroying the XP and W7 partitions/startup ? The Ubuntu partition may be removed if nessecary.

Thanks for the help.

---

### Post by Grenage on 2009-12-01
If you boot from the disk and select your existing ubuntu partition as the destination, you can perform a clean install.  You will lose anything on that partition.

---

### Post by wojox on 2009-12-01
Yeah, doing a fresh install on your pre-existing Ubuntu partition should work. Grub2 is good at finding your other partitions and adding them.

---

