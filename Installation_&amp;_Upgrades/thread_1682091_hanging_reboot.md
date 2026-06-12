---
title: "hanging reboot"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by fojam on 2011-02-05
I just installed Ubuntu 10.10 on a 25 gb partition of my portable hard drive. It asked me to reboot so I clicked on reboot. now it just hangs there with the Ubuntu wallpaper in the background and the mouse with the little loading icon on it. I am afraid to force shut it off for fear of damaging Ubuntu or my Portable Hard Drive

What do I do?

---

### Post by dino99 on 2011-02-05
while booting, edit the boot line, and remove "quiet splash" that might help to know which error it found, if that not enought, add nomodeset and/or noacpi. If you dont see the grub menu by default (case of unique Os), hold "shift" key down at end of bios process to see it.

---

