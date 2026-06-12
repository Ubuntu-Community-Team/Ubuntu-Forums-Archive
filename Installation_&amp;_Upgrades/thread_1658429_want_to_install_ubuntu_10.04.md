---
title: "want to install ubuntu 10.04"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by Arunbhandari on 2011-01-02
I have already installed ubuntu 10.10 as a dual boot with windows 7. But now I dont like this version and want to install ubuntu 10.04. I am confused whether I have to delete my current ubuntu 10.10 or install 10.04 directly. If I delete ubuntu 10.10 then I wont be able to run windows 7 since GRUB will be disabled, I guess.
I need a suggestion with this.
 Your help will be highly appreciated.

---

### Post by Quackers on 2011-01-02
Welcome to UF :-)
From the live cd/usb you can run gparted and delete the 10.10 partitions then install 10.04 into the free space that is left.
This will make Ubuntu 10.04 boot directly. You can then run ```
sudo update-grub
``` in a terminal which should then make Windows bootable.

---

