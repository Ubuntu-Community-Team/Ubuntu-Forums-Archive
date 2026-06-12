---
title: "Planning Win7/Ubuntu 10.10 dual boot, SSD &amp; HDD"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by gstilma on 2011-01-20
Hello:

I'm currently dual booting XP and 10.04 on an old build. I'm planning & collecting parts for a new build using a 60gb SSD as boot drive and a 500gb HDD for documents and anything /home. I want to dual boot Win7 and 10.10 and, after some research here and elsewhere on the interwebs, have the following steps/partitions in mind:

1. Install Win7 on a 40gb partition of the SSD and tweak it (move paging file to 100gb NTFS partition on HDD, no hibernation, etc.)

2. Install Ubuntu root on remaining 20gb of SSD, /home on remaining 400gb ext4 partition of HDD.

Of course, Win7 gets installed first to get GRUB to work correctly. I don't planning on using Win7 much (just Netflix & a few other things), so I figured 40gb was enough of the boot drive.

Can anyone tell me if there are any apparent problems with this plan? What about swap -- some say that double the system memory isn't really necessary. I'll have 4gb DDR3, so maybe I could have just, say, 2gb swap on the SSD?

Really, I'd just love to read any comments/suggestions. Thanks.

---

