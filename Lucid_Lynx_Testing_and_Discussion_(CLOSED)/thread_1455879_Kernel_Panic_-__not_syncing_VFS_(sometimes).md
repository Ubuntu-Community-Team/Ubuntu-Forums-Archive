---
title: "Kernel Panic -  not syncing: VFS (sometimes)"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sloosley on 2010-04-16
About 50% of the times that I boot-up, my system crashes: Kernel Panic - not syncing: VFS: Unable to mount foot fs on unknown-block(0,0). (see attached pic of crashed screen)

The other 50% either it boots as advertised, or else I get an error message that allows me to strike a key to continue (ie, return to the boot menu).

I'm running Beta 2 on a dual boot system. This behavior has been consistent since Beta 2, irrespective of the kernel. 

Any suggestions would be kindly appreciated!

---

### Post by reiki on 2010-04-16
I had this same problem after I had installed 10.04 to an eSATA drive. I suspect it may have been an issue with that eSATA drive not always being recognized at boot properly because I have since turned OFF the eSATA drive, rebooted, ran update-grub so it would make a new config file WITHOUT the eSATA entries.... and have not had an issue since.  I had the kernel panic issue even when booting to the INTERNAL hard drive as long as those EXTERNAL eSATA entries were present in the GRUB menu.  

If you're NOT using an external then you may want to take a look at whether or not your hard drive cabling is tight and clean. If you're using RAID.... then I can't really help you as I have no real experience with RAID in Ubuntu as I've not used it.  :)

---

### Post by sloosley on 2010-04-16
Thank you for the suggestion Reiki. I'm not using an external drive, only a new SSD, which appears to work well booting into Win 7. A little frustration for sure!

---

