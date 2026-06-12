---
title: "Vista doesn't boot after Ubuntu installation"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by totencham on 2007-10-19
I've installed Ubuntu 7.10 (64 bit) on disk with Vista already installed. When I select Vista in grub menu, the screen goes black, "Starting up..." appears and computer suddenly reboots.

My menu.lst (Windows part):
```

title           Windows Vista (normal)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Windows Vista (rootnoverify)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1

```
(None of the aboves work)

fdisk -l:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81920000    7  HPFS/NTFS
/dev/sda2           10199       35696   204800000    7  HPFS/NTFS
/dev/sda3           35696       35759      512000   82  Linux swap / Solaris
/dev/sda4           35759       38914    25336832   83  Linux

```
I would appreciate any help.

---

