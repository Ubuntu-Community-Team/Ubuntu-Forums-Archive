---
title: "Change GRUB hard drive"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by CC Inc on 2012-02-03
Hi,

I ordered a ide to Usb converter, and when I plug my ubuntu install drive into the Usb port, ubuntu cannot seem to boot. How can I configure GRUB to boot ubuntu from the Usb drive?

---

### Post by PatrickD-52761 on 2012-02-04
> **CC Inc said:**
> Hi,

I ordered a ide to Usb converter, and when I plug my ubuntu install drive into the Usb port, ubuntu cannot seem to boot. How can I configure GRUB to boot ubuntu from the Usb drive?

What error messages do you get? And do you have an IDE drive still in the computer (with GRUB installed on it)?

In theory, if your BIOS supports booting from an external USB drive, it should boot up. But, you probably have to move that device to the first position in your boot list (or press some key to get a Boot Menu-- most likely F10 or F12).

Without knowing what errors you get, if any, it's almost impossible to tell if it's a Grub issue, a BIOS issue, or some other issue (like a loose connection).

Have a great day:)
Patrick.

---

