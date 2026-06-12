---
title: "GRUB and graphical installer"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by FHavlak on 2008-10-13
I am planning on installing Ubuntu today, and I had a quick question.

I installed gentoo 2008.0, and after many tries succeeded, but I think I'd like something easier for a new Linux user to manage.

One of the problems that I hit installing gentoo was that the filesystems created by their default tools were unreadable by grub.

To get around this you had to drop to command line and create the filesystems manually using and extra set of options (forcing the ext3 filesystem to use an io buffer of 128k instead of the default 256k).

This error in grub hit any Gentoo install following their guides or just using the livecd, and I was hoping to avoid something similar happening by asking here:  Am I going to want to create my partitions from the command line or will the ubuntu install cd just work?

---

### Post by caljohnsmith on 2008-10-13
Yes, from what I've read recently, what you describe is a known bug with Grub as Grub can't handle the new ext3/ext4 file systems that use an inode size of 256 vs. the older 128. But if you use the Ubuntu installer to format your Ubuntu partition, you shouldn't have any problems that I'm aware of since it will use the older 128 inode size. So my recommendation is go for it. :)

---

