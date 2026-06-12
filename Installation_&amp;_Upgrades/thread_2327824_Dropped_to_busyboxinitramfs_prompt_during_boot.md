---
title: "Dropped to busybox/initramfs prompt during boot"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by Scott_Pidzarko on 2016-06-14
Says that it "Can't find the root device" and lists the UUID which I've verified is the correct one through the boot-rescue-disk DVD tool by running blkid. I tried adjusting the root device timout to longer with no effect. This happened when one of the machines at work refused to POST so I swapped the disk into the new computer and it passed post but I get dropped to a busybox/initramfs prompt every time. The disk is still mountable and readable so I'm sure the disk itself is fine.

[https://paste.ubuntu.com/17344145/](https://paste.ubuntu.com/17344145/) for full details of the various commands the boot-rescue-disk dvd ran for me after I reinstalled grub.

EDIT: I have tried changing /mnt/fstab to boot via /dev/sda1 instead of by UUID with no difference to the error message.

Anyone have any ideas?

-Scott

---

