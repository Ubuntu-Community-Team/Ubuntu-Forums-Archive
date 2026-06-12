---
title: "Grub no longer works"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by opieisop on 2013-05-04
I started out with a drive loaded with windows vista. I then installed Ubuntu 12 on a newly created partition, grub was loaded and everything worked out. I was able to select the os I wanted to use ( with Ubuntu as default exactly how I wanted it ) on startup. A few days later I upgraded my windows side to Windows 7. But now I can no longer boot up my Linux side. The grub start up menue dosent even come up. It just goes straight to windos. I'm pretty sure I can just reinstall Ubuntu overtop my old install and it would work out. But I would lost all info on that current install. Is there another way to get this working again ?

Thanks in advance.



-Opie

---

### Post by darkod on 2013-05-04
Yes, very easy. The windows installer by default overwrites the bootloader on the MBR, os it put windows bootloader there which can't boot linux.

Get your ubuntu cd and from live mode you can easily restore grub2 to the MBR:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by opieisop on 2013-05-06
Thank you Sir.

---

