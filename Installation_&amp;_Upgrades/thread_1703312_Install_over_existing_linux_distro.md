---
title: "Install over existing linux distro"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by snowcrash101 on 2011-03-09
Hello

Currently I have dual boot setup: Win XP and Lubuntu. I wish to replace Lubuntu with Ubuntu netbook remix.

What's the simplest method of doing this? Do I use the install routine for netbook remix, and select/overwrite existing partition that Lubuntu occupies. Though what about swap and will grub be automatically updated? 

thanks for any help

---

### Post by nothingspecial on 2011-03-09
In the install when you get to the partitioning bit choose manual.

Select your lubuntu partition, choose to use it as an ext4 journaling file system. Choose to format it and give it a mount point of /

Select your swap partition and choose to use it a swap. You don't need to format it.

Do not touch your windows partition.

Make sure you pick the right one.

Back up anything in XP that you don't want to loose and make a recovery disk if you don't have one just in case. You will loose everything on your lubuntu partition.

Grub should recognise the remix and windows automaticaly.

Things can go wrong when messing about with partitions.

---

### Post by snowcrash101 on 2011-03-09
Many thanks for instructions - it worked perfectly :D

---

