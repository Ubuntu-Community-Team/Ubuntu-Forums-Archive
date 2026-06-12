---
title: "Copy floppy boot disk?"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by ahampton on 2005-04-20
While installing hoary I opted to have to boot from a floppy. Now I have one boot floppy. Makes me nervous. How do I generate a backup?

I tried copying the files to another floppy, but it doesn't boot.

Thanks,

Art Hampton

---

### Post by jbharrison on 2005-04-20
1) make an image file of the boot floppy:

$ dd if=/dev/fd0 of=/tmp/fd0.img

2) write image to new floppy

$ dd if=/tmp/fd0.img of=/dev/fd0

---

