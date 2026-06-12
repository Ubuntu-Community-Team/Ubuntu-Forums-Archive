---
title: "Can I install  Ubuntu Studio?"
date: 2023-04-19
forum: Installation &amp; Upgrades
---

### Post by daveyb415 on 2023-04-19
Machine info: 
Dell Inc. Inspiron 5537 / memory 8GB / Intel® Core™ i7-4500U CPU @ 1.80GHz × 4 / Mesa Intel® HD Graphics 4400 (HSW GT2) / Hard drive 1TB / OS: Ubuntu 22.04.2 LTS / 64-bit / GNOME ver. 42.5
Can I install Ubuntu Studio with Ubuntu Desktop already installed? 

Thx

---

### Post by guiverc on 2023-04-19
You can add the Ubuntu Studio packages into any Ubuntu Desktop, or Ubuntu *flavor* system.

Refer [https://ubuntustudio.org/ubuntu-studio-installer/](https://ubuntustudio.org/ubuntu-studio-installer/)

Yes you could add a second desktop (`ubuntustudio-desktop` or [https://packages.ubuntu.com/jammy-updates/ubuntustudio-desktop](https://packages.ubuntu.com/jammy-updates/ubuntustudio-desktop)) to your existing system, which will result in Ubuntu Studio (using KDE Plasma) and your existing Ubuntu Desktop (GNOME) too, but why not use the installer (*and not end up with two desktops*).

FYI:  If you were asking about dual boot; that would work too, as they are many choices as to how.

---

### Post by yancek on 2023-04-19
It might be simpler to do as suggested in post 2.  You can install 2 versions of Ubuntu on the same computer and even on the same drive.  One problem I can see is that if you have a Legacy/MBR machine, the 2nd install will overwrite the Grub of the first install.  This will happen with both a Legacy/MBR which overwrites the code in the MBR and an EFI install which overwrites the grub.cfg file on the /boot/efi partition of an EFI install.  You would need to then run sudo update-grub from the new install to include the previous Ubuntu.  If you want the current Ubuntu to be in charge of booting rather than Ubuntu Studio, you should be able to install Grub to the Ubuntu Studio partition.  You would need to use the manual (Something Else) option during the install.

---

### Post by slickymaster on 2023-04-19
*Thread moved to **Installation & Upgrades**.*

---

### Post by daveyb415 on 2023-04-26
THx all for the direction.  I may just try to install the packages into my current desktop. Already have to OS installed on this LT, soon I will remove the WIN11 and then that wold be a better time to pursue the multiple Ubuntu desktops. 
peAce

---

