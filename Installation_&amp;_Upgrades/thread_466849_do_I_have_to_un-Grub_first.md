---
title: "do I have to un-Grub first?"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by muka on 2007-06-07
I have this odd situation where I upgraded from the previous version to 7.04 using the 'alternate' CD. And there is something about it that doesn't make me too happy at all.

To cut a long story short, if I re-install with the 'desktop' CD what happens with Grub as my install is dual-boot.

Do I have to first run my recovery CD and restore my MBR, or will the Grub file get properly ove-rwritten without it becoming a longer list of items (along with the present selection).

Much thanks
Muka

---

### Post by mitch.c on 2007-06-08
*I THINK*, that if you follow the prompts carefully, grub should be reinstalled and should pick up on your other installation (Windows?).

If you are just trying to switch to the desktop version however, why not just use apt-get:
```
$ sudo apt-get install ubuntu-desktop
```
[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

