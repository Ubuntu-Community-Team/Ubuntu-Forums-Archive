---
title: "installation issues"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by layzeeboy on 2008-10-18
Hi this is my first time attempting to install ubuntu (so first time outside a windows OS). I recently bought a new computer and am having issues with the install of ubuntu(8.04). 

I have just tried the run w/o change option so i really can't do anything to wrong.
First what happened was the ubuntu load screen loaded then an error -"large number buffer I/O error on device fd0,logical block 0" occurred and would repeat i searched and people said it was a floppy issue in the bios so i changed it so i had no floppy (i don't but whatever. After this i tried again and the boot screen came up but then something about busybox v 1.1.3 shell (ash) then (initramfs) comes up i typed help and saw some options so i tried continue - nothing happened, exit - nothing, then yes- an infinite loop of y appeared.

I've looked this up and no one can say for sure what it is, people say to change your sata HD to raid from achi but does anyone know a definite fix. I still want to boot XP as well (so dualboot. Is this issue fixed in 8.10??
Any help would be much appreciated!!
 

These are the specs if this helps:
GB EP45-ds3l mobo
q6600 intel 2.4ghz cpu
sata WD HD 750g 200g xp partition
sata pioneer dvd combo
4gb gskill ram 1200mhz
9800gtx+ nividia gpu

---

### Post by cariboo on 2008-10-18
You have to fix Windows first so that it will boot from a SATA drive then you can change the AHCI setting in your bios. I believe if you update to SP3  you should have the proper drivers.

Jim

---

### Post by joffa82 on 2008-10-19
I am having the same problem with my ep45-ds3l motherboard, I've found that by pressing F6 and adding generic.all_generic_ide=1 to the kernel line after the -- that i'm able to load the livecd.

Though when I go to install I keep getting errors saying the files on the CD are corrupt. Not sure if it's related or i just need to re-burn the cd. I'll keep trying tomorrow and see what I can come up with.

---

### Post by layzeeboy on 2008-10-21
tried the achi settings, it wasn't enabled so i enabled it but nothing would boot.. then changed back and the windows bootmgr was gone so had to reinstall windows. Not happy...
Gonna try generic.all_generic_ide=1 thing soon...

---

