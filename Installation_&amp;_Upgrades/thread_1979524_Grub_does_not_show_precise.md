---
title: "Grub does not show precise"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by BcRich on 2012-05-13
I installed precise and everything went fine. i then rebooted after installation was completed expecting to see a new os in my grub menu. but sadly not :(
I have a 500GB drive that is partitioned as 200 and 300. Fedora used to occupy the 200, but i formatted that partition and installed precise on it. 
I still use ubuntu 10.10 which is working as normal (and I'd like to keep it that way :) ) and when i check out sda2 (with nautilus) which is where precise is supposed to be installed, it all seems to be there. in other words it seems that precise is installed correctly but just not being recognized by the boot loader.
this is my grub version
grub-install (GRUB) 1.98+20100804-5ubuntu3.3 
Also Fedora still shows up in my boot menu, but no longer exists.
Any idea what's going on here?

---

### Post by BcRich on 2012-05-13
yipes my bad
```
sudo update-grub
```
fixed it :oops:

---

### Post by grahammechanical on 2012-05-13
Did you get an option asking where to install Grub or which Grub to use? I did. You may have selected to keep the 10.10 Grub which is why you needed to run update-grub.

Regards.

---

