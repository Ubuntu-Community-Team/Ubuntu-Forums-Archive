---
title: "Add windows OS to grub2"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by ZeldaFan on 2009-11-26
I have ubuntu karmic installed on my primary hard drive with grub2. I have another hard drive with just windows xp  installed on it. How do I add an entry to grub2 to have my second hard drive visible under grub2 (both hard drives are internal)?

---

### Post by darkod on 2009-11-26
In Terminal run
sudo update-grub

It will write few lines, usually there should be something like
Found Windows XP on /dev/sdb1

Reboot and there should be Windows XP in grub menu, try it out.

---

