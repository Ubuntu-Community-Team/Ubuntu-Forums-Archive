---
title: "ubuntu-edgy grub problems"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by abeodesee on 2006-12-22
i've got problems with grub on edgy,
on installing i choose install on first sector of partition /dev/sda6 as i plan to access grub from my windows boot menu.
problem is that grub creates in the menu.lst:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

easy to fix with a live-cd,
i was wondering if it possible to update grub before using in on the dvd installer

cheers

---

