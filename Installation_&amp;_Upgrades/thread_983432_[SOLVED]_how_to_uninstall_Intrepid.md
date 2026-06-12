---
title: "[SOLVED] how to uninstall Intrepid ?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Steve_G on 2008-11-15
I dual-boot Hardy with XP but wanted to try Intrepid so I installed it in a separate partition. As I can't get wireless to work with Intrepid I now want to remove it and continue using Hardy. I can't find an uninstall option but I assume that I could just reformat the partition. My concern is what this will do to Grub - presumably Intrepid will have overwritten the previous Grub boot file?  What is the easiest (safest) way to remove an unwanted version of Ubuntu?

---

### Post by confused57 on 2008-11-15
Reinstall Hardy's IPL(Initial Program Loader) to the mbr, using the 8.04 live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Steve_G on 2008-11-16
Thanks confused57. Intrepid is no more and Grub restored :)

---

