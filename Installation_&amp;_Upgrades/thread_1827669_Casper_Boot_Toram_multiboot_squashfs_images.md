---
title: "Casper Boot Toram multiboot squashfs images"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by jb.transfer on 2011-08-18
Hi All,

I've just created a bootdisk (ssd) with multiples Squasfs images I can choose to
boot at the Grub2 menu.

No I tried to put the sqfs-images into a ramdisk. Therefore I edited the
script '/usr/share/initramfs-tools/scripts/casper'. I used the 'dirty hacks'
in the ubuntuforums.org/boottoram howto but I suited them for my needs.
Now the Systems stops after the kernel and doesn't find a root system.

The sqfs-image without the modification of the 'casper'-script still boots
but doesn't load into ram completely.

I hope anybody can help me out. I hope I don't have to go embedded :confused:

Stay Tuned :guitar:#
jb

---

### Post by jb.transfer on 2011-09-03
Hi Everybody,

I solved this.
I didn't need the 'dirty hacks'.

I just messed up the initrd. After changing files
in /usr/share/initramfs-tools/ I make sure
to create a new initrd.gz and to use it :lolflag:
I didn't figure out how to mark this thread as solved.

Cheers

---

