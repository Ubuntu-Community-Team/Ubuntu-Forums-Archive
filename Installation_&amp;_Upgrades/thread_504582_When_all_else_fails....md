---
title: "When all else fails..."
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-07-19
I have looked for a guide and could not find one, and my post on the Hardware & Laptops forum went unanswered. The problem was that originally, I could not even boot the 7.04 Live CD on my Compaq Presario F500. I got around this with information posted at [http://ubuntuforums.org/showthread.php?t=431345&highlight=Compaq+Presario+F500](http://ubuntuforums.org/showthread.php?t=431345&highlight=Compaq+Presario+F500). Now, every time I do a reboot, I have to add the vga=792 and noapic to the kernel line thing before I boot. Is there any way to add it permanently so I can just boot? Thanks!

---

### Post by merlinus on 2007-07-19
Add the statements to the end of the kernel line in /boot/grub/menu.lst:

```

gksudo gedit /boot/grub/menu.lst

```

-merlin

---

