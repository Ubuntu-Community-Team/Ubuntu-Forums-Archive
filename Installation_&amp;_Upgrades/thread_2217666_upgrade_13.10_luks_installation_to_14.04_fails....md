---
title: "upgrade 13.10 luks installation to 14.04 fails..."
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Mr.Gosh on 2014-04-18
after upgrading the 13.10 luks encrypted installation. the isntaller recognizes the old installation und aupgrades....

but after the reboot grub loads and after starting there is a black screen followed bz>

```
Gave up waiting for root device. Common problems>
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/ubuntu--vg-root does not exist. Dropping to shell!

Busybox.....
(initramfs)


```

did anyone sucessfully upgrade an luks installation? I think there is the problem...

---

### Post by nejc.gasper on 2014-11-02
Sorry to dig this up, but I would need to upgrade from 13.10 to 14.04. I am afraid since reading this though. There is no other feedback to be found. So anyone else managed to upgrade? Was this situation salvageable?

Edit: I decided to just go with it. Everything is fine on my end.

---

