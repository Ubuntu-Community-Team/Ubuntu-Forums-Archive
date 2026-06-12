---
title: "Understand Boot Loaders"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-10-25
I'm researching on how to use lilo, grub, or ntloader, etc. and trying to understand one thing.

It seems that whichever boot loader you want to use, you just write that to the MBR and it _Overwrites_ the current boot loader that is there. So therefore, do you not have to _Uninstall _the current boot loader before installing the new one? Most things, you need to uninstall first before installing something new. But here, are we just _Overwriting_ and that's it?

---

### Post by coffeecat on 2011-10-25
You just overwrite, and that's it!

The Windows bootloader consists of only 440 (444?) bytes in the mbr, which simply hands over the booting process to the partition with the boot flag set. Windows has more boot files in the boot sector of the boot partition, whether that's the separate "system" partition that Windows 7 uses or the C: partition.

With grub2, the 440 bytes of code passes the boot process to core.img. With an MBR partition table, this is in the embedding area, an area reserved for boot code which is between the partition table and the first sector of the first partition. Windows doesn't use this area, but some rogue Windows apps do and can mess up grub2. Legacy grub puts stage 1 in the actual mbr and stage 1.5 in the embedding area. The rest of the grub code whether legacy or grub2 is in /boot/grub in your Linux boot or root partition.

With a GUID partition table and grub 2 you need a small unformatted partition 1 for core.img.

---

