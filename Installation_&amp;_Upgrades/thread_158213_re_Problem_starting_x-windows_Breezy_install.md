---
title: "re Problem starting x-windows Breezy install"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by donaldd on 2006-04-10
I'm trying to help a friend start with Ubuntu, he owns a Dell Inspiron 9400, after a dual boot install X-windows seems to be broken, I tried dpkg-reconfigure xserver-xorg with no success. The graphic card used is a shared memory Intel® Media Accelerator 950. Dmesg gives the following error messages 
Vga compatible controller Intel Corp unknown device 27a2 (rev os)
Display controller Intel Corp unknown device 27a6 (rev os)
Appreciate if someone can point me in the right direction

Thanks Donald

---

### Post by Kapre on 2006-04-10
donaldd - try a live CD on it first and then look at the config that it is using (once its up and running). I just installed Xubuntu on my daughter's PC (Cel. 433, 128 Meg, intel810[built in] and 4 gig HD) and I also had trouble with xserver but I just did "dpkg-reconfigure xserver-xorg" and made sure to select the appropriate driver.

K

---

