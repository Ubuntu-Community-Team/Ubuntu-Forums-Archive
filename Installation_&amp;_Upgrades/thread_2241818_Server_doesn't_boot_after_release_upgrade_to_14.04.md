---
title: "Server doesn't boot after release upgrade to 14.04"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by Vasco_Fonseca on 2014-08-28
Hi eveybody

I upgraded my Ubuntu server to 14.04 yesterday, and something went wrong with the bootloader.

It stops saying it can't find the normal.mod in /boot/grub/i386-pc/ and falls back to rescue mode.

I have 2 1Tb SATA hard drives in RAID1, and from the rescue mode I can see the disk's and the contents of the partitions (ls (md/0)/boot/ shows the various files in it).
Oddly, when I list /boot/grub I see the modules, which should be inside i386-pc (and they are, I've confirmed it with chroot via a live CD), and when I try to list /boot/grub/i386-pc it replies file not found.

I've tried to set the pager in rescue mode, but it doesn't work, so when I can't see the entire reply when I list /boot/grub and can't confirm if the list can see the i386-pc folder or not, I presume not.

I've read a lot of threads and tried various solutions the last few hours, and increased my knowledge of mdadm and grub in the process :) , but the problem persists.

I tried reinstalling grub several times, no success. It's installed in /dev/sda and /dev/sdb, which I think it's the right places, but I tried to install in /dev/md0 anyway. It didn't install, it replied that the setup couldn't be done with UUID and exited. Not sure if it's normal, or the cause of the problem.

Tried purging and reinstalling, same thing.

Tried copying the grub folder to the root directory (saw something about this in a thread), same thing.

I've chrooted and rebooted the machine about a dozen times over the last 20h, and honestly I've ran out of ideas... :)

Any insight on this is appreciated :)

Thanks
Vasco

---

