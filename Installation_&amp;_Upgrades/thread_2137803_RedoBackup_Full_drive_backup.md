---
title: "RedoBackup Full drive backup"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by Redalien0304 on 2013-04-22
Used RedoBackup to Backup 4 Partitions /Ubuntu 12.04 (root) /home /swap /linuxmint. Everything Backed up but Only the /Linuxmint (root/home combined) partition shows up in nautilus. The other 3 Partitions only show up in Gparted but i cannot unmount them. Shows they are Locked & try unmount Manually. Restored to all 4 Partitions to a 3.5 HDD. All 4 Partitions are on 3.5 drive via a HDD case which i know works cause has other stuff on it. When try to a Usb Boot trys & reboots the laptop & same all over with Internal Hdd drive in or not. Any help would very much appreciated.

---

### Post by mastablasta on 2013-04-22
use terminal to launch nautilus with elevated privileges:

```
gksu nautilus


```

see if that will show all of the partitions.

---

### Post by Redalien0304 on 2013-04-22
Nada same thing i end up restarting laptop cause nautilus freezes baiscly have not tried tried Restarting Nautilus yet. do not know nautilus restart command. also when i try to unmount the one that Partition (Linuxmint) does show up Linuxmint says it cannot unmount  cause one or more other dives are busy. so i end just flipping the Switch on the Usb Drive enclosure.

---

