---
title: "Windows 7 Dual boot Ubuntu - Separate Boot partition"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Gralamin on 2011-06-11
Hello!

I recently got a Solid State Drive and have been reconfiguring my Windows / Ubuntu setup. Currently have:

120 GB SSD, containing ext4 Boot partition (small), Windows 7, and Ubuntu root.
1 TB Raid 5, containing Home directory, winswap, linuxswap, and most windows files.

Partition break down:
/dev/sdd1: 60 mb boot partition (ext4, which may be the issue. Should this be something else?)
/dev/sdd2: 91.7 GB windows partition
/dev/sdd3: 25ish GB Linux root partition

/dev/mapper/*-0: 12 GB winswap (have 6 GB RAM)
/dev/mapper/*-1: 12 GB linux-swap (have 6 GB RAM)
/dev/mapper/*-2: Extended partition
  /dev/mapper/*-3: 300ish GB home partition 
  /dev/mapper/*-4: 695 GB windows data partition

Right now I can, by overwriting MBRs, have either Ubuntu fully working, or Windows 7 fully working.

So my questions are:
How can I create a working MBR for Windows 7 and Ubuntu in such a setup, on the boot partition, without losing Windows 7 ability to boot? Should I just try [This guide?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks!

Just needed to set the boot partition again after recovering windows.

---

