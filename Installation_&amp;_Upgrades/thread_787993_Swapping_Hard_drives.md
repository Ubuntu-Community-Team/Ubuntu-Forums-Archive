---
title: "Swapping Hard drives"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by SergioA on 2008-05-09
Hi there!

I've got the following configuration, first HD /dev/sda (master with /dev/sda1 flagged as boot and formatted as ntfs) with Win XP, and second HD /dev/sdb (slave) with Ubuntu 8.04 (attached two snapshots from GParted).

The idea is to get rid of Win XP so I would like to swap the two hard disks (changing their connectors), then reinstall Grub on the new master (using a live CD and following the instructions at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351))

Any suggestions/caveats before disaster strikes?

Thanks in advance :-)

Sergio

---

### Post by dstew on 2008-05-09
Why do you want to swap the connectors? Why not just delete XP, then do whatever you want with that disk? Then you would not have to re-configure anything. Ubuntu will boot without being the master. The "Master" disk is just the disk with the active controller, not the disk with the operating system on it. Ubuntu will work fine on the slave drive.

---

### Post by housam on 2008-05-09
You can edit the [[COLOR="Red"]_grub menu _[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")to point the boot loader to the ubuntu partition and then delete xp.

---

### Post by SergioA on 2008-05-10
> **dstew said:**
> Why do you want to swap the connectors?

Hi dstew,

the idea was to put that disk in an external usb box...

---

