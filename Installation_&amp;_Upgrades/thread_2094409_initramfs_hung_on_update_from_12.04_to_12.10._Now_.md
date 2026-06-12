---
title: "initramfs hung on update from 12.04 to 12.10. Now hangs on adding module i810"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by virtuousd on 2012-12-13
I had to interrupt the distribution upgrade when it hung on the line:

```
update-initramfs: Generating /boot/initrd.img-3.5.0-20-generic
```

I have not been successful in getting it to complete. dpkg --configure -a hangs on the same line as the dist upgrade above.

Here is the log for when I try to run update-initramfs separately:

```
@ubuntu:~$ sudo update-initramfs -u -v
...
...
Adding module /lib/modules/3.5.0-20-generic/kernel/drivers/gpu/drm/i810/i810.ko
```

It hangs on that last line indefinitely.

---

