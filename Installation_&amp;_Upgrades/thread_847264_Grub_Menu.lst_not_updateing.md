---
title: "Grub Menu.lst not updateing"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by gwm on 2008-07-02
Hi,
I have a problem similar to this one:
[http://ubuntuforums.org/showthread.php?t=846242&highlight=grub+menu+update](http://ubuntuforums.org/showthread.php?t=846242&highlight=grub+menu+update)

I have Hardy Heron installed. It installed with kernel 16. I recently noticed that my wife's Pc has an overflow of kernels offered but mine has only one, namely: 16. My /boot directory has all the kernels up to 19 installed but the grub menu was not updated.
I went in and added a reference to the latest kernel manually and booted with that one. When I do that, my wireless LAN card vanishes.
I was wondering if this is not perhaps somehow related to why the later kernels were not added to the boot menu.

---

### Post by tech0007 on 2008-07-02
Make sure you have 'linux-generic' installed. check it in synaptic or type 'dpkg -s linux-generic' in terminal. this will make sure kernel upgrades will update grub.

---

### Post by gwm on 2008-07-02
Thanks,
I do have generic.
I have just reinstalled it using synaptic and I asked for package maintainer's menu. Then I rebooted and all is fine.
** correction **
kernel 18 is working fine. 19 does not see my wireless network card.

---

### Post by gwm on 2008-07-03
I've just updated with the latest kernel-19 and ,my wireless card is visible again. It seems that it is machine dependent, because my wife's pc worked fine with the same wireless card, on the previous revision of kernel-19.
I'm impressed with update-grub. It recognized that I was using kernel-18 and left me there after the update. Now I understand that it reads the comments and uses them to configure the uncommented lines of /boot/grub/menu.lst, it is quite easy to work out how to configure it.

---

