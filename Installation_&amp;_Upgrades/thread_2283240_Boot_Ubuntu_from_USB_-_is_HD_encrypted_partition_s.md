---
title: "Boot Ubuntu from USB - is HD encrypted partition safe?"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by markh1289 on 2015-06-20
Hi All,

On current model HP laptop Win8.1 is installed with disk encryption.
Occasionally I want to be able to use the laptop hardware for a different purpose.
If I boot it to Ubuntu 14 on a USB drive and make no attempt to read or write to the encrypted disk, will the Win8.1 installation remain safe from corruption by Ubuntu?

Regards, MH

---

### Post by dino99 on 2015-06-20
if you boot from a live usb, then you work inside the ram (and swap if needed & activated by yourself), and if you does not explicitly mount the hdd, then ubuntu will not be aware of its existance ;)

---

### Post by sudodus on 2015-06-20
Short answer: Yes.

Longer answer: Ubuntu (booted from USB) will not write to the internal drive by itself. If you ***want to***, you can try to mount the Windows partition, but if it is encrypted, you will probably fail. If you ***want to***, you can use gparted and remove the Windows partition (and create new partitions for Ubuntu), but I don't think you will do that by mistake, so yes, the Win8.1 installation will remain safe from corruption by Ubuntu.

---

### Post by markh1289 on 2015-06-20
Thanks very much for your replies

---

