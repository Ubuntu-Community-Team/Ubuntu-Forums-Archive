---
title: "direct rendering problem"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by tpariel on 2006-08-24
hi all,

Following the suggestion I got in this forun I managed to install the Ati driver and every things seems to work well but I have no direct rendering. After the comand glxinfo I get: direct rendering : No
How can I set the direct rendering for my video card Ati Radeon X600? 

Thanks, Ariel

---

### Post by baldy1324 on 2006-08-24
well the ati driver is unaccelerated and wont give you direct rendering. you can install the restricted modules for your kernel by typing - ```
sudo apt-get install linux-restricted-modules-`uname -r`
``` this will download the all restricted (non-free) drivers that only work for your specific kernel
therefore if you upgrade kernel you have to upgrade this. then type ```
gksudo "gedit xorg.conf"
```the scroll to the part that says Driver ati and change ati to fglrx. then see if you have direct rendering:) 
hope that helped

---

