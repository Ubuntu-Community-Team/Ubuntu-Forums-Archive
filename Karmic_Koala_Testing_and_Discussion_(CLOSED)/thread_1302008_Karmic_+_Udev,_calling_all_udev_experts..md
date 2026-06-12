---
title: "Karmic + Udev, calling all udev experts."
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sefs on 2009-10-26
It worked correctly for me under jaunty.

Here is the problem.

I installed vmware. vmnet0 was created in /dev with ownership root:root

I want to have vmnet0 with ownership root:vmware-vmnet0

So I "cp -rp /dev/vmnet0 /lib/udev/devices/" which created vmnet0 in /lib/udev/devices then I set the ownership and permissions as I want.

But on reboot vmnet0 is created in /dev with incorrect ownership and permissions and does not reflect the vmnet0 changes found in /lib/udev/devices/vmnet0.

This would have worked in jaunty but not karmic.

---

