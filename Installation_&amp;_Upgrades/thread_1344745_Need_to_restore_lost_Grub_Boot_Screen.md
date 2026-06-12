---
title: "Need to restore lost Grub Boot Screen"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by explorer716 on 2009-12-03
Postby explorer716 on Thu Dec 03, 2009 2:52 pm
I have a PC with two hard drives. I run Windows on one drive and Ubuntu 9.10 on the other. I had a Grub boot screen that at startup allowed me to choose which OS I wanted to use.

Yesterday, I upgraded from Vista to Windows 7 and in the process it erased my Grub boot screen leaving me no way to access Ubuntu. Is there a way I can restore my Grub screen without having to reinstall Linux Mint?

Thank you

---

### Post by darkod on 2009-12-03
Do you know on which partition is your Ubuntu 9.10 root? And did you have separate /boot partition?

---

### Post by wojox on 2009-12-03
[Reinstall Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by raymondh on 2009-12-03
> **wojox said:**
> [Reinstall Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

+1

Windows overwrote the MBR and installed its' bootloader on the MBR of the 1st HD to boot (as set in BIOS).

---

### Post by presence1960 on 2009-12-03
I would install GRUB 2 to Ubuntu disk, leaving windows bootloader on windows disk. Then switch the Ubuntu disk to boot first in hard disk boot order in BIOS.

---

