---
title: "Warning: The last ubuntu update redited my Grub list"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Prisma on 2007-06-09
i was unable to boot again. After the update when i reboot it gave me the error 15 (no file found)
I have to use the live CD to reboot and edit the grub list again. My grub files are store in H0,5 but after the last update my list was rewritten and the partition that appear on the grub list was H0,6.

So be careful

---

### Post by Kobalt on 2007-06-09
Kind of weird... Are you talking about the 2.6.20-16 kernel update ? Have you checked this out on the Launchpad ? If not you should really, and eventually report it...

---

### Post by Prisma on 2007-06-09
I am in 7.04 now. You are right i think i should report this on launch pad.

---

### Post by awaldram on 2007-06-09
I think you should check your menu.1st

post it here and we'll see whats wrong with it.
most prople get fooled by the # sections these are NOT remmed out and will be used to create the stanzas every time update-grub is run (i.e during kernel update)

---

### Post by bapoumba on 2007-06-09
In addition, in /boot/grub/menu.lst, please check:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```
If correct (hd0,0 part should match your own configuration).

---

