---
title: "Fresh install, software RAID 1 failure."
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by general_disarray on 2005-05-03
First, a little background on the machine.

2 X 18GB SCSI disks in hardware RAID 1, /  and swap, 2 X 80 GB IDE disks on an IDE controller in software RAID 1, /home.

The install goes fine, I am able to create and format the software RAID device.  On reboot, I'm greeted with a GRUB error, which, after a little googling, I fix (first time using grub, miss LILO already).  On the next reboot I get errors that /dev/md0 device does not exist, and that special device /dev/md0 could not be mounted.  So, back to google, I discover EVMS. evmsn shows /dev/evms/md/md0 with a status of modified, and only by deactivating and then activating it will the device node show up in /dev, where I can then mount and use it.  Of course, all this does not survive a reboot, and this is where I'm stuck.  ](*,)

This is my first Debian based distro (switched from Gentoo), so alot of things are new to me.  Please help, I really don't want to go back.

---

### Post by general_disarray on 2005-05-05
NM, I just bought a dual G5, so don't worry about it...

---

