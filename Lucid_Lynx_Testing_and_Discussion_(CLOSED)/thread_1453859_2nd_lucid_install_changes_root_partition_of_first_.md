---
title: "2nd lucid install changes root partition of first install"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eljeffe on 2010-04-13
I've tried several permutations of this install, but the basic problems shows up. The most recent incarnation is as follows:

[LIST=1]
[*]have a separate boot partition
[*]have windows on sda1
[*]install mythbuntu on sda6
[*]   (everything fine at this point)
[*]install lucid on sda2
[/LIST]
result is that grub menu points both entries (sda6 and sda2) to the sda2 partition.

This does not happen when I install one of the linux to a different hard drive.

I've attached the boot info script results.

---

