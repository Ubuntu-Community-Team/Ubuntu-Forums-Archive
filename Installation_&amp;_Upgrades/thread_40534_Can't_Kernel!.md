---
title: "Can't Kernel!"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by GOVO on 2005-06-09
Hi ! I am  new here.
I meat a big problem! After I update "linux-image-2.6.10-5-386 (2.6.10-34.1) to 2.6.10-34.2" and reboot, I found that it didn't  boot any more! 
It says :Kernel panic-not syncing:VFS:Unable to mount root fs on unknow-block(0,0).
I can see that some people in Chinese have the same problem! We don't know how to fix it . Can you help me? Thanks! I don't want to reinstall my ubuntu. :neutral:

---

### Post by si_sol on 2005-06-09
Assume that GRUB is your bootloader :
- During boot process, press ESC. It should show GRUB menu
- Select kernel version that come with your default ubuntu install (on my machine, it is 2.6.8.something) 

hope this help

---

