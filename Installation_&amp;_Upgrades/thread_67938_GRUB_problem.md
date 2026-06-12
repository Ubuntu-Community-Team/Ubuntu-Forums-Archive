---
title: "GRUB problem"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by Gobbla on 2005-09-21
[COLOR=Red]EDIT: Problem Solved[/COLOR]

Okay I've installed Ubuntu Hoary on my laptop (IBM ThinkPad R40) and the installation runned smoothly. I installed GRUB in the MBR and rebooted. Then this error comes up when GRUB is loading: 
GRUB Loading stage1.5. 
GRUB loading, please wait... 
Error 18

[QUOTE=Debian.org]6. Grub Error 18

Situation

Code Listing 6.1: Grub Output

kernel (hd1,4)/bzImage root=/dev/hdb7

Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). [/QUOTE] 
The problem is that I cannot flash BIOS (no floppy drive) and i cant move the /boot partition since its in the MBR (if I haven't misunderstood something). So what should I do? I have Windows XP in the first partition and GRUB worked just fine when I had WinXP+Red hat. Thanks in advance.

---

