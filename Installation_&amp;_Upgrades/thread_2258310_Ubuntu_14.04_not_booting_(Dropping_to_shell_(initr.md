---
title: "Ubuntu 14.04 not booting (Dropping to shell (initramfs))"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by ding.xuan on 2014-12-26
Hi, I'm a novice at Ubuntu and I was hoping someone could help. I dual boot Ubuntu/Windows 7 on my computer and recently upgraded from 12.04 to 14.04. Originally, I upgraded using the internal update software, but I've also done fresh installs of 14.04 from a live CD twice and I consistently get the following error:

> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/####(points to partition on which Ubuntu is installed) does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)


Both installs from the live CD appeared to be successful. This error occurs after the computer is completely shutdown and then powered back on. If I boot into Windows, "restart" (not Shutdown), and boot into Ubuntu, I don't get this error and everything appears to function normally. Similarly, if Ubuntu is already loaded, and I restart, it appears to work fine.

I found this thread [http://ubuntuforums.org/showthread.php?t=2229307](http://ubuntuforums.org/showthread.php?t=2229307) , but my problem seems a little different. Any help would be much appreciated!

UPDATE: I tried using boot-repair and I end up with the same error. The log from boot-repair is here: [http://paste.ubuntu.com/9636501/](http://paste.ubuntu.com/9636501/). I've also found that typing "exit" at the initramfs prompt will bring me to the usual Ubuntu login screen. Can someone please help and point me to what is going on?

---

