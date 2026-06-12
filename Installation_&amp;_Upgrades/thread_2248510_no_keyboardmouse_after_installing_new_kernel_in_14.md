---
title: "no keyboard/mouse after installing new kernel in 14.04 desktop"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by sand7000 on 2014-10-15
After installing Ubuntu Desktop 14.04 I saw that I had kernel 3.13.0-32.  I need 3.13.0-37.  I installed it with 
```

sudo apt-get install Linux-image-3.13.0-37-generic
sudo apt-get install Linux-headers-3.13.0.37
sudo apt-get update
sudo apt-get upgrade
sudo grub-mkconfig -o /boot/grub/grub.cfg

```
Now when I boot I get the option in grub to choose the kernel and either boots fine, however if I choose 3.13.0-37 I get to the password prompt and my keyboard is not responsive.  I am guessing that a necessary kernel module is not being loaded.  I noticed that /lib/modules/3.13.0-37-generic/modules.dep has 696 lines while /lib/modules/3.13.0-32-generic/modules.dep has 3941 lines.  Can anyone explain what I need to do to update the modules being loaded for the new kernel?

---

### Post by sand7000 on 2014-10-15
Fixed it.  I had to run:
```
sudo apt-get  dist-upgrade
```
This increased the number of modules in modules.dep to 3942.  Marking as solved.

---

