---
title: "where o where has my cdrom gone"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by edrappin on 2006-11-09
I don't even know where to begin trying to solve this issue

I purchased a new laptop with a 100 GB hard drive. First I installed windows on the entire drive. Then I used Qtparted and made my windows partition 15 GB and left the rest to linux. I then installed Kubuntu edgy on the linux partition. 

Neither operating system can see the cdrom. In windows there is no sign of the cdrom in the device manager and there is no mention of my CDROM player when I run dmesg after kubuntu comes up. There is a cdrom line in my fstab file though.

The cdrom is connected as I do see it in the BIOS and I can boot from the cdrom. 

Any Ideas at all?

Thanks everyone.

---

### Post by edrappin on 2006-11-09
I think i figured it out. The folks who made the laptop put the harddrive on IDE channel 0 master with nothing on the IDE channel 0 slave. They put the the cdrom on the IDE channel 1 slave.  This is "illegal" correct?

---

