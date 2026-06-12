---
title: "'is d: a removable disk?' behavior"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by FoZFoRiC on 2012-06-06
When I tried to install ubuntu 12.04 on an old desktop that I had put in a second hard drive from a different computer, the installation asked if d: was a removable disk for some reason.  I suspect it still has a MBR from when it was primary drive in an even older computer.  

After installation was done and reboot, the system went directly to the windows xp  on c: and there was no grub loader screen at all. Using boot repair disk and repairing grub made all kinds of problems initially, but I resolved that.

**The question is:** what is the installation trying to figure out when it asked about d: being removable? What actions does it take when given a yes answer and what actions does it take when given a no answer?  I ask this because I have 4 more computers of wildly different configurations all with multiple hard drives that I plan on installing ubuntu to and want to learn more before tackling them as I may want to do a targeted cleanup of system files like MBR and other configuration files.

---

