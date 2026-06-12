---
title: "can't boot - can I get to my data from cd/usb boot?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by adrian_nye on 2011-01-10
I have dual boot windows 7 and ubuntu 10.04.   I had never booted to windows until yesterday by accident, and it did a massive update and hosed my ubuntu so it wouldn't boot.  I have data that I'd like to get
from my ubuntu partition before a reinstall.

To make matters worse, I tried a grub change to try to fix the boot sector problems, and now it won't boot to windows either.  It boots directly into the grub prompt.

My question is, can I boot from a cd/usb and then access my hard disk ubuntu data so I can back it up over
a network before I reinstall ubuntu?

Thx

---

### Post by adrian_nye on 2011-01-10
I booted from usb and I see the partition with my data (under Computer, it is a filesystem).

However when I try to open it it says wrong fs type, bad option, bad superblock on /dev/loop1, missing codepage or helper program, or other error.   dmegs says unable to read superblock.

---

### Post by oldfred on 2011-01-10
From your USB, you can run fsck to see if it will fix your Linux partitions. If the USB flash drive mounts swap you may also have to so a swapoff to unmount the extended partition if your install is inside an extended partition.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by oldfred on 2011-01-10
You have too many threads going:

[http://ubuntuforums.org/showthread.php?t=1663304](http://ubuntuforums.org/showthread.php?t=1663304)

This shows that you just have wubi, so you need to run chkdsk from windows. I do not know how to do a fsck from a wubi install.

---

