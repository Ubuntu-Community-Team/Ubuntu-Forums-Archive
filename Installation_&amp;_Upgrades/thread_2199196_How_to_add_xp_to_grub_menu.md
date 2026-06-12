---
title: "How to add xp to grub menu"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by Hvidemose on 2014-01-12
Hi

I installed Xubuntu alongside XP by creating a swap, an installing on another partition. The problem now is, that I cant enter my XP from the start up GRUB menu.

Is there a way to ad it to this menu?

Cheers :-)

---

### Post by deadflowr on 2014-01-12
Run
```
sudo update-grub
```
from a terminal, and see if any entries for Windows show up.

If not you might need to install os-prober.
Or make the os-prober script in /etc/grub.d executable.

But I would bet that running the above command should get the XP install to appear in grub.

Post the output if any problems occur.

---

### Post by Hvidemose on 2014-01-12
Thanks mate!

---

