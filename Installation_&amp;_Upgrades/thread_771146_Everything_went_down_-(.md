---
title: "Everything went down :-("
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by pnti on 2008-04-27
I upgraded Ubuntu on various computers and everything went well with one exception (of course on my own computer). Please take a look at the picture below and suggest any remedy.

[[IMG]http://img232.imageshack.us/img232/1825/dsc03381sg0.th.jpg[/IMG]](http://img232.imageshack.us/my.php?image=dsc03381sg0.jpg)

---

### Post by deragon on 2008-04-27
Mmm...  You are one unlucky guy.  Seams that the kernel (or a module within) does not like your hardware.  In grub, you might disable acpi and other subsystems (check Google; I do not remember the syntaxe).  Else, try the Live CD if it is reproduceable.  If it works, try the same parameters on your system.  Try to get the same kernel installed.

Good luck,
Hans Deragon

---

