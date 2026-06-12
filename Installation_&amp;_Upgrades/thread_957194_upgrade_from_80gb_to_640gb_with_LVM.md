---
title: "upgrade from 80gb to 640gb with LVM"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by mem on 2008-10-24
All i want to do is move/clone my current install on an 80GB hard drive to a 640GB drive. The 80 is on its last legs and i'm pretty sure i'll lose the data if i don't get it off soon.

I'm trying to do this as easily as possible...
i tried clonezilla, but it wont resize the standard 8.04 lvm partitio ns on the source driveso what i'm left with is:

640GB:
boot (200mb)
extended (79GB)
   lvm (79GB)
UNUSED SPACE

how i can make the lvm extend the rest of the disk, still have my data safe / bootable, and just extend the partition to take up the remaining lvm space?

i tried expanding the extended partition using gparted (after i had cloned with clonezilla) to use the rest of the disk, but it caused all kinds of wacky issues booting the drive.

someone _please_ help, i've searched all over the place and cant find a solid answer.

edit: just ran clonezilla again and now the 640 wont even boot, grub just shits itself.. lol halp!

---

