---
title: "Upgraded to 12.04 and now grub problems"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Poilar on 2012-04-28
I use my windows bootloader, with Grub as an option.  Before I updated, I choose choose windows or choose grub, and if I chose the latter I could choose from the grub menu and all was well.  After I updated, each option on my grub menu just gives the error message "no such partition." The same thing happens if I run "ls" from the command line.

I can run boot-repair and that lets me get into Ubuntu, but only by overwriting my windows mbr.  Any ideas how I can fix grub on my ubuntu partition without overwriting my windows mbr?

Here in my boot info: [http://paste.ubuntu.com/953793/](http://paste.ubuntu.com/953793/)

Thanks

---

### Post by darkod on 2012-04-28
Grub2 is not suited to be used on a partition, like grub1. It's bigger and doesn't fit on the PBR so part of it needs to be saved on another location. This link to the other location gets easily broken during updates, upgrades, etc.

It's recommended you use grub2 on the MBR to avoid these issues. I can't see anything special that you would need to keep the windows bootloader for.

---

