---
title: "Ubuntu installer won't recognise root disc"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by ChrisCummins on 2009-11-20
Hi,
I'm setting up a dual boot system for audio recording/production. Windows XP Pro / Ubuntu 9.10. I have setup Windows, partitioned the drive (6 partitions in total, 1 reserved for Ubuntu), formatted the ubuntu partition as FAT32, used the wubi installer to install it to that drive but then when I reboot, the ubuntu installer just says that theirs no root disc specificied and pops up recurring error message until I turn the PC off.
 
I tried booting off the CD and installing that way, but got as far as the partition manager - which just shows a blank screen and refuses to list anything. Any ideas?
 
Before I installed Windows, I checked the Ubunut installer and the partition manager did recognise the entire empty hard drive, just not now that I've partitioned it. The HD is raid 1 and was partitioned using the windows xp installer + windows xp disc manager.
 
Any ideas? Thanks.

---

### Post by lemming465 on 2009-11-21
Probably your windows RAID-1 setup is so-called "fakeraid", that is, based on BIOS and windows drivers. (Full hardware RAID controllers are expensive, as are versions of windows that turn on the microsoft OS support for pure software RAID.) The WUBI install depends on reading the existing partition, which in turn depends on the dmraid drivers understanding your motherboard chipset's idea of a software RAID layout.

What's your hardware?  In particular, what's your motherboard, and what's the exact model of the "southbridge" chip on that motherboard?  *sudo lspci -vv* may be enlightening in that regard.

The simplest solution may be to reinstall with the RAID turned off, and use the second disk for period backups rather than live mirroring.

---

