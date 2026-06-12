---
title: "Ubuntu installation GRUB/BootLoader error!"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by fofogogo23 on 2012-01-27
Hey everybody,
I've been looking around for hours now, and have not found a solution yet.
When I install Ubuntu on my Windows 7 machine using the CD, everything goes great until towards the end of the installation where it says something about a fatal error that the grub/bootloader could not install to /dev/sdb (Or scd or whatever I don't remember), then it gives me three options to choose from:
-Choose another place to install the bootloader.
-Continue without bootloader.
-Cancel installation.

I really have no idea what to do. I read something about RAID, but I'm not sure what kind of RAID I have (I'm pretty sure I have RAID though)

Any help would be appreciated!
Thank you very much, have a great day!

---

### Post by darkod on 2012-01-27
I guess you are using the standard desktop cd. The bootloader error is common if you install with the desktop cd on raid.
You should use the alternate install cd for raid and/or lvm installations.

If you already have it installed, you might be able to add only the bootloader but honestly it might be easier to simply install again using the alternate cd. Be careful, if you select an auto method the old install will not be deleted. You need to select Manual partitioning and specify to install on the partitions the first install created.

It would also be a good exercise how to install on raid, so I would repeat the install with alternate cd instead of looking how to add grub2 on this first install.

---

