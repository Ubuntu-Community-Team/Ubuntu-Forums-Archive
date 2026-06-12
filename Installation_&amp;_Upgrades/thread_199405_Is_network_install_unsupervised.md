---
title: "Is network install unsupervised?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by broughcut on 2006-06-18
Hi, I left a laptop on installing ubuntu over the network. It takes 90 mins due to internet connection so I left it, but there was a power interruption (we're off grid) and the battery died before I checked back. It had plenty of time to complete installation, and eveything seems to be working (apart from wifi cards, which I need to configure).

Wondering if there were any important user steps required at the end which I've missed?

I also installed it on my Panasonic laptop earlier on today (first linux os, very impressed) and the only glitch was that the display cut out during the last 10-15 mins of the install (when it was at about 50% progess installing the 877 or so files it downloads from the mirror). I was blind apart from the hd activity light and had to press enter a few times to keep things moving. Whatever those steps were (setup default dual OS boot menu etc??) I missed them on the second installation. And I just assume I selected default settings on the first one!

Just wondering... Everything (including dual boot) seems to be working fine so I don't think there's any need to reinstall.

thanks...

---

### Post by broughcut on 2006-06-19
no worries need to reinstall anyway, for some reason ntfs and fat32 were not mountable from ubuntu. I detelted the partitions in windows and created the fat32. ext3 and swap in Partition Magic... Rebooted... Grub error!

Thank god for "fdisk/mbr". Why doesn't Grub defer to boot.ini in these circumstances (or handle such errors in some other way)... as it stands, an error on the linux partition can disable dual boot machines. Is there a better way of setting up the dual-boot manager?

---

