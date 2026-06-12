---
title: "loopback disabled by default?"
date: 2004-10-29
forum: Installation &amp; Upgrades
---

### Post by ouminan on 2004-10-29
I tried to mount an iso image recently with:

```
sudo mount NeverwinterNights1-linux.iso /mnt/iso/ -t iso9660 -o loop
```

and I get the error message:

```
mount: could not find any device /dev/loop#
``` 

Seems like loopback is disabled by default in the kernel.  If it is, is there a way to enable it?

Thanks!

-Andrew

---

### Post by jdong on 2004-10-29
Did you **modprobe loop**?

---

### Post by ouminan on 2004-10-29
That did the trick!

Thanks for the help... time to 'man modprobe' and learn more about linux...  :razz: 

Thanks!!

---

