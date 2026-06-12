---
title: "Mounting failure during Ubuntu update"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by Lloyd_Brown on 2014-09-24
My wife got a notice to update her Ubuntu and followed the directions. The netbook is setup for dual boot.  Something went wrong with the update and this is what the screen looks like upon booting into Ubuntu:
mount: mounting /dev/loop0 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)


Is there anything I can do to complete the update or do I have to reinstall from a USB drive?
If I have to reinstall, is there any way I can rescue her files after booting from Windows?

Thanks!

---

### Post by TheFu on 2014-09-24
Is there a rescue mode option in the boot screen?
Can you check for full storage on /boot?
Did you happen to use either LVM or encryption during the original install?

Oh - and which 2 OSes are on it?  Ubuntu 14.04 and Mint?

---

