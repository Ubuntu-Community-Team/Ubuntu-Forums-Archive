---
title: "dual boot with windows"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by sroy on 2007-09-23
Hello there,

I am trying to install windows XP on my dell machine which currently runs ubuntu linux on it so that I could configure it as a dual boot. However, when i hit a key after the "press any key to boot from the cd" is displayed, nothing happens. All the posts that I have seen so far discusses the opposite scenario (ubuntu on existing windows XP and not windows XP on existing ubuntu).

Does anybody have any pointers?

---

### Post by Tautoa on 2007-09-23
The reason why you havn't seen much discussion on doing it this way, is that installing Ubuntu on an Xp machine is easier.
When you install Windows, it will install it's own bootloader over GRUB, and the Windows one won't recognise Linux.
When you install Ubuntu, it overwrites it with GRUB, which does recognise Windows, meaning that you can dual-boot.
If you were going to install Windows on a Ubuntu machine, you would have to reinstall GRUB afterwards.

As for the other problem... could be a dodgy CD?

---

