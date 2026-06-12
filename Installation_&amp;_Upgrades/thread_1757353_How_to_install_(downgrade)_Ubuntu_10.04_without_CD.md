---
title: "How to install (downgrade) Ubuntu 10.04 without CD and bootable pendrive?"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by adam993 on 2011-05-13
Hi, now I have installed Ubuntu 10.10. Works good, but I would like to switch LTS-release-cycle.
I can't burn CD, so I'm trying to install Ubuntu 10.04 without cd or pendrive.
I tried to install Ubuntu 10.04, using Ubuntu alternate cd and grub loader: [https://help.ubuntu.com/community/Installation/FromLinux#Procedure%202](https://help.ubuntu.com/community/Installation/FromLinux#Procedure%202) but it doesn't work (bugs in kernel modules)
Is it possible to downgrade Ubuntu 10.10 to 10.04 without burning cd? Can i create new partition and house the installation disk?

---

### Post by oldfred on 2011-05-13
I think most users would find it easier just to remove hard drive and plug into another system that has a working CD or can boot USB.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Not sure if you can install to same partition or not. You have to be extremely careful of MBR. If you install a boot loader and it does not work, then you will have to remove drive and fix from another computer.

I would probably create a Primary partition for the ISO and create a grub only boot partition and never let an install install grub, so I can at least get grub to load. Not sure if booted from an ISO on hard drive, it will let you create partitions or not as partitions have to be unmounted.

You may want to fully understand this and other manual boot procedures:
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

