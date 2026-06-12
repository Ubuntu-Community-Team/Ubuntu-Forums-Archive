---
title: "Grub menu help"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by Sainarx on 2006-07-08
I have installed the kernel image for 686 Pentium based machines on my PC, with Celeron.And when I turn on my PC, Grub always ask me what to boot(686 or 386 kernel).My question is how can I make it to boot automaticly the 686 kernel, without asking me every time?And how can I remove the 386 image without damaging my system and is that posable?

---

### Post by atoponce on 2006-07-08
You can remove the 386 using Synaptic.  It will automatically update Grub for you.

---

### Post by Sainarx on 2006-07-08
Thanks for the help but I have another problem with synaptic.Every time when I update my system, install programs or uninstall something I get this error: [http://img82.imageshack.us/img82/2372/screenshot8nl.png](http://img82.imageshack.us/img82/2372/screenshot8nl.png)

---

### Post by Sainarx on 2006-07-08
> **atoponce said:**
> You can remove the 386 using Synaptic.  It will automatically update Grub for you.
...and I still have that menu on boot time with 3 options (keren-686;kernel-686 recovery mode;memory test) :|

---

### Post by atoponce on 2006-07-08
You should keep the recovery mode and memory test in Grub, in case you ever need those tools.  The kernel-686 should be highlighted by deualt, and boot automatically after 10 seconds, unless you are dual booting with Windows and have that selected as the default.

---

