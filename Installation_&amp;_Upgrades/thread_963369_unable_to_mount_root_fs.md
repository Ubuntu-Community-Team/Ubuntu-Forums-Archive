---
title: "unable to mount root fs"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by gadya on 2008-10-30
I have an old version of linux on a primary partition and I boot it using grub. I installed a newer version 8.04 on a logical partition. It said it had installed OK but I don't know what it did about grub - it said 'updating grub'. It doesn't appear to have done anything.
I can still boot as before with the old menu coming up. I have now updated the old menu.lst to include the new installation.
But when I try to load the new installation it comes up with "kernel panic, not syncing: VFS: unable to mount root fs on unknown block(0,0).

(Note that I can't test the installation by booting it directly via the partition table as it's on a logical partition.)

This is the new entry:
title		Ubuntu kernel 8.04
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hdb6 ro quiet splash
savedefault
boot

after the root (hd0,5) it comes up with
"filesystem type = Ext2fs, partition type = 0x83
so it finds a good partition

but after the boot, it comes up with 

"kernel panic,
not syncing: VFS: unable to mount root fs on unknown block(0,0)"

Has the installation been done to some other block which I need to specify somehow?

---

### Post by gadya on 2008-10-30
since posting the above I have added to menu.lst:

initrd	/boot/initrd.img-2.6.24-19-generic

and it no longer does a "kernel panic" but after a lot of toing and froing from side to side it eventually lands up in "BusyBox built-in shell" rather than a Gui interface.

What is wrong with the installation?

---

