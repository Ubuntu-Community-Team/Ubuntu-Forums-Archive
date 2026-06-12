---
title: "Dual boot two hard drives"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Doug11 on 2010-05-11
I have Ubuntu and XP each on their own hard drive. Is there a way to choose between the two on boot-up or do I have to go into the BIOS settings and choose from there which device I want to boot every time I want to change the booting OS?

---

### Post by darkod on 2010-05-11
Option 1. You can choose which OS you want in the grub2 menu. That would mean leave the ubuntu disk as first choice permanently, and use grub2. If currently XP is not in the menu, which would happen if XP was installed after ubuntu or the disk was unplugged, just boot ubuntu and in terminal run:

sudo update-grub

If for what ever reason grub2 gets corrupted, you can still boot XP by selecting that disk in BIOS, like you are doing now.

Option 2. Depending on motherboard manufacturer, most recent boards have a so called Quick Boot menu. During boot when the DOS type screen shows, look at the bottom if it says which button to press for quick boot menu. Usually it's F12. That will give you choice of the disks without entering BIOS.

PS. In the above for grub2 I assumed you are using more recent version. Grub2 was introduced with 9.10. For 9.04 and earlier, or if you did upgrade from 9.04 without also upgrading grub1, you still have grub1 which needs different approach because it needs XP entry to be created manually.

---

### Post by Doug11 on 2010-05-11
> **darkod said:**
> Option 1. You can choose which OS you want in the grub2 menu. That would mean leave the ubuntu disk as first choice permanently, and use grub2. If currently XP is not in the menu, which would happen if XP was installed after ubuntu or the disk was unplugged, just boot ubuntu and in terminal run:

sudo update-grub

If for what ever reason grub2 gets corrupted, you can still boot XP by selecting that disk in BIOS, like you are doing now.

Option 2. Depending on motherboard manufacturer, most recent boards have a so called Quick Boot menu. During boot when the DOS type screen shows, look at the bottom if it says which button to press for quick boot menu. Usually it's F12. That will give you choice of the disks without entering BIOS.

PS. In the above for grub2 I assumed you are using more recent version. Grub2 was introduced with 9.10. For 9.04 and earlier, or if you did upgrade from 9.04 without also upgrading grub1, you still have grub1 which needs different approach because it needs XP entry to be created manually.

Thanks. I checked out the F12 deal but that does not give me the choice of which hard disk to boot from. I will try update grub and see how that works. You are right. I did install XP after Ubuntu.

---

### Post by darkod on 2010-05-11
Even if the quick boot menu worked, I still prefer grub2. The update should sort it out.

That command needs to be run after adding a new OS and also after any change to grub2 configuration files, like changing timeout value, default OS, etc. Until the update-grub is run, the change is not reflected.

---

### Post by Doug11 on 2010-05-11
The update-grub worked fine. The only thing I always find annoying is that in my grub list,,it shows everything. Even recovery partitions. Is there some sort of grub.list that can be edited to delete some of these unnecessary entries?

---

