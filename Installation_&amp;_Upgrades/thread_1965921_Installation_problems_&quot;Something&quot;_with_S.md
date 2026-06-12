---
title: "Installation problems: &quot;Something&quot; with SCSI disk"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by kjelle392 on 2012-04-26
Hello all.

After successfully installing Ubuntu 11.10 earlier this day on my laptop, I was ready to do the same at my desktop alongside with Windows.

I downloaded the newest 12.04, burned the image and booted into install. After installing, I was told to reboot. So far so good.

But when I now boot (of course without the DVD), I get some errors (?) and the booting stops. The last 3 lines are:

sd 22:0:0:0 [sdl] No caching mode page present
sd 22:0:0:0 [sdl] Assuming drive cache: writethrough
sd 22:0:0:0 [sdl] Attached SCSI disk

... and that's all.

I have tried to unplug both my external drives, and the cardreader but still no luck.

How can I solve this?

Edit: Problem solved. The installationprocess seems to also install to external hd's, and that is what happened. Made two partitions manually on one of my internal hd's, and used the pointed the installation to those. BUT; I managed to place the bootloader on the same disk, so that when I now want to boot into Ubuntu, I have to manually chose that hd from the boot-menu in bios...

---

