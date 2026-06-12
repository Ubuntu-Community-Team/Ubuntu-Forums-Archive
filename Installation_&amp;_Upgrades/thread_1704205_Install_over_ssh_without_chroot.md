---
title: "Install over ssh without chroot?"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by tavasti on 2011-03-10
I have old linux installation (Debian Sarge), and only access I have is ssh. 
I need to install Ubuntu 10.04 to it. I tried with Install over ssh <https://help.ubuntu.com/community/Installation/OverSSH> but that fails, since chroot doesn't work:

/mnt/new# chroot .
FATAL: kernel too old

So now I need suggestions how to proceed installation? Alternative installer have option to use ssh as console, but there are quite many steps before network is configured and ssh is available. Network config has to be static, dhcp is not possible.

And another issue is to get that installer booting from hard disk, but I assume that would not be a problem.

Ideas how to continue?

---

