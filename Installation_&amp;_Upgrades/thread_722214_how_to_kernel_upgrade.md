---
title: "how to kernel upgrade"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-03-12
I'm kinda new to Ubuntu. I just wondered how to backup my kernel. How to upgrade my kernel. And how do i go back to the backup if something goes wrong? And why do i have to update the kernel? Or do i? And if not, why is it wrong or not?

Right now running dualboot Win Xp and Ubuntu Gutsy 7.10 with Kernel 2.6.22-14-Generic

---

### Post by Pumalite on 2008-03-12
[http://en.wikipedia.org/wiki/Kernel_(computer_science](http://en.wikipedia.org/wiki/Kernel_(computer_science))

---

### Post by peakshysteria on 2008-03-12
Thanks man. I also found [http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/](http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/) and:

Upgrade of the kernel in Debian or Ubuntu Linux

Use apt-get command. First find your kernel version:

$ uname -r

Next find available kernel images:

$ apt-cache search kernel-image

Now install kernel by explicitly specifying version number:

# apt-get install kernel-image-x.x.x-xx

OR

$ sudo apt-get install kernel-image-x.x.x-xx

_______

---

### Post by Pumalite on 2008-03-12
You are welcome.

---

