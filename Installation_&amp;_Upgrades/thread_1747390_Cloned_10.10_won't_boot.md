---
title: "Cloned 10.10 won't boot"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by pleriche on 2011-05-02
I have 10.10 on an old 60GB hard disk in an external USB caddy so I can boot off this when I want to instead of Windows on the internal laptop hard disk. This works well, and has done for some time.

I recently got a 1TB portable USB drive and thought it would be cool to reserve the 1st 60GB for a clone of the 10.10 system and use that instead. So I set up 2 partitions exactly like the 2 partitions on my old disk (not forgetting the boot flag) and copied the contents with dd. I also used dd to copy the boot sector excluding the partition table (dd if= of= bs=446 count=1; dd if= of= bs=512 skip=1 seek=1 count=2047).

But it won't boot. No sign of grub, no messages, no nothing. Ideas?

Regards - Philip

---

### Post by pleriche on 2011-05-02
Oh, I forgot. I checked the 1st sector of the new disk against the old with od. OK, I didn't compare every byte but they looked pretty much the same.

The laptop is a Toshiba Tecra M5, with is around 3 or 4 years old. Do BIOSs of this vintage have problems booting off large disks?

Regards - Philip

---

