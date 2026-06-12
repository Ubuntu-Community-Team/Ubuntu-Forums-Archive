---
title: "Dropping to a shell! problem solved"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by damotor on 2006-07-31
I just updated from breezy to dapper and after restarting the system load stops at "waiting for root file system...", after waiting for some minuts I get a terminal saying "ALERT! /dev/hda6 does not exist. Dropping to a shell!", at this point I tried some solutions posted here (none worked).
But this worked for me: restart your computer, in the grub menu select the "Ubuntu, kernel 2.6.15-26-686" line and hit the e key, now select the " /boot/vmlinuz-2.6.15-26-686 root=/dev/hdaX ro quiet splash" and press e, in my case this line was " /boot/vmlinuz-2.6.15-26-686 root=/dev/hda6 ro quiet splash" but there was no /dev/hda6 in my /dev, so I changed it for " /boot/vmlinuz-2.6.15-26-686 root=/dev/hda5 ro quiet splash" as my linux partition is the last, restarted and... worked until starting the X.
I looked at the log and modified the /etc/X11/xorg.conf changing the driver to "vesa".
And that's all, now I'm writing from Dapper ;-)

---

