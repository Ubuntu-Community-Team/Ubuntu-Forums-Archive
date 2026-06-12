---
title: "Hard drive set up question?"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by jubei2010 on 2006-11-10
I am planning on installing Ubuntu Edgy on a third drive on a different controller.  The first two drives are running in raid and contain my windows install.  The third drive has my pagefile for windows on it as well.  Now when I set this drive up in seagate do I need to set it up as bootable to be able to boot Ubuntu at all off of it or can it boot at all if set up as extra storage?

---

### Post by OpsVentus on 2006-11-10
Depends on where you want grub/lilo to be installed.
1 You can put grub on the first disk, this way you don't need the bootable flag.
2 You can also put grub on the third drive, this way you will need to make it bootable.

1 you always get grub and you can choose there what to boot.

2 you need to tell the bios what to boot.

---

