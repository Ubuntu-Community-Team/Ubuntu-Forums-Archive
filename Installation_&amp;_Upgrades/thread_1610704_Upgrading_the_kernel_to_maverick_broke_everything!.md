---
title: "Upgrading the kernel to maverick broke everything!"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by wishingstar on 2010-11-01
Dear all,


  I have been using Ubuntu since 9.04 without many (serious) problems, I  installed the 10.10 CD and put it on a flash drive (after a while or  looking through the web to realize that the startup disk creator breaks  with maverick. Anyway, when I booted from flash, it would get completely  stuck (no cursor, no blinking line at the top, just nothing!). 



So I  went back to my lucid install and did a "update-manager -d". When the  upgrade was done, i rebooted, and was faced with the same problem again.  I had to manually edit the "grub.cfg" file to set the lucid old kernel  as default. Again I was faced with a new problem: virtualbox couldn't  find the kernel files because upgrading the kernel deleted some files  that were required, also, at random times after login, i get no theme and window borders are gone (which I usually solve by running "compiz --replace" in terminal, annoying but not as serious as the virtualbox part).


  What I need to know is if there is a way to upgrade from lucid to  maverick without the new kernel (I still don't understand why it broke,  but oh well!) or to solve the virtualbox problem, as I need to run some windows programs for work.



  My specs are: 



Toshiba Satellite A215

Dual core AMD athlon-X2 ATI Radeon X1200 (been using the default driver for it since jaunty) 

Ubuntu Lucid with latest updates
  

Please help, and thanks in advance

---

### Post by jrev on 2010-11-01
Why not install Maverick in double boot on your Hard disk ?
It would be easier for you to check the Maverick operation and go back to the previous version in case of trouble :P

---

### Post by wishingstar on 2010-11-01
> **jrev said:**
> Why not install Maverick in double boot on your Hard disk ?
It would be easier for you to check the Maverick operation and go back to the previous version in case of trouble :P

Well, I considered that, but i don't like having 2 systems on my laptop. If I could just solve the virtualbox problem, i would be a happy maverick user (don't care much about the new kernel anyway, 2.6.32-25 is good enough for my hardware).

Thanks for the suggestion anyway!

---

