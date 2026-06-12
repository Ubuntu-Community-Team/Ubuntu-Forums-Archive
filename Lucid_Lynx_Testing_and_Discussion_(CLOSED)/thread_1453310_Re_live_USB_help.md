---
title: "Re: live USB help"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jis on 2010-04-13
I made a live usb of xubuntu 10.4 beta2 by unetbootin. But if I install updates or additional software, they are not present in the next boot. How do you update a general live usb easily?

---

### Post by lisati on 2010-04-13
Moved to Lucid Lynx Testing and Discussion

---

### Post by VMC on 2010-04-13
> **jis said:**
> I made a live usb of xubuntu 10.4 beta2 by unetbootin. But if I install updates or additional software, they are not present in the next boot. How do you update a general live usb easily?

I think you want persistence. Check [_here_]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") and [_here_]("https://help.ubuntu.com/community/LiveCD/Persistence") for some info.

---

### Post by psyke83 on 2010-04-13
> **jis said:**
> I made a live usb of xubuntu 10.4 beta2 by unetbootin. But if I install updates or additional software, they are not present in the next boot. How do you update a general live usb easily?

Yes, you need persistence. Please keep in mind that while the links that VMC have provided are quite useful if you wish to learn how to manually enable persistence, there are much more user-friendly solutions - the Startup Disk Creator can enable persistence mode in its interface (which is not possible in unetbootin).

For a while I was using an persistence installaton from a USB drive (as my internal drive was broken). While it did work more or less, I encountered several issues, such as certain files mysteriously getting deleted and corrupted files when new packages were installed.

IMHO, persistence is only meant for light usage (such as saving a few documents), and you should not rely on this mode for a real installation. *Especially* for a development release - when you upgrade a package on a persistent installation, there are now two versions of the files on your system - the older files in the read-only casper image (which cannot be removed), and the newer files in the read-write casper persistent image. The merged (read-only and read-write) filesystem will magically "hide" the older files, but they are still occupying space on your USB drive.

You do realize that it's possible to do a "full" install to a USB drive (if the drive has enough space), right?

---

### Post by VMC on 2010-04-13
> **psyke83 said:**
> Yes, you need persistence. Please keep in mind that while the links that VMC have provided are quite useful if you wish to learn how to manually enable persistence, there are much more user-friendly solutions - the Startup Disk Creator can enable persistence mode in its interface (which is not possible in unetbootin).

For a while I was using an persistence installaton from a USB drive (as my internal drive was broken). While it did work more or less, I encountered several issues, such as certain files mysteriously getting deleted and corrupted files when new packages were installed.

IMHO, persistence is only meant for light usage (such as saving a few documents), and you should not rely on this mode for a real installation. *Especially* for a development release - when you upgrade a package on a persistent installation, there are now two versions of the files on your system - the older files in the read-only casper image (which cannot be removed), and the newer files in the read-write casper persistent image. The merged (read-only and read-write) filesystem will magically "hide" the older files, but they are still occupying space on your USB drive.

You do realize that it's possible to do a "full" install to a USB drive (if the drive has enough space), right?

Exactly. I tinkered around with persistence for a while and decided it wasn't for me.

---

