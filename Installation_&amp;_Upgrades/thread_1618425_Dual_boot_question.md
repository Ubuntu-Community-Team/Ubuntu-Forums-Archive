---
title: "Dual boot question"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by NcTarheel704 on 2010-11-10
I am currently dual booting vista and bactrack. I would like to get rid of backtrack and install ubuntu. I would just format the backtrack partition then install ubuntu correct? Will this not do anything to the grub bootloader that came with backtrack.?

---

### Post by Hawkoon on 2010-11-10
> **NcTarheel704 said:**
> I am currently dual booting vista and bactrack. I would like to get rid of backtrack and install ubuntu. I would just format the backtrack partition then install ubuntu correct? Will this not do anything to the grub bootloader that came with backtrack.?

If you format the partition, your bootloader will go as well if it sits in that same partition.

Personally I am a big fan of a small grub data-only partition. Any new operating system goes in its own partition and in case the installation screws up grub, I just use a live CD to fix grub and check/tweak the entries in menu.lst

I basically followed this guide
[HTML]http://www.justlinux.com/forum/showthread.php?threadid=147959[/HTML]

---

