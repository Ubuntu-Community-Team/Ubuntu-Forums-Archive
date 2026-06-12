---
title: "grub&gt; setup (hd0) Error 17: Cannot mount selected partition
Hel"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by rmx on 2008-02-06
Hello.

I have a system with xp and ubuntu.

I erased my ubuntu partion and restored a saved one from a backup.

I found this error before boot menu: error 17.

I run live cd (7.04) and launched a terminal:


```


grub

grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,5)

grub> setup (hd0)

Error 17: Cannot mount selected partition


```

My ubuntu partition is on sd6, and /boot/grub/stage1 existes, does anyone have a clue

thanks

RMX

---

### Post by mike1821 on 2008-02-06
Hi,

Are you using only one hard-drive (hd0)?

Have you checked the menu.lst file? Are you sure that the backup grub configuration file is the same as your latest system?

Mike

---

