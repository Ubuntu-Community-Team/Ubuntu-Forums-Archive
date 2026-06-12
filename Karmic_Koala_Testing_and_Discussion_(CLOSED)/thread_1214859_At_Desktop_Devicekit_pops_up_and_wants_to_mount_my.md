---
title: "At Desktop Devicekit pops up and wants to mount my second drive."
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-07-16
Karmic is on sdb

This is weird behaviour. If I give it the password it mounts sda1. But then if I click on sdb3 it mounts that without the password.

How do I stop this annoying behaviour.

---

### Post by xebian on 2009-07-16
> **philinux said:**
> Karmic is on sdb

This is weird behaviour. If I give it the password it mounts sda1. But then if I click on sdb3 it mounts that without the password.

How do I stop this annoying behaviour.

set timeout_timestamp=0 in sudo config.  I think visudo will get you there.

---

### Post by philinux on 2009-07-16
> **xebian said:**
> set timeout_timestamp=0 in sudo config.  I think visudo will get you there.

For now I just disabled policykit from the startup apps menu.

Why would karmic want to mount my other drive in the first place.

---

### Post by ronacc on 2009-07-16
its been acting this way for awhile , there are other threads about this , see [http://ubuntuforums.org/showthread.php?t=1201754](http://ubuntuforums.org/showthread.php?t=1201754)

---

### Post by philinux on 2009-07-17
Thanks ronnac.

---

### Post by philinux on 2009-07-17
Seems like a couple of similar bugs reported.

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448)
[https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122](https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122)

---

