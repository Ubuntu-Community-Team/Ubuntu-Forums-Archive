---
title: "Wifi problems after 11.10 upgrade"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by artoonie on 2011-10-18
I've tried the suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=1860574&highlight=wifi](http://ubuntuforums.org/showthread.php?t=1860574&highlight=wifi)
To no avail.

lspci tells me my driver is BCM4312.
It has been disabled in "Additional Drivers" and when I try to activate, it tells me to look in /var/log/jockey.log for errors.
The relevant errors, some repeated, are:
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module     wl
WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43    : blacklisted, b43legacy: blacklisted


Any ideas? Is the card no longer supported/should I switch to ralink drivers?

---

### Post by artoonie on 2011-10-19
Solution:
Copied from this thread, modified a bit:
[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

1. Download the Broadcom drivers: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
2. Apply the patch provided at the same URL
3. Unpack and modify the ‘src/wl/sys/wl_linux.c‘:
      Line 35 (after #include <linux/etherdevice.h>) add: [INDENT]#include < linux/sched.h >
[/INDENT]   4. Compile the code with: make
   5. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
   6. Update dependencies: sudo depmod -a
   7. Modify the blacklist to include the ‘b43&#8242; and ’ssb’ drivers  /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)

Note: you may want to see if it works without step 3 and 7, I think it will, and that requires less fudging with your ubuntu internals.
The last few steps in the thread linked above weren't necessary for me.



[COLOR=DimGray]Just for search terms, my Broadcom drivers weren't working on my Dell 1545 laptop, and the Additional Drivers app would give an error when I clicked "Activate."[/COLOR]

---

