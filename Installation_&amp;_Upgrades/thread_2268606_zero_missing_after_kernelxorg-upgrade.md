---
title: "zero missing after kernel/xorg-upgrade"
date: 2015-03-10
forum: Installation &amp; Upgrades
---

### Post by ladiko on 2015-03-10
Hello,

i am running Ubuntu 14.04 Server with Xfce4 Gui - all standard repositories. Some days ago i updated my machines with ```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
``` and now it looks like the attached picture. whereever there's a zero, it's invisible:
[ATTACH=CONFIG]260547[/ATTACH]

i have tried it on several machines, everytime with the same result.

---

### Post by dino99 on 2015-03-10
Looks like the LTS kernels always have issues; myself have made the choice to never use them, due to kernel problem/abi issue/conflict with driver
If you want to install recent kernels, then you may have better luck with the kernel-ppa ones  [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

To an empty folder, download the 2 headers + the 2 images you have chosen to install; then from that folder, install by: sudo dpkg -i *

---

### Post by Vladlenin5000 on 2015-03-10
> **9d9 said:**
> Looks like the LTS kernels always have issues

Actually the problem occurred after the OP upgraded the kernel for the one included in 14.10... And no, LTS kernels rarely - if ever - have issues.

To the OP: Any special reason for such upgrade? Why don't you use the 14.10 release straight away?

---

