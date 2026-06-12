---
title: "After upgrade to 2.6.24-19 laptop wont boot"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by raiwo on 2008-06-19
After upgrading to 2.6.24-19 my machine gives me following errorin bootup ```
udev-event[1547]:run_program:'/sbin/modprobe' abnormal exit 
```and goes to busybox. After doing reboot it did this again, just gave different udev-event numbers, like [1533] & [1542] 

2.6.24-18 works just fine, using toshiba satellite-A200 laptop

so, how to fix this?

---

### Post by jualin on 2008-06-19
try booting with an older kernel. To do this select the older kernel from the GRUB Menu when your computer starts. Hope this helps!

*edit* Is this a Wubi installation? If it is follow the Wubi Guide which talks about the BusyBox error, which is usually because of a Hard Reboot [https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623]("https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623")

---

### Post by raiwo on 2008-06-19
> **jualin said:**
> try booting with an older kernel.
at the moment i am using 2.6.24-18 kernel & this is not a wubi install.

---

