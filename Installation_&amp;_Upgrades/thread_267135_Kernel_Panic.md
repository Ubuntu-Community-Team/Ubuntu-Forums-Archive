---
title: "Kernel Panic"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by postino87 on 2006-09-28
hi all

i've just download the new kernel source 2.6.18 from kernel.org and i'm trying to compile it, but at the system reboot, a message say:
"kernel panic - not syncing: VFS - unable to mount root fs onunknown-block (0,0)"

i use only IDE disk, so and i've compile as built in the ide disk support (BLK_DEV_IDEDISK)

my root fs is ext3 and of and EXT3_FS is compile as built in, and also RAM disk support and initiramfs/initrd are built in

..so, wher's the problem? where i'm wrong?

thanks a lot

---

### Post by postino87 on 2006-09-28
so anyone can help me ?  :(

---

### Post by doomie22 on 2006-09-28
Im having the same problem on my dell ls with xubuntu booting over a network...anyone help please, i need this up an running tomorrow. Thanks

---

### Post by bitwiseshiftleft on 2006-10-08
You may also need to compile in support for your chipset, and all that random stuff.

---

