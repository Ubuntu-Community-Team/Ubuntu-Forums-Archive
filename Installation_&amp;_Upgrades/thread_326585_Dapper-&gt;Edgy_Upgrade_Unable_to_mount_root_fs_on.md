---
title: "Dapper-&gt;Edgy Upgrade: Unable to mount root fs on unknown-block(0,0)"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by DarthPlageus on 2006-12-27
I upgraded my HP Compaq nc8430 laptop from Dapper to Edgy, using:

gksu "update-manager -c"

When I reboot I get:

root (hd0,0)
  Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz root=/dev/sda1 ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x15787d]
savedefault
boot
Uncrompressing Linux... Ok, booting the kernel.
[17179570.956000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

What is going on, and how can I resolve this problem?  Thanks!   :-?

---

### Post by DarthPlageus on 2006-12-28
An update to my post.  The error in the message I posted:

 Filesystem type is ext2fs, partition type 0x83

May yield a clue, since the root filesystem is actually an ext3 type, as per the original /etc/fstab entry:

/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1

Could it be a lack of support for ext3 in the kernel I built?  How do I resolve this?  Thanks

--john

---

