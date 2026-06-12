---
title: "Problems dual booting XP and Kubuntu 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by DogsOfWar on 2008-04-29
Here's my setup: I have 2 HDDs, the first one with XP and the second with Linux.  Before now I was able to get dual booting to work fine with Ubuntu 7.10.  Recently I decided to try Kubuntu, so I reformatted and installed Kubuntu 8.04 (KDE 4) on the second drive.  First I tried to make it work with my original partition setup, which had separate partitions for / and /boot, but I got an "error 22: partition does not exist" whenever I tried to boot.  Then I rearranged things a bit and put / and /boot on the same partition.  Now I get a "error 17: partition cannot be mounted".  I've tried reinstalling grub several times with the Kubuntu live cd and Super Grub Disk, but I still get that error.  Here's some more particulars:

- When I installed Kubuntu I made it install grub on the second HDD; the first time I installed ubuntu, it installed grub on the first HDD and killed xp (no idea why).  I got it to dual boot properly by using Bootpart.
- I can get as far as the grub main menu, but both of the boot options (normal and recovery mode) return error 17.

Could it have anything to do with boot flags?  And if so, can both my HDDs be marked as bootable at the same time (I heard somewhere that you can't do that)?

Thanks in advance.

- DoW

---

