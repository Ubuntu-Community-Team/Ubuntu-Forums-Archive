---
title: "cannot boot after updating dapper to 2.6.15-20-23"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by donaldd on 2006-05-30
Hi @,
Needed to upgrade to dapper to use wpa on my laptop, been quite happy for the last month, yesterday updated linux-image from 2.6.15-20 to 2.6.15-23 only to find I could no longer boot, I'm using an Asus W3V laptop. Although I have absolutely no idea why it's happening it's not an issue because I can go back to using the old image.  My problem is when installing Applications sometimes linux source or headers are needed, can I use  linux-image-2.6.15-20 with linux-headers-2.6.15-23-686,  linux-headers-2.6.15-20 does not seem to be available.

---

### Post by donaldd on 2006-05-30
Found the fix press escape and edit grup menu adding acpi=off, once you can boot into system edit /boot/grub/menu.lst to make it permanent

---

