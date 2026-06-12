---
title: "Linux 3.2.0-34 not present in grub"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by Firepowerforfreedom on 2012-12-05
I've installed kernel 3.2.0-34 on both of my Precise machines recently, but the option for 3.2.0-34 does not appear in GRUB 1.98. I've upgraded one of them now to GRUB2, and 3.2.0-34 is recognized right off the bat. Anyone else have this issue?

---

### Post by darkod on 2012-12-05
You seem to have older grub2 that might not update the latest kernel automatically. If I'm not mistaken Precise comes with 1.99.

Which means you might have upgraded ubuntu but when it asked if you wish to upgrade grub or use the current one, you answered to use the older one. I think that breaks the procedure to auto add the latest kernel.

Does it help if you run:
sudo update-grub

---

### Post by Firepowerforfreedom on 2012-12-05
> **darkod said:**
> You seem to have older grub2 that might not update the latest kernel automatically. If I'm not mistaken Precise comes with 1.99.

Well, I just ran my other box through its updates, and voila! 3.2.0-34 booted automatically. Apparently, one box got GRUB 1.98 and the other got 1.99, but I upgraded the one with 1.98 to 1.99, so all is well.

---

