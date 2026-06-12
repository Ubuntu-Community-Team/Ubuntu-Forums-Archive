---
title: "Dual boot partitioning improvement"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by MightyMe on 2007-10-25
Have (had) a system with XP on one big NTFS partition. Defragged it in XP several times. Still didnt seem to defrag the disk enough since the Ubuntu 7.10 installer resized it to a size i thought was big enough, but XP still crashes on boot. Ubuntu works just fine though and I can see/mount the NTFS partition.

Instead of diving into what went wrong I would just like to comment on the installer. It's just a simple thing and relates to changing a text label, namely:

If you're resizing your NTFS partition with the Ubuntu installer, the slider underneath says "Size of new partition" (if I remember correctly).
The ambiguity is; is this the size of the NTFS partition AFTER RESIZE or the size of the new partition(s) YOURE CREATING? Just asking for a text label change in the installer to clarify this.

Btw, does anyone know if there's a way to repair my XP without destroying Grub in this case?

/Me

---

