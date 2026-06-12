---
title: "I'm replacing SUSE with Ubuntu"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by Efwis on 2005-05-04
i am a Noob that is replacing SUSE with Ubuntu, but I have a couple of  questions regarding installing Ubuntu.

I'm running  a dual-boot ATA system with XP Home on one drive and Ubuntu will be on another.

now my questions

1. do I need to repartition and format  the linux Hard drive for Ubuntu to go on? its a 5GB hdd, which is big enough for my needs, but SuSE partitioned it to a 1.7 GB drive, don't ask me why i have no idea.

2. SuSE uses GRUB for the bootloader, do I need to worry about getting things set up so I can use Ubuntu under the dual-boot?

I'm downloading Hoary Hedgehog as we speak, so that I may install it.

---

### Post by pjbright on 2005-05-04
Efwis:

No need to pre-format - the Ubuntu installer will handle it for you.  It may not be pretty, but does work.  Ubuntu also uses GRUB, so this is also not an issue.  You may want to override the default partitioning, though, if you use a /home partition - useful if you switch distros often!

-Pete

---

### Post by Xian on 2005-05-04
[QUOTE=Efwis]1. do I need to repartition and format  the linux Hard drive for Ubuntu to go on? its a 5GB hdd, which is big enough for my needs, but SuSE partitioned it to a 1.7 GB drive, don't ask me why i have no idea.

2. SuSE uses GRUB for the bootloader, do I need to worry about getting things set up so I can use Ubuntu under the dual-boot?[/QUOTE]
1. Doesn't matter unless you plan on having an extended partition. If that is the case then I'd use the Ubuntu partitioner as it handles this procedure differently than SuSE. Both distros use parted so they are compatible.

2. You will just install Grub to the MBR during the install, and during this it will pick up your WinXP automagically.

---

