---
title: "Log for do-release-upgrade?"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by mamlouk on 2012-10-19
Just did an upgrade from 12.04 to 12.10 on a workstation working as my file/printer sharing at home. I ran ```
sudo do-release-upgrade
``` from a terminal window, and everything went fine until a very late stage of the upgrade process where an error popped up saying that partition /boot had 0 bytes left (only had 1 kernel installed). The upgrade continued but I could see a whole bunch of errors skimming through my terminal window. The upgrade process ended with exit code 1. I rebooted normally into 12.10, but neither nvidia driver is working nor my HP printer/scanner.

I was wondering if there is a recorded log of the upgrade process so as to troubleshoot the errors that were generated during the upgrade process (now that I removed the old kernel).

thanks

---

