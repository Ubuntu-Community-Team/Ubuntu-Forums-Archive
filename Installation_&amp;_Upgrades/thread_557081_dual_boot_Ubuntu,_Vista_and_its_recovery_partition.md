---
title: "dual boot Ubuntu, Vista and its recovery partition"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by jynyl on 2007-09-22
This is for a PC preloaded with Vista and a recovery partition.  The Vista recovery is done using a boot time selection.
What is the recommended method of installing Ubuntu so as to retain access to the recovery partition?

I guess the method would be to use Vista to resize the c: drive to make space for Linux and swap (leaving the recovery partition as is).  But how is access to the Vista recovery partition retained, if grub replaces the Vista boot loader?

TIA

Peter

---

### Post by pxwpxw on 2007-09-22
**jynyl**

Have you looked at this thread, which also refers to the recovery partition.
 [SOLVED] Dual Boot Vista + Ubuntu 
[http://ubuntuforums.org/showthread.php?t=538693&highlight=vista+dual+boot](http://ubuntuforums.org/showthread.php?t=538693&highlight=vista+dual+boot)

Normally, grub would chainload to the vista bootloader and the existing vista bootloader options. However I am not a vista user, just xp.

---

