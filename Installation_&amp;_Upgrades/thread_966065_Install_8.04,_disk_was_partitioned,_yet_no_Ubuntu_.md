---
title: "Install 8.04, disk was partitioned, yet no Ubuntu and cannot recover disk space"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Banafupe on 2008-11-01
New to all of this... went to install 8.04 on my notebook running XP. Wanted to have dual boot, yet didn't use the manual partition option. Adjusted the amount of disk space with the partition manager, and then went to install. After process was completed and rebooted machine, could not choose another OS (Ubuntu), only Windows kept booting up. Use the install disk again and it reflects that the drive was partitioned and it wants to now partition it some more thus make my existing space for windows even smaller.

Can I start over, by reclaiming the initial partition space that was created? Initially, Win had 45GB and Ubuntu had 25GB, now it wants to divide the 45GB in half and getting a disk error saying too small of drive option. HELP!!:confused:

---

### Post by gibberz on 2008-11-01
Hey Banafupe , sorry to hear your having problems! you can start over with the install but this time choose the manual approach . From there you should be able to see the partition that was made  first time and from their reformat the partition (ext3 is a good choice) and mount the root file system which is '/'. 
I don`t no why it`s not adding the bootloader to let you choose which OS you would like but since your in the posistion to do a fresh install and try again ,i would.Hope this helps a bit :)   ps you`ve not downloaded the new 8.10 intrepid ibex release by mistake have you? i know you said 8.04 above but if you had ,their are a few early problems with the partitioner that people are having?

---

