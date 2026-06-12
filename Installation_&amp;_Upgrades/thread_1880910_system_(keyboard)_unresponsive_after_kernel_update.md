---
title: "system (keyboard) unresponsive after kernel update"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by cpbl on 2011-11-14
I have two partitions containing Ubuntu (11.04 and 11.10).   They each have a /boot/grub directory.
Only one of them seems to get actually updated when a new kernel is installed from an apt update (ie the one on the respective partition that's being updated).

Only one of them (the one in the 11.10 partition) seems to get used during booting. Thus, when I update the kernel in the other partition (11.04), the grub.cfg that gets updated has no effect on the grub that gets used in booting.

This seems really dumb. Surely the updater can find out which partition is the master or whatever, and update appropriately? Or else the grub should/could be linked to the grub folder on the other partition?  I'm not confident of a workaround for this..


In any case, I just did the 11.04 kernel update that went out and now when I boot into it, the system comes up with blank screen and unresponsive keyboard. I can ssh in and reboot, but there's no local login possible.
I don't really know whether that's related the grub problem, because I have tried to copy over the grub lines and boot into the new kernel but I get the same problem.

Anyone else with this disaster? Or advice?

---

### Post by BillyBoa on 2011-11-14
It's like trying to create a double head snake. It would be very interesting.....

---

