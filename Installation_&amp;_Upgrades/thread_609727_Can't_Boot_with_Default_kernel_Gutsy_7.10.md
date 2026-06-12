---
title: "Can't Boot with Default kernel Gutsy 7.10"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2007-11-11
The  live CD of Ubuntu 7.10 Gutsy booted to a graphical desktop and worked ok, however after hard drive installation, boot fails with:

waiting for root filesystem.


So far the only way I have got Gutsy working is with my own self compiled 2.6.23 kernel.


Looking back at my own notes, I had the same probled with Feisty due to a missing module, piix in the initramfs.

I booted from the live CD created a mount point for my / ubuntu gutsy, chroot  and added piix to /etc/initramfs/modules and craeted a new initramfs, changed my entries in grub, but still the original
2.6.22 kernel failed to boot.

I do have more than 15 partitions on an IDE hard drive on IDE0.
Any help appreciated.

Hardware:
Asus P4P800-E
Intel P4 2.8G
Maxtor 160G  UDMA100 HD
Nvidia 5700FX Ultra

---

