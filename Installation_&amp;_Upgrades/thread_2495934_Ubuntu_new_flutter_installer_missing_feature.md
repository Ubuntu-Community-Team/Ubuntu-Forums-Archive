---
title: "Ubuntu new flutter installer missing feature"
date: 2024-03-08
forum: Installation &amp; Upgrades
---

### Post by sirblacksheep on 2024-03-08
In the Ubuntu Ubiquity legacy installer when selecting manual  partitioning I had the freedom to not only select endless partition  tables but more importantly create a separate boot partition for where  my new Ubuntu install places my efi/boot. In the new Flutter version I  can only select  which drive to place my boot but doesn't allow me to  create or select a specific boot partition where I want my Ubuntu boot  partition to be. 

I run multiple distros in one system for testing purposes. In my current  Alienware X17 I run 4 distros. To competently separate and quick swap  one of my distros in rotation I have one separate small boot partition  for each distro I use for example: Ubunt: Boot partition / System  Partition + Fedora Boot partation / system partation, Arch: Boot  Partition / System partition ...........    and so on. If i quickly want  to change let's say to Garuda Linux all I do is replace Fedora Boot  partition / System Partition to Garuda Boot partition / System partition   then hit a quick grub update on the existing running distros. Makes  this quick hassle free and never messes up my boot sector when replacing  one distro to the other. 

When I installed Ubuntu 23.10 I had to use the legacy installer for it  not to mess up the rest of my distro setup by manually placing my ubuntu  boot partition (not just the destination drive) where I want it.

Can the Ubuntu development team transfer this feature to the new  installer so we once again able to manually create and select not just  the drive but also the partition where we want the Ubuntu boot sector to  go?  

I fear that the legacy installer will be dropped by Ubuntu 24.04 and I  won't be able to Install Ubuntu without messing up the rest of my boot  sectors if I can't manually place my boot partition anymore.

---

### Post by QIII on 2024-03-08
Duplicate of [https://ubuntuforums.org/showthread.php?t=2495779](https://ubuntuforums.org/showthread.php?t=2495779)

Closed.

---

