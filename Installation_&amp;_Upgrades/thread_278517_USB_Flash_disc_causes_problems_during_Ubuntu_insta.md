---
title: "USB Flash disc causes problems during Ubuntu install"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by miceagol on 2006-10-16
I accidentally installed Ubuntu the other day with a usb flash drive connected. It brought me the following errors at first boot
```

Uncompressing linux... Ok, booting the kernel
Segmentation fault
Segmentation fault
0Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
udevd-event[1692]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1695]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1697]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1699]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1701]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1703]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1705]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1707]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1709]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1711]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1713]: run-program: '/sbin/modprobe' abnormal exit
udevd-event[1715]: run-program: '/sbin/modprobe' abnormal exit
Segmentation fault

Alert! /dev/hdb1 does not exist. Dropping to a shell!

```
When I afterwards did a new try to install Ubuntu with the flash drive removed, the forementioned error didn't occur.

Is this a known bug, or should I report it somewhere? If so, where? I think it's important to get rid of such small issues, as new linux users would have great problems knowing what went wrong, and thus we risk loosing potential new linux users. ;)

---

### Post by K.Mandla on 2006-10-16
It's possible it's been seen before; the place to check is at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) ... 

I have seen this issue on other Debian-based distros, but hadn't noticed it with Ubuntu. :-k

---

### Post by miceagol on 2006-10-16
Thanks for the link. Didn't find a similiar problem posted there, so I posted the [possible bug]("https://launchpad.net/distros/ubuntu/+bug/66459"). :D

---

