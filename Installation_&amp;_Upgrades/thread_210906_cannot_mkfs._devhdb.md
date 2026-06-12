---
title: "cannot mkfs.* /dev/hdb"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by zambaroo on 2006-07-07
Hello all.

Long time linux user, completely baffled by this problem:

Installed dapper onto a machine w/two drives, hda and hdb, both are the same size, albeit made by different vendors. After the installation (during which the second drive was left untouched), I cfdisk'd hdb to contain a 62Gb partition in the end of the drive. Then I tried to mkfs.ext3 it, and this is what I get:

root@xenomom:~# mkfs.ext3 -v /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
/dev/hdb1 is apparently in use by the system; will not make a filesystem here!

The partition is not mounted, lsof and fuser also tell me that the partition is not in use. I've rebooted the machine after cfdisk.

What gives? Any ideas would be appreciated.

-z

---

### Post by mlind on 2006-07-07
You've probably tried this already, but do you get the same error if you drop to runlevel 1?
If you're running X and gnome, gnome-vfs might be doing its own tricks to your partition.

Other than that, I dunno. Very strange behaviour.

---

### Post by zambaroo on 2006-07-07
I have not tried that, thanks for the suggestion. I just stopped gdm and made sure X is not running. I also stopped xen related services. Still the same effect persists.

z

---

