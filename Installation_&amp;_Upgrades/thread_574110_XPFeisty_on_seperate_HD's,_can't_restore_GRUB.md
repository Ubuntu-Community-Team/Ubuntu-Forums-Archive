---
title: "XP/Feisty on seperate HD's, can't restore GRUB"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by tbrown11 on 2007-10-12
I've followed a few guides on restoring GRUB after installing XP, all goes well, but then the Windows boot loader takes over on boot and goes straight to XP. I have XP on sda, Feisty on sdb. My assumption is that while I've restored GRUB on sdb, the MBR is on the Windows disk (sda).. i'm afraid to go ahead and write GRUB to sda out of fear of screwing both up and not being able to boot up at all. How can I move forward while assuring that I'll be able to boot both afterwards? Thanks in advance for your help.

Fixed: Used SuperGrub cd to overwrite MBR

---

