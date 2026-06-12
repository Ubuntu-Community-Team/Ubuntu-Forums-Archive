---
title: "generic vs generic default"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by Curlydave on 2005-05-21
when I load up GRUB, which should I load, "generic" or "generic (default)"?

---

### Post by Sam on 2005-05-21
[QUOTE=Curlydave]when I load up GRUB, which should I load, "generic" or "generic (default)"?[/QUOTE]
If you have only one kernel, they should be the same.

Have a look in /boot/grub/menu.lst to list your boot list and their options.

---

### Post by Curlydave on 2005-05-21
K, so this is normal to have duplicates?

---

### Post by Sam on 2005-05-21
Yes. In /boot there is a "vmlinuz" symlink which refers to the last kernel installed (or the default one). "vmlinuz-old" is a backup of the kernel if you install an another, and there are the kernel images. So it's normal to see one entry in menu.lst for the default (which refers to kernel <version xyz>) and an another entry for the kernel <version xyz> directly.

(hope you understand what I said :?)

---

