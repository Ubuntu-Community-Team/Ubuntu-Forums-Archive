---
title: "Overheat During Upgrade"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by cloak_of_shadows on 2010-07-09
Okay, so yesterday I was upgrading from Karmic to Lucid. After all the packages were downloaded and installed, the computer restarted as it should. But during the first boot, my computer overheated and shutdown (damn alienware and their factory overclocking:razz:). I restarted the system and it overheated again in about thirty seconds. After that, I put the computer on an air conditioning vent and restarted. Booting into the first thing in my GRUB menu (Ubuntu 2.6.32.23) causes the screen to flash and remain black. So I booted into recovery mode, executed "dkpg" hoping to fix whatever was broken. I think after that I ended up in a terminal (no GUI) and just did "sudo shutdown now". I then rebooted and retried to boot ubuntu 2.6.32.23, it again booted to a blank screen. Below Ubuntu 2.6.32.23 in GRUB I had Ubuntu 2.6.31.19. Booting that works, it first says "mount: mounting none on /dev failed! No such device" and below that "chroot: cannot execute /etc/apparmor/initramfs: No such file or directory". It then boots Ubuntu, which says (in about ubuntu) it is 10.04 LTS - the Lucid Lynx.


So what I'm wondering is:
1) Did the overheat (or anything I did) mess anything up?
2) Why does Ubuntu 2.6.32.23 not boot?
3) Is Ubuntu 2.6.31.19 really Lucid Lynx?
4) If anything is wrong, how do I go about fixing it?


I'm hoping everything I put above was in the order it happened, I'm pretty sure it is. Thanks to anybody who can help!

---

