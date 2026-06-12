---
title: "&quot;disk read error&quot; after install"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by mskin on 2010-03-24
im getting a disk read error after installing ubuntu over a windows xp installation when i choose to boot into xp from the loader list.  i can install into ubuntu without issue.  

i suspect during the install i slightly adjusted the partition size bar (ok, im pretty sure i did) and this is confusing xp.  

is there a way to fix this or do i need to go through the dual install process again?  

the four previous times i've installed machines this way, i typically get the xp loader first (with ubuntu as an option).  this time i only get the ubuntu list.

thanks for the help.

---

### Post by lemming465 on 2010-03-28
Could we see the output of *sudo fdisk -lu* please?  In general, one can shrink partitions (move the end closer to the beginning), but moving the beginning is more problematic.

If you have a bootable XP disk such as BART-PE available, running XP chkdsk against the NTFS partition(s) might improve the situation.  Depending on how badly things are messed up, it could also destroy everything, e.g. if windows and Linux ended up with different theories about the disk geometry.

As a general rule, I get my best multiboot results from partitioning the disk first (using whatever combination of XP and Linux) seems appropriate, installing windows second, and installing Linux last.  I normally let Linux control the disk MBR.

---

