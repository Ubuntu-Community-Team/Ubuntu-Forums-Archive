---
title: "Karmic erases other partitions boot sector"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by charris208 on 2009-10-27
Odd problem here, which I will break into several parts.

1) I have two disks with a number of partitions set up as software raid1 and containing various distros. In order to boot the various distros I have a separate boot partition that the mbr boots to that brings up a grub menu from which I chainload the distro I want. Naturally the different distros have their own grub installed on their own partitions.

2) Installing Karmic Koala was a bit of a hassle, it couldn't install grub on it's own partition, but it did install grub 0.97, without the stages ;) So I had to install grub-pc, copy the stages to /boot/grub from the strange place they were put, make a grub.conf file, and then I could set up the partition from the command line in the first grub boot. I put this info here in case someone else runs into the same problem.

3) OK, so now Karmic boots nicely on its raid1 partition. Here is the real problem: If I mount my other distro containing partitions the boot sectors are erased! So I have to reinstall grub on them from the grub command line before I can chainload them. I assume Karmic is doing this on boot with some sort of fsck script. But whatever, the question is, how do I put a stop to this boorish behaviour on the part of Karmic?

---

