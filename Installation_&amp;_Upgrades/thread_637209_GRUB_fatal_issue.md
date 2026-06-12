---
title: "GRUB fatal issue"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2007-12-10
My issue is this; I decided to remove ubuntu (x32) to install ubuntu 7.10 (x64) I had Windows Vista installed on HDD1

my laptop has 2 HDDs, i installed ubuntu on a 15GB partition on the 2nd HDD, and added 2GB swap.

When i was ready to install x64, i booted into the live CD, went into parted, DELETED the 15gb ubuntu partition and the 2GB swap partition, then resized the original NTFS partition that i used in windows for backup to max size. i reboot and i get this:
```
GRUB Loading stage 1.5

GRUB loading, please wait...
Error 22
```

I can't use grub reinstall method because there are no setup files to 'recover' to rebuild GRUB. I cannot boot into vista anymore. (currently in liveCD)

please help!

_My PC:_
HP dv9543cl (laptop)
2.0 Ghz Core2Duo
2GB RAM
Nvidia Geforce 8600  GS
2x 160GB HDDs

---

### Post by mikewhatever on 2007-12-10
Why haven't you installed 7.10 64 as originally planned? I am no expert in Vista, but it seems you'll need to restore its bootloader to be able to boot it.

---

### Post by ArchCorsair on 2007-12-10
Ok, i solved my issue by remaking the partitions, 30gb for ubuntu, 2gb swap. installed ubuntu 7.10 x64. set windows bootloader not to start up. all issues solved now. :D

---

