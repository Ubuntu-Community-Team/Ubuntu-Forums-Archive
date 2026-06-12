---
title: "Tri-boot GRUB Chainloader issues"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by madhatt3r1 on 2009-12-22
I'm trying to setup my system to boot to XP, win 7 and ubuntu. I have all OS' installed and working but i get two boot menus and its quite annoying. I would like to have grub handle all 3 choices not just refer me to the Windows 7 boot manager. CAn anyone help me figure this out?
 
Here is what i have done so far:
Installed Win Xp (Hd0,0)
Installed Win 7 (Hd0,1)
This is when the windows boot loader took over
Installed Ubunti 9.10 (Hd1,0)
When i boot grub comes up, it has my ubuntu install and some memory tests and a selection called Windows 7 loader. 
 
I booted from my win 7 cd went to the command prompt and ran \boot\bootsect /n52 ALL /force and this changed the GRUB windows loader option to boot straight to win xp but i could not get GRUB to find the OS on the second partition. I had to go back and fix the boot in order to get back into Win 7 via the windows boot loader.
 
Anyont know how i can break win xp and 7 out of this MS strangle hold and allow GRUB to handle them?

---

### Post by ottosykora on 2009-12-22
personally I did small separate partition at the end of the drive only for grub. Installed grub to mbr and the stage 1.5 etc to the separte partition.
There I did set up all operating systems as chainload.

---

