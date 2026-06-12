---
title: "Another grub2 won't boot windows thread"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by jbernardo on 2010-05-03
Since some people are writing on all "Lucid's grub2 won't boot windows" threads to start a new one, here is mine. I have a asus eeepc 1101ha. With Karmic, it would boot into w7 without problems. I installed Lucid on another partition, and after that the w7 grub entry would leave me with a blinking cursor in the left top corner, and hang.
I booted with the w7 dvd, ran bootrec.exe to restore mbr and bootmgr, and the booted into w7 to confirm. It was working. Then I booted with the live dvd, mounted the lucid partition, and installed grub. Now choosing the w7 entry would ask for the boot media, and pressing any key would bring me back to the grub menu. Lucid and karmic boot without problems.
Installing grub from karmic now gave the same error. Running update-grub didn't change anything.
As I had to use w7, I booted again from the dvd, and restored again mbr and bootmgr. Booted into w7, used it, then once again to the live cd, to reinstall grub, and once again the w7 entry in grub makes grub ask for the boot media.
I've attached my boot info script.
Ah, I also played with the bootable flag for the /dev/sda1 partition, but it didn't change anything.

---

### Post by kansasnoob on 2010-05-03
I'll be darned if I can see the problem :confused:

Consider this a free bump :)

---

