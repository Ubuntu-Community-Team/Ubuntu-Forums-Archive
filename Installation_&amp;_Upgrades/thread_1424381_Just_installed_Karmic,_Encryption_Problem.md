---
title: "Just installed Karmic, Encryption Problem"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by uRock on 2010-03-07
I just reinstalled Karmic on my Netbook and I decided to use the alternate disk so that I could encrypt my /home. The install went well. I did the updates and restarted, now it doesn't boot I get this on the screen;

[I]udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc.cmdline)
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-wild/uuid/*address* does not exist. Dropping to shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of buit-in commands.

(initramfs) _[/I]

What do I do to get this fixed?

Thanx,
Ronnie

---

### Post by uRock on 2010-03-07
Selecting the 2.6.31-20 kernel in restore mode= fail
Selecting the 2.6.31-14 (original) kernel boots fine.

---

### Post by uRock on 2010-03-07
I fixed it. The update manager aperently popped up the restart now or later window too early and I clicked. It wasn't done with updates.
I ran ```
sudo dpkg --configure -a
``` and now all is good.

---

