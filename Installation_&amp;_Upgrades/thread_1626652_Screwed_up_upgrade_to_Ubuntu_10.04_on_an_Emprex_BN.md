---
title: "Screwed up upgrade to Ubuntu 10.04 on an Emprex BNB-1021"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by elderpav on 2010-11-20
I am a serious newbie when it comes to Linux. I bought an Emprex BNB-1021 mini notebook which came with Ubuntu 8.04 preinstalled. Since that's a relatively old distro, I figured I'd upgrade to 10.04. I downloaded the upgrade and installed it, and right at the end of the process I got an error (I don't recall exactly what it said, but I think the gist was that the installation failed). Anyway, now Ubuntu won't boot. The boot aborts and I get dumped into BusyBox. Here's the output of the screen:

error: unexpectedly disconnected from boot status daemon
libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
 - Boot args (cat proc/cmdline)
   - check rootdelay= (did the system wait long enough?)
   - check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a5f1131b-1de5-481a-a582-ee4e00080c98 does not exist. Dropping to a shell!

BusyBox 1.13.3 (Ubuntu 1:1.13.3-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

I've been browsing around all the threads on this site and have already tried a lot of the proposed solutions with no luck.

Someone suggested going into Grub and choosing Ubuntu 8.04 from the bootlist, but it's not there. 8.04 is gone. I can't revert back to it.

It's been suggested I add 'rootdelay=90' to the end of one of the lines in the commands list before booting, but that has no effect at all.

I've even tried downloading & installing Ubuntu onto a USB thumb drive and booting from that, but that doesn't work for a completely separate reason, the Ubuntu distro on the thumb drive isn't recognizing my video display and the screen comes up all garbled.

I'm out of ideas. Any more suggestions?

---

### Post by ajgreeny on 2010-11-20
I fear you may be unlucky with this netbook.  A quick search on [www.googlubuntu.com](www.googlubuntu.com) came up with this page, which does not give much hope, I'm afraid.
[http://ubuntuforums.org/showthread.php?t=1613607](http://ubuntuforums.org/showthread.php?t=1613607)

---

