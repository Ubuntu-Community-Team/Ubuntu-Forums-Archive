---
title: "Installation Issues with Ubuntu 6.06 LTS"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by sunilvarma on 2006-11-09
hi all, I have experience installing ubuntu 6.06 earlier on my old PC and it worked without any issues.

But now I got a new PC and am unable to install ubuntu. I have the 6.06 LTS liveCD. I have WinXP on my PC and am trying to multiboot ubuntu.

After I boot from the CD and select "Start or Install Ubuntu" from the starting screen, it says "loading vmlinuz..." and "loading initrd..."

Then, it reaches the loading screen, "loading essential drivers... ok" and then "mounting root file system" and thats where it hangs and reaches the busybox shell.

It says "Can't access TTY; job control turned off"

my PC runs on Pentium D processor, Asus P5B mobo and has a SATA harddisk. these are the only two changes from my old PC (it used to have a P4 and IDE hdd).

Someone please help...

Thanks

---

### Post by wkulecz on 2006-11-09
Boot the live install CD and see what is in your /boot/grub/menu.lst file.

should be something like vmlinuz-xxxxxx root=/dev/sdaX where X is the partition you installed to.  If this is OK look at /etc/fstab and make sure the line to mount / is the correct /dev/sdaX

Was this a clean install or did you move your old drive to the new system?

I had a similar problem on a raid install because when I added a raid5 array it usurped the/dev/md0 device name and system wouldn't boot, I had to edit menu.lst and fstab to use /dev/md1 instead of md0 after creating the raid5.  It shouldn't have happened, but it did.

Use the search, there may be issues with certain SATA controllers, but I'd hope that if the installer had the correct drivers it'd be smart enough to set them up for initial boot.

--wally.

---

### Post by sunilvarma on 2006-11-09
i googled and found out that its a issue with the jmicron controller on mobos with the p965 chipset.

anyways i read somewhere that 6.10 resolved this issue. can someone confirm this. i am downloading the iso now.

---

### Post by sunilvarma on 2006-11-09
heres an update. the 2.6.18.2 kernel fixed this issue. so now i need to know if i can get the ubuntu with the latest kernel? i have the 6.10 iso now.

can i edit it some how to have the latest kernel on install?

Thanks

---

