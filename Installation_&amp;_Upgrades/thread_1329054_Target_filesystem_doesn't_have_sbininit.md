---
title: "Target filesystem doesn't have sbin/init"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by FMaz008 on 2009-11-17
Hi !

I've a quite big problem right now. I've searched, and all the solutions are pretty old ( version 6 ... ) so I'm reposting:


After I've done the Upgrade from Jaunty to Karmic, I now can't boot. (well, the last one, as I can't boot, I'm not quite sure)


anyway, here is the error:
> 
Target filesystem doesn't have sbin/init

BusyBox v.1.1.3

/bin/sh: can't access tty; job control turned off

(initramfs)



Solution #1:
I've used a Ubuntu 7.04 live CD to boot and try to edit the /boot/grub/menu.lst . I've tried to remove the UUID and use a path:

root=/dev/sda1

Changed nothing (the UUID was right.

Solution #2:
Still on the live CD, I've tried to mount the /dev/sda1/ , and then to do this:
sudo chroot /media/disk
sudo aptitude reinstall ubuntu-minimal

After, I've checked in /media/disk/sbin/ and I really do have a file named "init".



I still have the same error. What should I do now ?
Why can't I just boot correctly using my last kernel ?


Thanks for the help, I really hope to find a solution soon...

---

