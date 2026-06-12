---
title: "How to tell 6.10 server installer what kernel to use?"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by neurophyre on 2007-03-02
The standard linux-server kernel installed by the 6.10 installer disk is broken on VIA C3 hardware.  How do I tell it to install -386?

---

### Post by scxtt on 2007-03-02
i don't think you can change which kernel is install by default (as you're installing the OS for the 1st time) -- are you wanting to change the kernel after the initial OS load?

```
[font=courier]:> aptitude search linux-image | grep 386
i   linux-image-2.6.15-23-386       - Linux kernel image for version 2.6.15 on 3
p   linux-image-2.6.15-25-386       - Linux kernel image for version 2.6.15 on 3
p   linux-image-2.6.15-26-386       - Linux kernel image for version 2.6.15 on 3
p   linux-image-2.6.15-27-386       - Linux kernel image for version 2.6.15 on 3
p   linux-image-2.6.15-28-386       - Linux kernel image for version 2.6.15 on 3
i   linux-image-386                 - Linux kernel image on 386.[/font]
```

---

### Post by neurophyre on 2007-03-03
I need to install a 386 kernel before the installer reboots.  The system is unbootable with the standard server kernel.

---

### Post by neurophyre on 2007-03-03
I managed to boot into rescue mode, get a shell on the system and apt-get install a working 386 kernel that will do until I can build my own.

---

### Post by tomas.srna on 2007-03-18
Hello...

May I ask how did you manage to boot into rescue mode?
Because when I select the recovery mode (2nd option), i still get 686...

Thanx.

---

