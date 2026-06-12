---
title: "boot loader restore after winxp installation"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by angryalf on 2008-09-28
Hi all!

I have next problem:
i have installed kubuntu (sda1 - swap, sda2 - root) & second OS winxp (just install in sda3). After installation winxp i have revrited grub :(
I try recover grub (load on kubuntu install CD with demo mode) then mount my partition (sda2 on /mnt , proc on /mnt/proc & dev on /mnt/dev) and chroot. After hat i do grub-install /de/sda , but this don't help.
Can any have idea to solve this?

Thank you!

---

### Post by WWSmith36 on 2008-09-28
Please read this
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope it helps

---

### Post by angryalf on 2008-09-28
In my case this article don't help......
To solve this i do next:

load from CD ( choise demo kubuntu)
mount my linux root partition to /mnt 
mount -t proc none /mnt/proc
mount --bind /dev /mnt/dev

after that i chroot /mnt /bin/bash

and edit my fstab (change some UUID-xxxx on to /dev/sda1 , you must set your own partitions)

and install lilo.
this help me rstore my system & leave kubuntu & win.

Thanks all to help.

PS: i hope this quick guide help other peoples.

---

### Post by SuperSonic4 on 2008-09-28
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

Since this guide uses ubuntu you'll need to:

A) Replace Terminal with Konsole (just press alt+f2 and type Konsole)

B) Replace sudo gedit/boot/grub/menu.lst with kdesu kwrite /boot/grub/menu.lst (graphical) or sudo kwrite /boot/grub/menu.lst (in konsole)

---

