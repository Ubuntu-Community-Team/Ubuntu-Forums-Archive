---
title: "problems: no users, hal fails, device manager fails, no usb..."
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by dona.net on 2007-02-24
Hallo everyone, I'm a new Ubuntu user. I'm trying to install Ubuntu 64bit on my Asus A6Km notebook, with dual-boot with WinXP. But I'm having a LOT of problems:

1) I installed Ubuntu 6.10 from the Desktop CD on my PC. First problem: during partitioning (simply creating root ext3 and swap partitions in the free space), the program gives an error, so after the partition table looks damaged, and I've to format all and reinstall Windows (repeated 2-3 times)

2) I installed Ubuntu from the Alternate CD. The partitioning goes, but he ask me only the user password, not the user name, so after the installation, I can't log in. I can do this only in the recovery mode with root, and creating a new user and so on.

3) I tried to reinstall with Ubuntu DVD, with desktop mode, because the partitions where already created with the previous alternate installation. This time the installation goes, and also he creates my user name.

So, now the installation is ok. Anyway, when I log in, it appears me an error message: "internal error - failed to initialize HAL!". There are also these problems:

1) the device manager doesnt work: when I try to open it from system-administration, a windows appears for a while, then it close immediately. Also opening it with the shell mode, with "sudo hal-device-manager", it logs this error: "could not get owner of name 'org.freedesktop.Hal': no such name"

2) if I plug in a usb key, there isn't the automounting

3) if I plug in the usb mouse, sometimes it doesn't work, and when it works, when I reboot, Ubuntu doesn't start: I must remove the mouse

My notebook has: nVidia 7300, Turion64, bluetooth, wireless, webcam, firewire, dvd... More info here:[http://www.asus.com/products4.aspx?l1=5&l2=24&l3=134&model=794&modelmenu=1](http://www.asus.com/products4.aspx?l1=5&l2=24&l3=134&model=794&modelmenu=1)

I found a lot of posts for HAL problem, but no solution found...
Can you help me?! This isn't encouraging for a new Linux user....
Thank you very much!

---

### Post by dona.net on 2007-04-07
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/hal/+bug/62990](https://launchpad.net/ubuntu/+source/hal/+bug/62990) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I found the solution: the problem is in the kernel. It could be resolved upgrading (forcing the newest version) or recompiling the kernel, or deactivating the ACPI module in the boot startup. There is an icompatibility between the Asus A6 series ACPI and the kernel.
Of course the new version 7.04 won't have this problem.
The bug was in: [https://launchpad.net/ubuntu/+source/hal/+bug/62990](https://launchpad.net/ubuntu/+source/hal/+bug/62990)
An italian version of this solution is here: [http://www.sunt.it/blog/2007/04/errore-hal-su-portatile-asus-a6km-con-linux-ubuntu/](http://www.sunt.it/blog/2007/04/errore-hal-su-portatile-asus-a6km-con-linux-ubuntu/)

Bye

---

