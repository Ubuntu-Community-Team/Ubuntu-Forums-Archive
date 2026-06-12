---
title: "recovered Ubuntu partition does not boot"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by alperyilmaz on 2007-05-22
Hi,

(Ubuntu partition = I mean Ext2/3)

- I have (actually, HAD) dual boot system with Windows and Ubuntu.
- When I was trying to fix an external drive's partition, I accidentally messed up main harddrive
- I used TestDisk to recover deleted partitions, both Windows and Ubuntu partitions.
- I used Ultimate Boot CD softwares to repair MBR and now Windows can boot 
- However no matter what I did, none of the bootloaders (Super Grub, Gjin, GAG, XOSL) can boot into Ubuntu partition.
- As far as I know:
.... Ubuntu partition is intack 
........If I use a partition manager and try to browse Ubuntu partition, I can see the files
........When I boot with Ubuntu LiveCD, existing Ubuntu partition mounts fine
.... Ubuntu (Ext2/3) and Linux Swap partitions are on Extended partition BEFORE and AFTER the accident

Can anybody help me? How can I recover to good old days where both Windows and Ubuntu can boot. Is this a boot sector problem in Ubuntu partition? The partition is mountable but not bootable.. 

pls help ...

---

### Post by merlinus on 2007-05-22
You might try this:

boot from Ubuntu live cd.

open a terminal.  enter the following, one at a time:

```

sudo grub
find /boot/grub/stage1

```

Write down the results, e.g. (hd0,7), and use this for the next two commands.

```

root (hd0,7)
setup (hd0)
quit

```

Good luck!

-merlin

---

### Post by alperyilmaz on 2007-05-23
merlin,

i'm impressed. i wasted so many hours to fix that problem with no result but your couple lines of commands fixed everything. Now, grub bootloader works and I can boot into Ubuntu or Windows.

thank you very much..

---

