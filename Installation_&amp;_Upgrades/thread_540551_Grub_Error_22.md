---
title: "Grub Error 22"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by LonestarZ06 on 2007-09-01
I currently have an HP laptop that has two HDs on it. I shrank the primary partition on the second HD so that I could install Ubuntu 7. I installed it and it finished without an issue. However, I rebooted and I am getting error 22. I have Vista loaded on /dev/sda1 and another vista partition on /dev/sdb1. I created /dev/sdb2 for swap and /dev/sdb3 for root. I have tried following the instructions on [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to help reinstall grub to the right location, but I haven't had any luck. I also went into BIOS to see if I could tell it to use sdb as the primary disk, but there isn't a place to select that. Any ideas would be greatly appreciated. So far, I have tried re-installing grub to /dev/sda1 and /dev/sda with no luck.

---

### Post by Pumalite on 2007-09-01
Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Pumalite on 2007-09-01
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

