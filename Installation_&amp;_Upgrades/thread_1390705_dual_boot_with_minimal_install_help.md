---
title: "dual boot with minimal install help"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by paulqueen on 2010-01-25
**the skinny**

installed xp, then ubuntu minimal install 9.10, and now have no idea how to get xp to load becuz there is no grub boot loader menu.... and the 

**the fat**

my drive is setup like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         255     2048256   82  Linux swap / Solaris
/dev/sda2             256        4904    37343092+   f  W95 Ext'd (LBA)
/dev/sda3   *        4905        7454    20482875   83  Linux
/dev/sda4            7455       30401   184321777+  83  Linux
/dev/sda5             256        4904    37343061    7  HPFS/NTFS

```

the W95 Ext'd is actually a winxp.. i dunno if that is normal or not... anyhow..

i first set up a swap... then partitioned off the winxp section and installed xp and configged it and setup some games and such and it worked fine... then i put in the minimal install 9.10 disc and followed directions and had root installed on the 20gb partition and home to the rest of things...

now, when my computer restarts, i dont get a grub boot loader menu and thus cant get back into xp without using a boot disk.

ive spent the last few hours googling and using the forums and boiled it down to *I THINK* being that my menu.lst is nonexistant... so then i tried to create my own, and failed miserably.  can someone provide some help?  thanks for anyone reading, and moreso if ya can help out =D

---

### Post by paulqueen on 2010-01-25
shameless bump

---

### Post by hemimaniac on 2010-01-26
well for starters, i believe 9.10 uses the new grub2, so there will be no menu.lst file, it has been replaced by grub.config and grub.default

i don't have any experience with it yet as i have seen too many people tremble at the mention of it

this however did help me the one time i was stuck, just go [here]("http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html")

---

