---
title: "Not booting after Installation - uninstalled RAID using ATA"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by tbobker on 2012-04-21
I tried installing Ubuntu 11.10 on my DELL DIMENSION but i always got the the end of the install and had an error about installing bootloader.
I decided to get rid of RAID and just have 2 hard disks separate and used ATA. The install went great no errors, only now I just cant boot as it cant find the bootloader? Can anyone advise. Many thanks.

---

### Post by Hakunka-Matata on 2012-04-21
Hello tbobker, tell us more.  What happens when you attempt to boot?

Can you boot to the liveCD?

---

### Post by oldfred on 2012-04-21
Hard drives keep RAID settings. You may have to remove those. Only run this if you do not want RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by darkod on 2012-04-21
If you are still willing to try raid, you need to install with the alternate cd not the standard live cd. The alternate has better raid support.

---

