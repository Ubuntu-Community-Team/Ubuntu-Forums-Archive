---
title: "booting trouble"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by berty909 on 2008-03-01
just installed ubuntu 7.10 from live cd. installing went well but when asked to reboot computer restarts and displayed a blank screen with the word grub. it is inviting me to type a command but what is this and why is this nessacery?i let the install partition the hard drive as sugested as there is windows on it as well. tried installing twice but come up with this screen each time.

---

### Post by Herman on 2008-03-01
That usually means GRUB's MBR is okay and it is finding the stage2 file in Ubuntu but it can't find a /boot/grub/menu.lst file for some reason.

You can boot with [Super Grub Disk]("http://sgd.benjamin-butschko.de/")  to get your computer started for now. Super Grub Disk will boot Windows or Ubuntu for you.
When you have Ubuntu booted, please open a terminal and run 'sudo fdisk -lu' and get a copy of the bottom half of your /boot/grub/menu.lst file and post those here and I or someone will help you.
```
sudo fdisk -lu
``````
gksudo gedit /boot/grub/menu.lst
```Or, alternatively, you could try booting up from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")  and write down what commands you needed to edit /boot/grub/menu.lst with later.

Regards, Herman :)

---

