---
title: "LFS - installing the GRUB"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by halfvolle melk on 2006-03-28
Hi,

At this point (8.4) the Linux From Scratch book suggests either to overwrite the hosts GRUB with **(hd0)** or *"to install GRUB into the &#8220;boot sector&#8221; of the LFS partition"* being hda3 in my case.

If I'd overwrite the Ubuntu GRUB and add the lost entries to the LFS GRUB afterwards, will apt seek to replace it with the newest version and cause problems?

If **(hd0,2)** is used, (how) will it be found at boot-up? You can only have one boot sector per HD right?

Or is the best idea just to append something like
```
title LFS 6.1.1
root (hd0,2)
kernel /boot/lfskernel-2.6.11.12 root=/dev/hda3
```
to the existing menu.lst?

Thanks.

Edit:
Being in a bold and daring mood I can now confirm option #3 works.

---

