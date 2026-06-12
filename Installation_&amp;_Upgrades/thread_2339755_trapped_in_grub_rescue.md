---
title: "trapped in grub rescue"
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by ahdaiu on 2016-10-12
First of all: I messed up.

I deleted a broken distro in Windows 10, then I installed a new distro in the free partition slot. I restarted the computer and now I'm in grub rescue(Because I attached the Boot-thing to my partition instead of my drive). I can get into Linux (through set boot(msdos..)..) but I cant get into Windows. I originally wanted to boot via easyBCD instead of Grub (and I would still like to if possible) but as long as I can access both Windows and Linux im Ok with it. What are my options to fix this mess?

---

### Post by ahdaiu on 2016-10-12
Ok, I fixed it by reinstalling my Linux (with boot attached to drive) and running boot-repair.

---

