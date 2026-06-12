---
title: "Upgrade from 10.04 resulted in failure [fixed]"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by ethan1el on 2011-08-03
Hey everyone, I was using 10.04 Server LTS when I decided to do an upgrade.

I'm using fakeraid and my boot path is /dev/mapper/isw_ecdhgaacgh_Volume01
After running the "do-release-upgrade" and rebooting, the boot failed with an error and a busybox with "ALERT! /dev/mapper/isw_ecdhgaacgh_Volume01 does not exist".

Somewhere along the upgrade process from 10.04 to 11 the actual root switched names from /dev/mapper/isw_ecdhgaacgh_Volume01 to /dev/mapper/isw_ecdhgaacgh_Volume0p1. I figured that out, when I did "ls /dev/mapper" in the busybox. So basically, my menu.lst still had the "01", but the new kernel was using "0p1".

Well, it wasn't that hard to fix. I rebooted the system with the old kernel (which was luckily still available in menu.lst), then changed the paths in /boot/grub/menu.lst and /etc/fstab from /dev/mapper/isw_ecdhgaacgh_Volume01 to /dev/mapper/isw_ecdhgaacgh_Volume0p1 and rebooted again.

Voila, fixed. But definately, things like this should not get into the upgrade stream. My production server was down for an hour as a result.

---

