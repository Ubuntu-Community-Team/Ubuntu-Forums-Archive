---
title: "Resize partitions in Ubuntu 16.10 installer"
date: 2016-10-13
forum: Installation &amp; Upgrades
---

### Post by sergeip2 on 2016-10-13
I am trying to install Ubuntu 16.10 on a GPT-partitioned hard drive. I need to shrink an existing NTFS partition and create a new partition in the resulting free space. My last Ubuntu installation experience was a few years ago, and I remember the installer's partition editor dialog was very powerful (definitely capable of resizing partitions). However, in the Ubuntu 16.10 installer I am unable to find how to resize a partition - the only relevant context menu item is 'Change...', bringing up a dialog with 'used for' and 'mount point', but no size field. Has the partition resize feature really been removed from the installer? Do I really need to usea second USB drive like GParted?

---

### Post by oldfred on 2016-10-13
Two things.
If you have Windows you must have fast start up or always on hibernation off. That keeps NTFS partition(s) mounted, so Linux NTFS driver will not mount them to prevent damage.
And you cannot modify partitions that are mounted. So you cannot use gparted on drive you boot from. Little key icons show mounted partitions that are locked.
Even with live installer, it may mount swap and you have to unmount it with swapoff.

I prefer to use gparted to edit Linux partitions.
But if resizing NTFS partition best to use Windows own partition tools and you must reboot immediately so it can run chkdsk. If partition needs chkdsk (based on flag), the Linux NTFS driver will not mount it to prevent damage.

---

