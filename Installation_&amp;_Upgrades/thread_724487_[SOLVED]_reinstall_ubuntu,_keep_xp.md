---
title: "[SOLVED] reinstall ubuntu, keep xp"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by elmick on 2008-03-14
Hi,

Ive seriously messed up my ubuntu installation and have to reinstall. Its on a dual boot with xp and i dont want to lose xp. 

can i just do install from disk from CD boot's desktop, and choose manual for partitioning?

from prepare partitions my partitions are set up as:

/dev/sda
  /dev/sda1  ntfs 54Gb     -- xp
  /dev/sda5  ntfs 50Gb     -- "
  /dev/sda6  swap 682Mb 
  /dev/sda3  ext3  15Gb

should i just reformat the ext3 and swap partitions and reinstall? Will this mean ill lose the GRUB files for booting to xp?

i dont want to have to fix mbr etc.

Thanks,

Mick.

---

### Post by Rocket2DMn on 2008-03-14
You should be OK to just install normally, using your current root partition as your new root partition (format it and install fresh there).  You can keep your current swap if you want, or just do it fresh, it doesn't really matter.

---

### Post by elmick on 2008-03-14
thanks a lot, everything went smoothly and im back in business !

---

