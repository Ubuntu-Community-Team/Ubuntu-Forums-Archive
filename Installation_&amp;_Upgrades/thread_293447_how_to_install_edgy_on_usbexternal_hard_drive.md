---
title: "how to install edgy on usbexternal hard drive"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by sbindval on 2006-11-05
how do i install edgy on usb external hard drive?
the hard drive already contains windows data...which i need.
thanks,

---

### Post by .t. on 2006-11-05
Can you boot from that HD?

---

### Post by elicriffield on 2006-11-05
You would use debootstrap

I think its all explained in install guide. [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html)

Eli Criffield

---

### Post by sbindval on 2006-11-05
> **.t. said:**
> Can you boot from that HD?

Yes, I can. I need to install on the USB hardrive, but not wipe out existing data.

Thanks,
Shyam

---

### Post by .t. on 2006-11-05
Try to boot from the Live CD, and install as normal. I'm not sure what device the drive will be though. Just make sure you resize manually, not delete (automatically either), the partition(s) you want to keep.

---

