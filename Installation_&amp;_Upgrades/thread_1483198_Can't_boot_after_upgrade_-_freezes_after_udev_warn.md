---
title: "Can't boot after upgrade - freezes after udev warnings"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by N-s-K on 2010-05-14
After an upgrade yesterday (from 9.10 to 10.04) and a reboot, my computer is stuck in the bootsplash:
> 
fsck from util-linux-ng 2.17.2
udevd[2866]: can not read '/etc/udev/rules.d/z80_user.rules'

/dev/sda1: has gone 371 days etc etc etc...
I've tried the solution posted here:
[http://ubuntuforums.org/showthread.php?t=1441810&page=4](http://ubuntuforums.org/showthread.php?t=1441810&page=4)

But my /etc/fstab doesn't contain any > none        /proc/bus/usb    usbfs    auto,devmode=0666    0    0Any idea ?

---

