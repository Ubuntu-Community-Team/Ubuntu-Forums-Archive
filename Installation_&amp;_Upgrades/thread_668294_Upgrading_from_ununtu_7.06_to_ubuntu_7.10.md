---
title: "Upgrading from ununtu 7.06 to ubuntu 7.10"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by dapissarenko on 2008-01-15
Hello!

I have a notebook with

a) Windows XP and
b) ubuntu 7.06

running on it.

Now I want to upgrade ubuntu to 7.10 without breaking my 

1) windows installation and
2) the boot manager (the operating system selection, which appears when booting).

How can I upgrade ubuntu (I have a CD with ubuntu 7.10 distribution at hand) without breaking Windows and boot manager?

What things should I keep in mind?

Thanks in advance

Dmitri Pissarenko

---

### Post by Thanoulis on 2008-01-15
Just pop your 7.10 CD in and follow the steps!:)
Remember to use the partition that currently las the 7.06 installation and everything will work fine!

---

### Post by mokshadaya on 2008-01-15
Yes, upgrading from 7.04 to 7.10 should go smoothly with no issues as long as you install over the same partition that currently has 7.04.  I assume you are using GRUB by default as the boot manager.

If you have made any custom changes to GRUB I would back up a copy of it to another partition, usb drive, CD, write it down on paper, etc, etc, etc.  If you haven't made any changes to it, 7.10 should automatically detect XP and setup the boot menu appropriately.

Enjoy!!

---

