---
title: "Grub error 17 - dual boot breezy w/ win xp pro"
date: 2006-03-18
forum: Installation &amp; Upgrades
---

### Post by jennyw on 2006-03-18
Hi there! I'm having trouble installing Breezy on a machine that already has xp pro installed on it. As soon as it boots, it says:

```
GRUB Loading stage1.5.



GRUB loading, please wait...
Error 17
```

There is no menu or anything loaded by GRUB -- no opportunity to interact with it.

I've searched around for solutions and have tried setting the bios to use lba (suggested somewhere), but there didn't seem to be such an option (it's auto or user; user just gives you a few options for the drive that don't have anything to do with lba that I can tell). I also tried reinstalling without firewire drives plugged in (someone suggested that might be causing a problem), but same result.  Also same result when I reinstalled grub using the live cd. I also tried ```
grub-install --force-lba /dev/hda
``` but that didn't work, either.

Any other ideas?

Thanks!

Jen

---

### Post by jennyw on 2006-03-18
Small update: I decided to see what would happen if I installed on a new hard disk (I happened to have one available).  And it works. So ... I'm guessing my problem has to do with trying to install on a machine that already had Windows on it. Since I doubt GRUB reads the Windows partitions as any part of getting to error 17, I suspect it has to do with my already having 2 partitions that together hold about 200 GB of data in front of the Linux partition.  Could that be it? If the bit in the MBR needs to load GRUB from /boot or something, I guess this could cause the problem. 

Someone else solved a similar problem by upgrading their bios, so I guess I'll try that next. But if anyone has any ideas in the meantime, I'd love to hear them!

Jen

---

