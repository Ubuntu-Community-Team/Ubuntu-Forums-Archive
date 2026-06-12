---
title: "Failed Upgrade"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by bkalinka58 on 2013-10-23
Hey guys,

I have no idea if this is answered somewhere though I'm sure it is. The other day I was upgrading from 13.04 to 13.10. Download was taking a while so I went to bed, woke up to see the Installation stopped about 2/3 in and I had no way of exiting the upgrade. Eventually rebooted the computer and it would not boot -- it was a stupid decision but I saw no other way to exit the installation. 

So, I partitioned the hard drive and installed 12.04 alongside 13.10. Is there any way I can fix the 13.10 installation without losing data? And if not, is there any easy way to delete that 13.10 partition so I can just upgrade from 12.04 to 13.10? Luckily when I installed 12.04 Ubuntu did the partitioning for me, haha. I'd prefer to not lose that data but it won't be the end of the world if I do. Any help would be greatly appreciated.

---

### Post by hansdown on 2013-10-23
Welcome to the forum, bkalinka58.

To see if your data is intact, run the 12.04 live disk, usb, etc to look at the 13.10 partition.

run

```
gksudo nautilus
```

Navigate to the 13.10 install, and try opening the files.

If there is data there, you can transfer it to a usb.

See if that works, then we'll work on installing 13.10.

---

