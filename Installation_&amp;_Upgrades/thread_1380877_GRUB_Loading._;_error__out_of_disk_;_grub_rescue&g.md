---
title: "GRUB Loading. ; error : out of disk ; grub rescue&gt;"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Evaris on 2010-01-14
Hi ! Absolute beginner with Linux, using the Ubuntu 9.10 live CD, I've installed it on 3 machines without any problem and the users are very happy.
Unfortunately with my old laptop after install and reboot : 
"GRUB Loading. ; error : out of disk ; grub rescue> "
What can I do ? I'm not familiar with line commands.
Any help would be much appreciated thanks.

---

### Post by Leppie on 2010-01-14
this may be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477430](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477430)
also, what partition is ubuntu on? remember that old systems cannot boot beyond cylinder 1024 (this can be circumvented by creating a /boot partition in the lower regions of the drive).

---

