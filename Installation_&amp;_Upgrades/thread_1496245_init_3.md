---
title: "init 3"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2010-05-29
Hi
as ctrl/alt/F1-6 don't work on my system I guessed that it's x related. So i downloaded the current Nvidia driver. Now nvidia install says to exit x but doing a init 3 as root is useless
What to do? :confused:
Thanks Michael

---

### Post by ahso4271 on 2010-05-29
ok so i tried:
/etc/init.d/gdm stop

it exits x but the tty is completely messed up. Nothing to recognise at 
all!
[B](i'm booting ubuntu 10.04 with grub1 but on another suse partition)
Many thanks
Michael[/B]

---

### Post by ahso4271 on 2010-05-29
removed all grub parameter and it works.

---

### Post by CadetD on 2011-06-09
> **ahso4271 said:**
> removed all grub parameter and it works.
Can you elaborate further on what you did. Where did you remove the parameters from?

---

