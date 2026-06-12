---
title: "No /dev/rtc for VMWare"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2008-10-16
VMware Workstation is having a problem because of no /dev/rtc in Intrepid.

> The host high-resolution timer device (/dev/rtc) cannot be opened (No such file or directory).  It appears that the device is not configured into your kernel.  Without this device, the guest operating system can fail to keep time correctly. To avoid this problem, reconfigure your kernel with CONFIG_RTC included, or see [http://vmware.com/info?id=34](http://vmware.com/info?id=34).

[https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/284602](https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/284602)

---

### Post by natros on 2008-10-21
there is a patch
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/252924/comments/5](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/252924/comments/5)

---

