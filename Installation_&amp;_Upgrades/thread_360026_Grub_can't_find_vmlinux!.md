---
title: "Grub can't find vmlinux!"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by pleriche on 2007-02-12
I have 3 hard disks hda, hdb and hdc containing WinXP, Win98 and (recently installed) Ubuntu 6.06.1. I had a (stage 1 only) bootloader (mrbooter) which the Ubuntu install overwrote with Grub.

To cut a long story short, I now have grub stage1 on both hda and hdc. Normal boot  via grub stage1 on hda works for all 3 systems, but if I use the BIOS to boot into grub stage1 on hdc, it brings up the same menu from hdc/boot/grub/menu.lst but fails to find vmlinux.

The root (hd2,0) command reports fs type as fat, 0xc, not ext2fs. Since hda and hdb are fat, it’s obviously getting its disks muddled, but then how did it find menu.lst?

The kernel command then reports Error 15: File not found.

If I go into a grub command prompt the find command is unable to find vmlinux.

What’s going on, anybody?

The relevant menu.lst entry is:

root (hd2,0)
kernel /boot/vmlinux-2.6.15-27-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

Regards - Philip

---

### Post by pleriche on 2007-02-18
Sorted. For the sake of anyone coming across this post later:

First problem: it's called vmlinuz, not vmlinux! (Amazing how you read what you're expecting, not what's there.)

I needed to install grub in the partition boot sector as well as the MBR, using the following commands from a grub boot disk:
root (hd2,0)
setup (hd2,0)
Without these, I could boot by requesting the BIOS to boot off hdc because this executed grub stage 1 from the MBR. But mrbooter looks for a chainloader in the partition boot record, not the MBR as it, itself, lives in the MBR (of the 1st hard disk).

Requesting the BIOS to boot off hdc still doesn't quite work: I think the BIOS tells grub that the disk it's booting off (hd2) is hd0. When it fails, you then have to go into edit mode and change
root (hd2,0)
to
root (hd0,0)
then type:
boot

But having got it to work with mrbooter I shouldn't have to do that any more.

- Philip

---

