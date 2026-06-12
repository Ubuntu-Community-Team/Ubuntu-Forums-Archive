---
title: "How to rediscover hardware?"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by pleriche on 2011-01-15
I have 10.10 running on an old laptop with a broken hinge. If I move the hard disk to another laptop with a good hinge and different video (and other) hardware, how can I reset Ubuntu to force it to rediscover the hardware and install the right drivers? Were I to move it back again, would it simply detect the old hardware and automatically pick up the old drivers?

Regards - Philip

---

### Post by dino99 on 2011-01-15
that is what each boot do automatically, but remove xorg.conf (if you have one) now the kernel directly deal with X

---

### Post by pleriche on 2011-01-15
Thank you - that's encouraging. And if I initially put the hard disk on a USB adapter to try, should it boot ok, or will it now appear as sda2, confusing the fstab?

---

### Post by dino99 on 2011-01-15
about usb adapter, it depend of the hardware inside it, and how the bios will recognise it. Look at usb bios settings and you need to know if the bios is able to boot from usb or not.
Let fstab as simple as possible: swap + boot partition, nothing else. Only set boot order into the bios.

---

