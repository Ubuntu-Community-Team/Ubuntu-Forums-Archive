---
title: "Ubuntu restarts in the middle of kernel upgrade."
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by nic10 on 2015-07-18
Hi all, I am having a problem with apt-get trying to upgrade from linux kernel 3.16.0-41 to 3.16.0-43 on Ubuntu 14.04. When the installation for the upgrade was happening the machine simply restarted on its own. I checked and noticed that the new kerrnel was not being used. I tried running apt-get again and it said that an installation was interrupted and that I should run dpkg. I then ran dpkg --configure -a and the machine restarted in the middle of that one too. Now I am in an endless cycle where I can't use apt-get because the kernel wasn't updated properly, but I can't finish the upgrade because it always restarts on its own and messes it up. Can anyone shed some light on how to fix this problem?

---

### Post by dino99 on 2015-07-18
i suppose your machine have a too high temperature when doing heavy work, and so restart (default choice into the bios/uefi, check it) to protect your hardware.
you might check the fan(s) to remove the dust if any, and be sure than fan(s) works as intended
it needs some fresh air to come in/out; if that hardware have been overclocked, then think to set it back to genuine settings

---

