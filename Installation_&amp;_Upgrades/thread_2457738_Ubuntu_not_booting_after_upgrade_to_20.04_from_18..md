---
title: "Ubuntu not booting after upgrade to 20.04 from 18.04"
date: 2021-02-08
forum: Installation &amp; Upgrades
---

### Post by avi-a on 2021-02-08
I upgraded Ubuntu to 20.04 from 18.04. But after the upgrade I'm having trouble booting my system. I'm getting the following message displayed:

[FONT=arial black]/lib/systemd/systemd-udevd: error while loading shared libraries: liblzma.so.5: cannot open shared object file: No such file or directory
Gave up waiting for root file system device. Common problems:
 [/FONT][FONT=arial black]- Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=................................ does not exist. Dropping to a shell!

[/FONT][FONT=arial black]BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu6.3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/FONT]

I tried a few solutions from various forums that involved booting with a live USB stick, but nothing worked. Please somebody suggest how to rescue this. I'm really falling behind with my work.
Ubuntu is installed on sdb4 partition.

---

