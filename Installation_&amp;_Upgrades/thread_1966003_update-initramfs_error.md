---
title: "update-initramfs error"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by masuch on 2012-04-26
Hi,

When I run:

sudo update-initramfs -u
and got error:

update-initramfs: Generating /boot/initrd.img-3.3.1
grep: /boot/config-3.3.1: No such file or directory
WARNING: missing /lib/modules/3.3.1
Device driver support needs thus be built-in linux image!
WARNING: Couldn't open directory /lib/modules/3.3.1: No such file or directory
FATAL: Could not open /lib/modules/3.3.1/modules.dep.temp for writing: No such file or directory
FATAL: Could not load /lib/modules/3.3.1/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.3.1/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.3.1/modules.dep: No such file or directory



This happened when I remove this kernel which I do not need it any more. Is there any way how to fix it ?

thank you for any help,
kind regards,
Martin

---

### Post by masuch on 2012-04-27
OK, I temporarily copied directory from another /lib/modules
and copied another config file - so warnings disappeared but I would like to rid off it anyway.

Does anybody know how to persuade update-initramfs -u to remove it permanently ?

thank you,
regards,
M.

---

### Post by masuch on 2012-05-10
solved by
update-initramfs -d -k 3.3.1

---

