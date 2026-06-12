---
title: "How to change OS selection menu in bootup to C drive"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by arunb on 2008-09-11
Hi,

How do I make the OS selection menu in bootup screen to run from my C drive instead of a USB pen drive (the pen drive contains the Ubuntu installation).

thanks
arunb

---

### Post by iaculallad on 2008-09-11
You have to edit your GRUB file:

```
gksudo gedit /boot/grub/menu.lst
```

---

