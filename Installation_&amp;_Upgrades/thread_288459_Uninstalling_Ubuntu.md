---
title: "Uninstalling Ubuntu"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by kc0eak on 2006-10-29
Hello,

I am currently considering uninstalling Ubuntu off my laptop.  I'm not going to go into the reasons as to why, but it is something that I may have to do.

If I need to uninstall it, how do I go about doing it so that the NT Boot Loader will take over for the GRUB boot loader that I have been using?  I won't have any problems removing the partitions as I have a partition manager that will do this, I just don't want to mess up the boot loader.

Thanks

---

### Post by yabbadabbadont on 2006-10-29
You will probably have to boot into the recovery console and run both fixmbr and fixboot.

---

