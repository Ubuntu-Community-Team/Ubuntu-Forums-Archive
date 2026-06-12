---
title: "won't boot after upgrade from ubuntu 9.04 to 10.04"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by saspurs on 2010-09-16
Here's the message I received:

init: ureadahead main process (2393) terminated with status 5
libudev: udev_monitor_new_from_netlink: error getting socket: invalid argument
Mountall: mountall. c3206: assertion failed in main: udev_monitor=udev_monitor_
init: mountall main process (2396) killed by ABRT signal
general error mounting filesystems.
A maintenance shell will now be started
Control-D will terminate this shell and reboot the system
Give root password for maintenance
(or type Control-D to continue.

I finally figured out what my root password was by dumb luck. It just takes me to a root prompt. I'm new to Ubuntu so I don't really know what I'm doing. Does anybody know how to fix this? Any help would be appreciated. I'm actually communicating through a live 10.04 installation disk.

---

### Post by PRC09 on 2010-09-17
From what I have read you cannot upgrade directly from 9.04 to 10.04.you can only upgrade from 9.10 or 8.04......


[https://help.ubuntu.com/community/LucidUpgrades?highlight=%28\bCategoryUpgrade\b%29](https://help.ubuntu.com/community/LucidUpgrades?highlight=%28\bCategoryUpgrade\b%29)

---

### Post by mörgæs on 2010-09-17
Since 10.04 runs well in a live environment, I would go for a backup and a clean install.

---

### Post by saspurs on 2010-09-17
> **PRC09 said:**
> From what I have read you cannot upgrade directly from 9.04 to 10.04.you can only upgrade from 9.10 or 8.04......


[https://help.ubuntu.com/community/LucidUpgrades?highlight=%28\bCategoryUpgrade\b%29]("https://help.ubuntu.com/community/LucidUpgrades?highlight=%28%5CbCategoryUpgrade%5Cb%29")

Your right. I meant 8.04. It said, It allowed me to upload 10.4 in the update manager and so that's what I did. 



[QUOTE=mörgæs]Since 10.04 runs well in a live environment, I would go for a backup and a clean install.[/QUOTE]

Well, I actually backed up my files beforehand, so a clean install is definitely an option if someone can't figure out what this error message is and how I can resolve it.

---

### Post by mörgæs on 2010-09-17
When you install, remember to have wired internet access. Besides that there should not be anything particular to be aware of.

---

### Post by wilee-nilee on 2010-09-17
I would just do a fresh install, 8.04 was ext3 and grub-legacy, and the error message except for the real geeks, means little to even those of us that are well acquainted with Linux. With a upgrade it could be any sort of problems. I would cut your losses and benefit from the fresh install, since your all backed up.

---

