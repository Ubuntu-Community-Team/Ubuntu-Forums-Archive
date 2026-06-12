---
title: "Edgy Startup Screen"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by n8qxb on 2006-10-30
Does anyone know how to have Edgy startup like Dapper. I prefer to see what's happening as it boots up?

Thank you

---

### Post by bmorency on 2006-10-30
> **n8qxb said:**
> Does anyone know how to have Edgy startup like Dapper. I prefer to see what's happening as it boots up?

Thank you

What you will want to do is look in this file: /boot/grub/menu.lst
Make sure to edit it as root.
Look for a section that looks like this below. What you should do is put a '#' infront  of the word splash on the line beginning with kernel and at the beginning of the line that says 'quiet' only. When i tried it the splash screen was goen but it didn't list things like it did in dapper. it might be edgy uses upstart instead of sysvinit. does anyone know if that what it is for sure?

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,6)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet #splash
initrd          /initrd.img-2.6.17-10-generic
#quiet
savedefault
boot

---

