---
title: "Best way to restore system to one OS?"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by cgb223 on 2011-08-31
Hey all, i have a laptop which, at the moment is tri booting backtrack, ubuntu, and Win7. The boot loader is grub. My issue is i need to get the laptop back to just windows (dont worry im not leaving linux forever, i have another computer with it). Now, grub is installed on the ubuntu partition. I figure i'll un install that first, then throw in gparted live and delete the two linux partitions. Then ill resize the ntfs the same way to the whole hard drive. Then I'll throw in the windows 7 disk and get the bootloader from that working. I figure that will do it, but before i wreck my system, does that sound right? Is there an easier way?

---

### Post by ahears on 2011-08-31
I would restore the master boot record *first*. Start the Windows 7 recovery console and enter:

>  
bootrec.exe /fixmbr **This will replace the Grub Loader on the MBR with the Windows.**


 Apparently, if you use the fixboot.exe command it will only recreate the Windows loader on that partitions boot record and won't actually replace the MBR. I learned this while studying to help remove a boot sector virus. Once you get that working I would then use partitioning software to remove the unwanted partitions.

---

### Post by Mark Phelps on 2011-09-01
Sounds like your plan is to resize the Win7 partition using GParted after removing the Linux partitions.  Would be best NOT to do that.  The Win7 OS partitions are particularly prone to corruption by Linux filesystem utilities -- and if it DOES get corrupted, you're going to have a hard time booting into it to fix it.

Instead, while Win7 still works, boot into it and use the Backup feature to create and burn a Win7 Repair CD.  You can either use the command line entries already suggested, or you can boot from that CD and run Startup Repair 3 or 4 times.

THEN, use the Win7 Disk Management utility to resize the Win7 OS partition.

---

