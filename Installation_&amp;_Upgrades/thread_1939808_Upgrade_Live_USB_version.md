---
title: "Upgrade Live USB version"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by qbektrix on 2012-03-12
I am using Ubuntu 10.04 on live USB. Is there any way to upgrade it to the latest version of Ubuntu. I did a lot of customisation and I dont want to redo it. Is it possible?

---

### Post by sudodus on 2012-03-12
> **qbektrix said:**
> I am using Ubuntu 10.04 on live USB. Is there any way to upgrade it to the latest version of Ubuntu. I did a lot of customisation and I dont want to redo it. Is it possible?
Please describe what kind of live USB drive it is, to make it possible to help!

- a regular static USB drive, that might as well be on a CD
- a persistent live USB drive with a casper-rw file or partition
- a 'normal' installation done to a USB drive
- or something else ...

---

### Post by qbektrix on 2012-03-12
I downloaded the iso file and created a persistent(casper-rw) live usb using [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").
Hope this info is sufficient.

---

### Post by sudodus on 2012-03-12
> **qbektrix said:**
> I downloaded the iso file and created a persistent(casper-rw) live usb using [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").
Hope this info is sufficient.
It is possible but risky to update most of the programs with a casper-rw persistent system, but as far as I understand, you cannot update/upgrade the kernel. So it is not possible to upgrade it to the latest version of Ubuntu :-(

However, 10.04 is an LTS version and it is supported until April 2013 if you want to do security updates (except for the kernel). But before doing that, I strongly recommend, that you make a backup copy of your casper-rw file.

---

