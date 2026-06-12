---
title: "WinXP does not boot - Ubuntu Migration Assistant"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2007-04-01
I am trying to install WinXP and Ubuntu on the same hard drive, separate partitions.  I have the XP partition setup which takes up 80% of the HDD and the remainder is left as unallocated space for Ubuntu.  So I boot up the live CD and start installing when I soon find that the WinXP migration assistant crashes.  I investigate a little and then realize that the current version of XP that I am using will not boot unless I have another hard drive connected (I have two HDs -- one is a backup with a valid WinXP install on it and the other is a new HD with a fresh XP install).  So it seems like the WinXP boot record is on the backup hard drive.  Because when I disconnect the backup hard drive, my PC just hangs at "Verifying DMI pool data" -- no error, no blue screen, it just hangs.  So can anyone tell me how to properly setup the boot record on my main hard drive with the Windows XP copy on it?  I tried following these steps listed here: [http://www.short-media.com/articles/repair_windows_xp](http://www.short-media.com/articles/repair_windows_xp) - Recovery console Bootcfg and Bootfix.  If I do bootcfg /list, it looks like the boot information is setup correctly, but the hard drive will not boot on its own, it needs the backup drive installed (I installed a fresh copy of WinXP on the main HD with the backup drive installed).  Anyway, I think that once this is resolved, I should be able to run the Ubuntu install w/ migration assistant not crashing.  Will recovery console - FIXMBR trash my HD?

---

### Post by zvacet on 2007-04-01
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot")

---

