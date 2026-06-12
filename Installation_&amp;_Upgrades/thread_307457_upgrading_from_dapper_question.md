---
title: "upgrading from dapper question"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Sumint620 on 2006-11-26
i'm looking to upgrade from 6.06 to 6.10. i was wondering if i do the upgrade with 

$ gksu "update-manager -c"

will this keep by GRUB and all the settings i have in GRUB? i'm dual booting windows XP and i also have a skin on GRUB (don't care if that goes or not). one more question about GRUB. the list of operating systems goes from Ubuntu at the top, some safe-modes etc, all the way to Windows at the bottom. since i'm not the only one using this computer, is there a way to move windows to the top so people who don't want to boot into ubuntu can boot to windows first?

---

### Post by taurus on 2006-11-26
It should.  It will also include the new kernel in there so you can boot from it.

---

### Post by Sumint620 on 2006-11-26
what do you mean by i can boot from the kernel.

---

### Post by taurus on 2006-11-26
In the GRUB menu, you can choose whatever kernel you want to boot by highlight it and hit the return key.

---

