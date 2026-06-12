---
title: "Startup troubles"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by klichev on 2007-02-23
Ok, guys, now I'm really, stuck!!!

I am writing this from Ubuntu Live CD and need some help.

I have WinXP installed. The harddrive is partitioned in four with WinXP on C:. Just the other day, I was called for some problems - WinXp did not want to start, displaying the "Windows did not start successfully... Safe mode... Normally..." message. None of these seemed to work - Windows self-restarted after agp440.dll was loaded and went to the same screen.

I then tried to boot from Ubuntu Live CD 6.06 - it started giving some I/O buffer errors on consequitive blocks just when trying to load Enterprise Volume Manager.

Tried without the harddrive plugged in and it worked.

I finally managed to boot up the machine with the hard drive on via Ubuntu 6.10. Then I mounted all the hard drive partitions and seem to successfully read from the systems.

There's some 'Volume' volume in the devices list, which I do not know of.

The list of the hard drive partitions is as follows:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551       10010    59922450    f  W95 Ext'd (LBA)
/dev/hda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/hda6            5101        7650    20482843+   b  W95 FAT32
/dev/hda7            7651       10010    18956668+   7  HPFS/NTFS


A second computer is on my way and I wondered if I'll successfully conect them via LAN or need to transfer the faulty harddrive to the other computer and backup the more important data - just in case... There's also a WinXP installation CD coming, so...

Oh - a Win2K installation successfully recognized all the four partitions...

Any help wuld be most welcome...

---

### Post by Kateikyoushi on 2007-02-23
Isn't it easier to put the HDD in the other PC than to backup via network ?

---

