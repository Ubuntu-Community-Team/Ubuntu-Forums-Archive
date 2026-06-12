---
title: "Prepare Partitions - blank list"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by EMR on 2010-10-09
I'm installing Ubuntu 10 LTS on a friend's computer.

This friend's computer has a history of not working very well, but those may have been due to bad configuration.  I'm starting fresh with this install (I'm on the live CD right now) and I've hit a snag-
here is a screenshot.
[IMG]http://i1120.photobucket.com/albums/l494/QuaternionJoe/Screenshot2.png[/IMG]
The useful buttons are all unclickable, and right clicking just asks me if I want to revert.  Is it not finding a HDD, or what?

---

### Post by srs5694 on 2010-10-09
First, see [this Web page,](http://www.rodsbooks.com/missing-parts/) which *may* provide a solution -- but I can't guarantee that you've got the same problem.

If that doesn't help, please post the output of "sudo fdisk -lu" on the affected computer, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by EMR on 2010-10-10
Thanks for the tip-this is starting to make more sense-I knew that the disc was kind of a mess, and I'd been hoping to use Gparted (or whatever parted front-end the Ubuntu installer uses) to format the thing again.  I guess I'll have to use the console version?

```
 Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cb410

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150689699    75344818+  83  Linux
/dev/sda2       150689700   156296384     2803342+   5  Extended
/dev/sda5       150689763   156296384     2803311   82  Linux swap / Solaris

```

I'll manually wipe the disc (not with a magnet) and get back.

Thanks as always!

---

### Post by srs5694 on 2010-10-10
Those partitions look reasonable to me, unless I've missed something. I'm therefore not sure what the problem is.

---

