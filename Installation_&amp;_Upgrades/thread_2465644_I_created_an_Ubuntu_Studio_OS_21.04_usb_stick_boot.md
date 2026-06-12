---
title: "I created an Ubuntu Studio OS 21.04 usb stick bootable"
date: 2021-08-07
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2021-08-07
I created an Ubuntu Studio OS 21.04 usb stick bootable, to run Ubuntu Studio OS from my PC(Not install it), but the state and files created between boot sessions not kept, in other words all files created after shutdown and boot back from usb stick the OS is resets--- all lost... how make the state and files Not get deleted/reset... but persistent in the usb stick?

---

### Post by tea for one on 2021-08-07
[COLOR="#0000FF"]mkusb[/COLOR] is a very good utility to create USB sticks with persistence.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by lsepolis123 on 2021-08-07
can convert the current USB Stick now to a bootable with persistence or needed recreate it??? I think followed here to create it: [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

---

### Post by tea for one on 2021-08-07
If your base operating system is Windows 10, then you can try [https://unetbootin.github.io/](https://unetbootin.github.io/)

mkusb is an application for Ubuntu.

It is better to recreate the USB stick rather attempt a conversion.

---

### Post by guiverc on 2021-08-07
Ubuntu by default suggest `rufus` for writing ISOs to thumb-drives

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

Rufus (recent versions anyway) have the capacity to write it with persistence as well; though I've no experience doing it (I'd use `mkusb` myselfl)

Please note:  A persistent *live* system is NOT the same as an installed system; the RAM disk created that the system runs from is created at a set size, so once it's used, the system can become *unstable* (or at least *very* slow).

Ubuntu could be installed to thumb-drive; but I've not done that in recent releases (and it's not a simple task, at least not with `calamares` which I understand Ubuntu Studio 21.04 uses as installer)

---

