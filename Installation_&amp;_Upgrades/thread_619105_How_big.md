---
title: "How big?"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by wydra on 2007-11-21
Ok, how big should my partitions be for a dual boot, Windows/Ubuntu 7.04 laptop?

I'm running 2 gigs for ram, and have a 80 gig HD.

Let me know if I'm correct...

Windows = 15gigs

Shared FAT 32, maybe about 38gigs?

/ dir for Ubuntu = 10 gigs

/home dir for Ubuntu = 15 gigs

swap = 2 gigs?

Oh, and what order should they go in, in Gparted. BTW, I'm probably going to set them up with Cute Part, then install windows on its part, then install ubuntu.

---

### Post by renzokuken on 2007-11-21
install windows to the first partition otherwise microshaft will not be happy and can cause errors with grub and mbr.......it doesnt like being second or later....hehe

as for the sizes, all those look fine.

my advice would be to use cute part to create a 15 gig part for XP at the start of the drive, then leave the rest as one partition for linux.

install windows to first partition, then install ubuntu, using ubuntu's partitioner to create your swap, /, and /home in the free space as you like

---

