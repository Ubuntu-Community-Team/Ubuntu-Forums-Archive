---
title: "Grub error 22 after repartitioning hard disk"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by tsvim on 2007-04-17
Lately I repartitioned my hard disk, thereby effectively changing the different partition umbering in grub. After reinstalling grub and having everything fine, now every time I get a kernel update (running Feisty beta, it's quite often) my menu.lst reverts to what it was before, grub trying to call root (hd0,8). This partition being none existent I get a error 22.
Of course I manage working around it, hitting e to edit and changing it to (hd0,5). But that change isn't permanent, but so isn't changing menu.lst. Although editing menu.lst fixes the problem for the next couple of days, but the next time a kernel upgrade is available, I'm stuck with error 22 again.

Anybody aware of the config file that stores the name of the partition?

---

### Post by zvacet on 2007-04-17
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

---

### Post by tsvim on 2007-04-17
Nothing on that link that could help me, the problem is not with GRUB, it is with some config file that is used every time a kernel is updated and writes the kernels to th menu.lst file.

If I change the file so everything works fine, it's just that something is not configured right over there and I don't know where the file is.

---

### Post by montgoss on 2007-04-24
I have the exact same error.  Any time a kernel upgrade occurs, it modifies the Grub config and, since it thinks my hard-drives are numbered backwards, it configures Grub wrong.

---

