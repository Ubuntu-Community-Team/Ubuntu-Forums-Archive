---
title: "Unable to install GRUB2 with RAID1"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Muuker on 2009-10-26
Hello,

I'm trying install Karmic RC (alternate disk on USB) onto a RAID1 system.

Installation goes fine until installing GRUB, then it returns to menu with no error. Rerunning GRUB install produces the same result (empty /boot/grub folder).

My RAID1 partitions are set up like this (as the installer detects the names):

/dev/mapper/isw_******_Volume01 (Ext4 - 243.8Gb) - is the Karmic RC install without GRUB
/dev/mapper/isw_******_Volume02 (Ntfs - 250Gb) - is Windows 7
/dev/mapper/isw_******_Volume05 (Swap - 6.2Gb)

RAID partitions are activated.
When looking at logs, installer can't seem to detect new Karmic partition as Ext4.

I would really like to get it working like this, as Jaunty was set up in the same way without problems.

I'll try to post exact syslogs tomorrow.

---

