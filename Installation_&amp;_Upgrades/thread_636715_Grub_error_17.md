---
title: "Grub error 17"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by edwardcix@hotmail.com on 2007-12-10
Hi guys
my scenario is that I booted winxp to delete the old one and put this new fixed version
so I deleted the win partition and when I tried to put the other back I got this error (too many partition or something) the problem is that now Ubuntu doesnt start so I setup the GRUB and thats what it shows on sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *        7584       14392    54693292+  83  Linux
/dev/sda3           14393       14593     1614532+  82  Linux swap / Solaris

```

so after that I reboot and I get error 17 if starting Ubuntu
I really need to backup the files on my Ubuntu :S

---

### Post by Pumalite on 2007-12-10
Boot a Live CD and backup your files.
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

---

