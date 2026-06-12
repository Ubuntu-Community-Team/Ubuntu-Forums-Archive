---
title: "Update Instillation Interrupted - No boot"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by micha8l on 2012-11-13
Hi... today I broke my system by trying to upgrade from Ubuntu 10.04 to 12.04. Everything was going fine, the upgrade downloaded, I was half way through the instillation and the *power cut*. I attempted to boot the system back up and* Boot failure message...*

```

udevd[67]: error: runtime directory '/run/udev' not writable, for now falling back to '/dev/.udev'
Gave up waiting for root device.
Common Problems:
-Boots args (cat /proc/cmdline)
- Check rootdelay= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls/dev)

ALERT! /dev/dsk/by-uuid/eb8ccee2-1d19-4979-8797-bd36f313c3e2 does not exist. Dropping to a shell!
BusyBox V1.13.3 (ubuntu 1:1.13.3-1ubuntu11)) built in shell (ash)
(initramfs)_

```Luckily enough I have a 10/04 LIVE CD handy so was to use the "Try Ubuntu" feature to gain access to the Internet.

I'd be very grateful if anyone could help me with this!

---

### Post by nathan.the.sane on 2012-11-13
Did you back up before updating? If not, can you open any of the old partitions from the LiveCD and get the data? 

If you're backed up I would just start a new clean install, it should boot after that. I think the problem is that the updater was in the middle of changing everything when it was interrupted, and now some stuff isn't where the old install is expecting it to be.

---

