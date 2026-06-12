---
title: "Error in dual boot"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by connor3 on 2006-10-07
i had xp on my laptop, then upgraded it to vista beta 2.  i then installed ubuntu on a seperate partition, and then configured it following the instructions on [http://www.commonmancomputing.com/y/learn/dualbootvistaand%20linux/tabid/62/default.aspx](http://www.commonmancomputing.com/y/learn/dualbootvistaand%20linux/tabid/62/default.aspx)

when i turned on my computer and waited for it to automatically boot to vista, the following error message came up:

  Booting Windows Vista Beta 2 build 5600
root (hd0,1)
  Filesystem type is ext2fs, partition type 0x83
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue...

Does anybody have any suggestions for how I can make this work?

Thanks!

---

### Post by kidders on 2006-10-07
Are you sure you don't have your disk partitions the wrong way around? (It seems unlikely your Vista is on an ext2 filesystem!) Perhaps you should double-check your grub configuration.

---

