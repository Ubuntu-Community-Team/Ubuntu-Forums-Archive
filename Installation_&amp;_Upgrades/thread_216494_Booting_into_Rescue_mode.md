---
title: "Booting into Rescue mode"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by Solidcell on 2006-07-15
So I'm trying to restore the Grub MBR but apparently I need to get into "rescue" mode to type "grub-install /dev/hda", but once at the boot: prompt, typing in "rescue" only returns a bad command error.  Aside from getting into rescue, I need to know what HDD my ubuntu boot is in.  I didn't know to check it before logging off for the last time, but when I installed ubuntu, it was the only HDD plugged in (SATA), so should there be a default?

The deal is, I installed ubuntu when it was the only one plugged in, then I unplugged the ubuntu HDD and installed windows when it was the only one plugged in.  Now when they're both plugged in, Windows is the one that gets booted and I just need to get the Grub to be the MBR.  Thanks guys.

---

### Post by Herman on 2006-07-15
If you have the Ubuntu 'Desktop' LiveCD, you should be able to do it by booting the LiveCD and opening a terminal, getting a GRUB shell, and using the following method:[*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

You should be able to re-install GRUB in a similar fashion in 'Rescue mode' with the 'Desktop' CD. I was in 'Rescue mode' in the Live CD the other day just to try it out, but I'll have to try it again before I'll remember exactly how to get into it. It shouldn't be too hard, I'll check on that and report back.

If you have the 'Alternate' Install CD, you can use the following method: [Click Here.]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")

By the way, it probably will be okay if you install GRUB to MBR on the both hard drives if you are not sure. 
You can also install GRUB to the first sector of your Ubuntu partition if you like as well. Although I prefer to install Lilo there instead as an auxilliary bootloader, and boot with  GRUB from MBR for normal use.
I would not recommend installing anything to the first sector of any non-linux partition, be careful not to do that.

All the best with it, Regards, Herman :D

---

