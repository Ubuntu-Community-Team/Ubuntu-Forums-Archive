---
title: "Installing different versions of Linux?"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-27
Hi!

I'm just curious as to how to go about installing for dual boot Ubuntu (already installed) and another Linux distribution to try out something new. Basically, I guess my question comes down to this: once both are installed, how do I boot up one or the other?

---

### Post by jasmuz on 2005-10-27
Modifying your /boot/grub/menu.lst file, so it can point to the other kernel of the diferent distribution.

---

### Post by RubenGonc on 2005-10-27
[QUOTE=SuperDiscoMachine V.5.7-3]Hi!

I'm just curious as to how to go about installing for dual boot Ubuntu (already installed) and another Linux distribution to try out something new. Basically, I guess my question comes down to this: once both are installed, how do I boot up one or the other?[/QUOTE]


You just need to add an entry of the new linux distribuition installed to GRUB or lilo wathever you use.

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-27
Hmmm...thanks. But do you add just the name of the distro., or the whole path to its kernel? Also, do you need to set aside a whole new partition, or can it use the same data as Ubuntu?

---

