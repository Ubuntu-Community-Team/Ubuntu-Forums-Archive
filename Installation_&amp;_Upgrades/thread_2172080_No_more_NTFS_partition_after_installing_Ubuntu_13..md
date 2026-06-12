---
title: "No more NTFS partition after installing Ubuntu 13.04 alongside Windows 7"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by luca5 on 2013-09-03
I installed Ubuntu 13.04 alongside Windows 7. At the reboot the system started in Ubuntu, without showing the Grub loader with options for Ubuntu or Windows. I have tried using Boot Repair but I had no luck. This is what come up with it: [http://paste.ubuntu.com/6057306/](http://paste.ubuntu.com/6057306/)

Any sudgestions?

---

### Post by Mark Phelps on 2013-09-03
According to that report, you didn't install "alongside" Windows; instead, you "overwrote" Windows. 

The entire Extended partition seems to be Linux-swap. 

There is no evidence of a Windows partition on the drive.

---

