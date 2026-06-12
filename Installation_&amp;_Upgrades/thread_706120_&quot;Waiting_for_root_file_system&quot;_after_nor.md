---
title: "&quot;Waiting for root file system&quot; after normal update"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by jeskata on 2008-02-24
I updated packages (including kernel) on a 7.10 i386 installation. Now it does not boot. What's up?
I can mount the partition from livecd without problems. GRUB settings seem OK.

---

### Post by dstew on 2008-02-24
Do you get the grub menu? If so, what error message do you get when you try to boot a kernel? Please post the output of** sudo fdisk -l** and **cat /boot/grub/menu.lst**

---

### Post by jeskata on 2008-02-27
Yes, no problem with grub. The problem will manifest after it has loaded the kernel and initrd, after which it attempts to mount the root partition. After a timeout it will drop to a busybox shell.
I tried changing the UUID of the root partition with the real device (/dev/sda3) without luck. Also did the same for / in /etc/fstab.

Ended up reinstalling since I needed to get the system working. Have not updated the system since.

---

