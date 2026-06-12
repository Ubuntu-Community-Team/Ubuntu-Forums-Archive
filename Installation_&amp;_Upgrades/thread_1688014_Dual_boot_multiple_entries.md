---
title: "Dual boot multiple entries"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by tankmil on 2011-02-14
Hi,

I have both Win 7 and Ubuntu installed on my PC.

For some reason, when I turn the computer on, and have to choose what to load, windows or Linux, there are multiple entries for Ubuntu:

Ubuntu, with Linux 2.6.35 - 25 - generic
Same thing but 24
Same thing but 23
Same thing but 22

there is:
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115)
Windows Vista (loader) (on /dev/sda2)
Windows 7 (loader) (on /dev/sda2)

Could someone please tell me:
1. Why are there 4 boots of Linux to choose from, and can I get rid of the older ones (24 - 22)
2. What is Vista doing there?

Thanks.

---

### Post by drs305 on 2011-02-14
The extra linux entries are older kernels. Each time a new kernel is added the menu is expanded, with the older kernel remaining on the menu. The newest kernel is normally the top one.

Most users keep one older kernel on the menu (one they know works). If you would like to remove older kernels from your system (which will also remove them from the menu), I highly recommend using a GUI app called Ubuntu Tweak. It's very simple to clean up older kernels and can do lots of other routine system tasks as well.

Here is a guide on using it to remove older kernels:
[HOWTO: Remove Older Kernels via GUI ]("http://ubuntuforums.org/showthread.php?t=1587462")

I'm not a Windows user but I believe the W7 bootloader piggybacks on the Vista one when Vista is present during the W7 installation.

---

