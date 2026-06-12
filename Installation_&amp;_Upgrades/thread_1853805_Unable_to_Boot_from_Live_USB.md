---
title: "Unable to Boot from Live USB"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-10-03
I made an Ubuntu 11.04 64 bit Natty Narwhal Live USB image with Universal USB Installer (the recommended program) on Windows 7 64 bit.  I was trying to run Ubuntu from the flash drive, but I kept getting this annoying message:

```
mount: mounting /dev/disk/by-uuid/04aa3697-7bc0-45b5-b86a-77a1e6534bd5 on /root failed: invalid argument
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/sys failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.

No init fount. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)
```

I searched everywhere to fix it.  But then I learned about the wonderful [Linux Live USB Creator]("http://www.linuxliveusb.com/").  I used this program to reformat my flash drive and install the Ubuntu .iso file.  Everything works great now.  :biggrin:

---

