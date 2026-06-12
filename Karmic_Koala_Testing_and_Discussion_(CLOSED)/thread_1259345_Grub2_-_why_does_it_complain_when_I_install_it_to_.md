---
title: "Grub2 - why does it complain when I install it to a partition?"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-06
Never had this before with the old grub.

---

### Post by Seventh Reign on 2009-09-06
Thats kinda like asking why the PS3 has better graphics than the PS2 .. They're both very very very very different, even tho they basically do the exact same thing.

And Grub1 has always 'warned' users when installing to Partition.  Atleast everytime I've installed.

---

### Post by philinux on 2009-09-06
Guess it'll have to complain then as I multiboot. It's going on partitions whether it likes it or not. ;)

---

### Post by VMC on 2009-09-06
I never tried that. So instead of installing grub2 to mbr, you installed it to a partition. Is that correct? If so, then sounds like a bug.

---

### Post by philinux on 2009-09-06
> **VMC said:**
> I never tried that. So instead of installing grub2 to mbr, you installed it to a partition. Is that correct? If so, then sounds like a bug.

Yep. Got jaunty on disk 1 karmic on disk 2. When I installed karmic I use the advanced option and installed grub2 to sdb1.

I then can edit menu.lst and chainload to disk 2.

---

### Post by dino99 on 2009-09-06
each of my hdd (3) have a different distro on with each his own grub2. Well, at boot time, grub2 is not very fast to find the good uuid to boot (about 10-15 secondes) but that work.
Actually 2 different grub2: 1,97 with karmic & the others with 1,96. I hope that 1,97 will replace 1,96 soon.

---

