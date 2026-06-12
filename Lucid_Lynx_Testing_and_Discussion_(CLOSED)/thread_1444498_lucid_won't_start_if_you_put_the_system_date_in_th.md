---
title: "lucid won't start if you put the system date in the past?"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xens on 2010-04-01
Hi, I was playing with the date command yesterday, I had to set my computer date in the past because I was testing a script in different conditions. 

When I rebooted my computer, fsck hold the computer saying that the last filesystem check was in the future, I had to boot from an USBkey and chroot to my frozen system to change the date and fix the problem.

Can someone with a VM try this operation ? 

Of course to reproduce this behavior fsck had to be started one time before you change the system date ans reboot.

Thanks, Romain

---

