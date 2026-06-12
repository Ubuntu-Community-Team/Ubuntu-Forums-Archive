---
title: "make ext3 partitions first or not ?"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by muka on 2005-09-06
OK, so I have my machine ready to install a dual boot with Grub.
I have arranged a 10 gig NTFS partition to install Ubuntu in.
Question :
Should make the root, swap and home partitions first BEFORE installing 5.04,OR let the install process do it ?
If I make it first, I imagine that Ubuntu will 'see' it.

Much thanks - Muka

---

### Post by mcmuffy on 2005-09-06
Your best bet would be to have 10gb of empty space (ie remove the NTFS partition) and tell the installer to do its own thing in the empty space. Thats what I did anyway and I ended up with a dual boot system with very little thinking needed on my part (always a good thing).

---

### Post by ultima2k on 2005-09-06
The easiest way would be to delete the NTFS-partition so that you get 10GB of empty space, then in ubuntu-install choose that space and automaticly make a swap and linux-partition :)

---

