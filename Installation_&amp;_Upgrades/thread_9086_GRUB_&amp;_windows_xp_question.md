---
title: "GRUB &amp; windows xp question"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by evanc on 2004-12-23
okay, hopefully someone can help out here. 

i've got ubuntu warty and a large fat32 partition on my first hard drive, and GRUB's running off that.... I've got XP installed on my second hard drive, which has the windows boot sector (I ran a recovery disk to get XP onto my second hard drive, while my first drive was removed).

So, the problem is this - i can boot to windows but only by going to bios and setting the default hd to the second one - when i choose windows in GRUB it says "wrong filesystem" or something, and stops.

the ubuntu install is working fine, and windows works fine when i choose to boot from the second hard drive.

all i need is to edit the GRUB listing for windows to load windows from my second hard drive.... i'm not sure at all how to do that, and i don't want to screw anything up, so if anyone has a link to a good GRUB how to, I'd appreciate it.

---

### Post by jonny on 2004-12-23
I'm no expert in these matters, but I have read several times that Windows XP will not run successfully on a second drive; I've certainly failed when I've tried to get it to work on a pure Windows box (XP & 98 on different drives).  How are you booting Windows successfully on the second drive?  If it's by playing with your bios settings or IDE cables, that might be the explanation.

Why not permanently swap the primary and slave drives over, and keep the faddy Microsoft lad on the primary?  Linux is much less fussy - it's happy to reside on the slave.  You can always make ubuntu your default o/s... as if you'd do anything else!

---

### Post by evanc on 2004-12-23
[QUOTE=jonny]I'm no expert in these matters, but I have read several times that Windows XP will not run successfully on a second drive; I've certainly failed when I've tried to get it to work on a pure Windows box (XP & 98 on different drives).  How are you booting Windows successfully on the second drive?  If it's by playing with your bios settings or IDE cables, that might be the explanation.

Why not permanently swap the primary and slave drives over, and keep the faddy Microsoft lad on the primary?  Linux is much less fussy - it's happy to reside on the slave.  You can always make ubuntu your default o/s... as if you'd do anything else![/QUOTE]

i've been getting windows to load by going to bios to set the slave hd to boot.... i suppose i could swap the drives and reinstall ubuntu, thus putting grub onto the 'windows' disk's mbr...

---

