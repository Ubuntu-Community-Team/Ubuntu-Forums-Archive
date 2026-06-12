---
title: "Installing Windows"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by Hex_Mandos on 2007-07-08
I recently bought a new laptop. It was supposed to be Ubuntu only, so I have just one ext3 partition (plus swap). However, I need to test some hardware on Windows now. Is there a way to reduce my ext3 partition to make room for Windows? And does Windows need some particular place in the partition table? (I know it needs to be in the primary master disk, but I only have one HD).

---

### Post by jskracht on 2007-07-09
Yes you can shrink your ext3 Ubuntu filesystem with gparted. I don't believe that Windows needs to be on any certain place on the hard drive. But remember after you install windows the Grub loader will probably not boot and Windows will overwrite it. So you will have to use the Ubuntu live cd and fix the boot loader.

Hope it works mabye you should try Vmware or Virtualbox if your computer is fast enough.

---

### Post by stchman on 2007-07-09
> **Hex_Mandos said:**
> I recently bought a new laptop. It was supposed to be Ubuntu only, so I have just one ext3 partition (plus swap). However, I need to test some hardware on Windows now. Is there a way to reduce my ext3 partition to make room for Windows? And does Windows need some particular place in the partition table? (I know it needs to be in the primary master disk, but I only have one HD).

Yes installing a M$ OS on a system that has Linux will overwrite the GRUB loader.

---

### Post by Pumalite on 2007-07-09
> **jskracht said:**
> Yes you can shrink your ext3 Ubuntu filesystem with gparted. I don't believe that Windows needs to be on any certain place on the hard drive. But remember after you install windows the Grub loader will probably not boot and Windows will overwrite it. So you will have to use the Ubuntu live cd and fix the boot loader.

Hope it works mabye you should try Vmware or Virtualbox if your computer is fast enough.

You can also restore grub with Super Grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

