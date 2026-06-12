---
title: "grub boot line"
date: 2006-03-23
forum: Installation &amp; Upgrades
---

### Post by trorion on 2006-03-23
I have breezy installed on hda partition 2
I have dapper installed on hdb partition 2

what instructions do I give to my grub boot loader?  I assume it would be something like this:
label: breezy
type: image
kernel: (hd0,2)/boot/????? root=dev/hda2 resume=dev/hda2

label: dapper
type: image
kernel: (hd0,2)/boot/????? root=dev/hda2 resume=dev/hda2

is the ????? vmlinuz or something different?
:confused:

---

