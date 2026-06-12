---
title: "Fail to boot after upgrading"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Oriolo on 2008-11-29
Good evening to you!

I installed Intrepid Ibex few weeks ago, everything was OK and it worked wonderfully. Today I made some upgrades, a kernel upgrade from 2.6.27-7 to 2.6.27-9 among others. As I rebooted, I got this message:
> Gave up waiting for boot device.Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/9e387016-bec3-4d32-9c0a-301c6bb6e8d5 does not exist.
Dropping to shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
  

I run Ubuntu on a HP Pavilion dv5000 laptop with an AMD Sempron Processor.
Fortunately, there still was the old kernel entry in /boot/grub/menu.lst, so I could easily start Ubuntu as I did before and for the time being set the old one as default in menu.lst. I checked that the new entry is exactly the same in every detail as the old one, except for the kernel version, so I guess that something must be wrong with the upgraded kernel.
I searched and found that other people had experienced this. Some said that after waiting for a while and then entering "exit" in the shell, the boot process went on and then recomended to set rootdelay=90 on the kernel entry in menu.lst. Didn't work for me. I waited about ten minutes, typing exit from time to time, still the same shell.

Hoping for your help

---

