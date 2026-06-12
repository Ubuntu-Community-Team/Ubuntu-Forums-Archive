---
title: "Ubuntu 20.4 on SSD does not boot. normal not found"
date: 2020-10-14
forum: Installation &amp; Upgrades
---

### Post by alexpilavakis on 2020-10-14
Hello, after installing ubuntu on my new SSD I cannot boot them as it gives the i386-pc/normal.mod not found.

It's not located in any of my disks/partitions and neither boot-repair did the trick. Here is the URL after the repair [https://paste.ubuntu.com/p/D6hDGTg33w/](https://paste.ubuntu.com/p/D6hDGTg33w/)

Any recommendations?

---

### Post by CelticWarrior on 2020-10-14
You may need to change the boot order in BIOS. Please select the drive where you told the installer to install the bootloader (Grub).

---

### Post by oldfred on 2020-10-14
The grub in sda, is looking for a partition by UUID that does not exist.
But grub was reinstalled to MBR of external drive and that should boot.

---

### Post by alexpilavakis on 2020-10-17
Changed the boot order but still when trying to boot from SSD I end up in grub-rescue screen with [COLOR=#000000]the i386-pc/normal.mod not found[/COLOR]

---

### Post by oldfred on 2020-10-17
Can you manually boot?
Change this example so all drive references are your drive & partition. If booting the external directly, the drive is hd0. Boot drive is always hd0, then others are in SATA port order. Some do make an external drive as first or sda when booting it.  Your install was in sde1 per report or hd0,1. But whether sda1 or sde1 (hd4,1) or perhaps another drive may just depend on your system. I sometimes have to experiment as with several drives & USB flash drives my order also changes. While boot should be using UUID, sometimes the reference change from hd4 when installed to hd0 when booting causes an issue.

grub rescue:
If you're in the GRUB rescue shell the commands are different, and you have to load the normal.mod andlinux.mod modules:
grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue> set root=(hd0,1)
grub rescue> insmod normal
grub rescue> normal
grub rescue> insmod linux
grub rescue> linux /vmlinuz root=/dev/sda1 # or sde1?
grub rescue> initrd /initrd.img
grub rescue> boot

---

