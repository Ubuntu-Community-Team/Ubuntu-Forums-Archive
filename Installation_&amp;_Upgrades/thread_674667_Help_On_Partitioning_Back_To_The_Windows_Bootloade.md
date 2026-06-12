---
title: "Help On Partitioning Back To The Windows Bootloader"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by 12871287 on 2008-01-21
Hey,

My setup may sounds stupid so just bear with me.

My laptop hdd is split into 4 partitions (3 have OS's and 1 is the linux swap)

I was triple booting (xp/vista/kubuntu) until the partition  where my kubuntu installation was was corrupted and as a result, I formated it entirely from windows xp. Normally, when I turn my comp on, it goes to the grub loader, where I select "windows" which brings me to a different bootloader and askes me whether I want windows or vista. Now, after I deleted my linux by formating the partition, its says Grub loading Please wait and then Error 17. I realized I screwed things up by formating in the first place, but I just wanna know how I can restore my comp so that it can boot into windows again.

Thanks in advance.

---

### Post by Craigus on 2008-01-21
Try supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by kellemes on 2008-01-22
> **Craigus said:**
> Try supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)



Indeed..

**or** startup the Windows-setupcd -> enter the recoveryconsole and enter "fixmbr"

---

