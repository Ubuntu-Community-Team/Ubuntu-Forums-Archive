---
title: "Edgy Server post-installation issues (won't boot)"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by stocks29 on 2007-02-15
After installing edgy server this is the error I get when trying to boot.  I think it has something to do with how udev names the device nodes.  During the installation only one of my hard drives was detected (fortunately it was the one I wanted to install the OS on).  My other three drives went undetected during the install.  My drive configuration is as follows:

drive1            60GB          /              on motherboard IDE channel
drive2          400GB          /              on PCI IDE controller
drive3          400GB          /              on PCI IDE controller
drive4          400GB          /              on PCI IDE controller

I should mention that I have two ide controllers that hold the other 3 drives.  Like I said, only the 60 gb drive was detected during the install.  Here is the error:

```
[42949391.130000] EXT3-fs: hde1 couldn't mount because of unsupported option features (3d1bf08).
mount: Mounting /dev/hde1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev fialed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

Any help that anyone could provide would be great.  It doesn't seem to be a grub problem in that it is starting to boot the OS.

---

### Post by bandie on 2007-02-15
seems like It did not detect your PCI card IDE controller.

---

### Post by stocks29 on 2007-02-27
any ideas on how to resolve that?

This is interesting because when I try to install the Desktop version instead of Server it detects all of the drives, but it is a little flakey about letting me select the drives for use....

---

