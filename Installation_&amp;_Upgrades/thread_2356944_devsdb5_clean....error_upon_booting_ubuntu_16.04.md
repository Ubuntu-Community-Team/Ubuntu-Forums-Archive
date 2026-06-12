---
title: "/dev/sdb5: clean....error upon booting ubuntu 16.04"
date: 2017-03-28
forum: Installation &amp; Upgrades
---

### Post by adventure man on 2017-03-28
I used gparted live to  resize my partitions because I kept getting an error that I was running out of space (mainly because my 120 gb drive was not partitioned properly to begin with).  I managed to do this and now I receive this message when booting and it won't go any further.  I get a "Press Enter for maintenance (or press Control-D to continue):" if I wait a minute.

Any ideas?

/dev/sdb5: clean 965046/7086080 files, 4824116/28328448 blocks

---

### Post by Dennis N on 2017-03-28
The message is from systemd-fsck which runs on each boot, and the message shows no indication of a problem. Clean is good. These messages can be hidden by the splash (sometimes not on some systems), but if boot is interrupted for some reason, it is revealed.  

Since you just did some partition work, a UUID may have changed and /etc/fstab still retains the original uuid. _Suggestion_: compare uuids of partitions in fstab with sudo blkid for any differences, and edit fstab to match. Use usb live session if necessary.


_Extra Comments_: systemd-fsck looks at each file system mounted in fstab except for root, and may run a check. Root is checked by another process. How to see reported result:  

My computer:
```
[dmn@Sydney ~]$ journalctl -b | grep systemd-fsck
Mar 28 05:59:51 Sydney systemd-fsck[304]: Common-Files: clean, 54783/7922544 files, 14688539/31744000 blocks
Mar 28 05:59:51 Sydney systemd-fsck[417]: fsck.fat 4.1 (2017-01-24)
Mar 28 05:59:51 Sydney systemd-fsck[417]: /dev/sdb1: 6 files, 474/403266 clusters
```

---

### Post by ajgreeny on 2017-03-28
Resizing a partition would not normally change the UUID but it is still a good idea to check as mentioned by Dennis N above.

When you changed the partition size did you move the start-point of the partition from which you are booting ubuntu?
That can cause problems for grub, rather than the filesystem itself being corrupt in any way.  In spite of that "clean" message it may still be worth running a full fsck on the partition, using a live disk, with command ```
sudo e2fsck /dev/sdx#
``` where sdx#is the root partition of Ubuntu that is giving you this problem.

If that still does not solve the problem it may be the time to use Boot-Repair from my signature, again in a live OS, as that may allow you to reinstall grub and, in doing so, reconfigure it to find your newly changed partitions.

---

