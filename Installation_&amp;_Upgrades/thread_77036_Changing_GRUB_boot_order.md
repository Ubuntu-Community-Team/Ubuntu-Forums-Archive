---
title: "Changing GRUB boot order"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by breezey on 2005-10-16
I have my Ubuntu version 5.04 installed as dual boot with Windows XP. How could I change the order of GRUB boot list so that Windows XP become the first on the list (will boot by default if I don't press any key on the keyboard)? Thanks.

---

### Post by xristos on 2005-10-16
In a console type ```
sudo gedit /boot/grub/menu.lst
``` 
You will find a line that says "default 0"
Change the number to correspond to the line you want to boot from .
In your case I am guessing it should be 4 . 
Good luck

---

