---
title: "Breezy-Dapper kernel question"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by smokey132 on 2006-04-06
Hello. I was previously using breezy 5.10, with the 2.6.12 kernel. i then followed upgraded to the 2.6.14 vanilla kernel using the HOW-TO guide posted here. Now i have recently done apt-get update and updated to the dapper system, which contains kernel 2.6.15. evreything works fine, when i boot up my system it, tells me loading 2.6.15, and when i type uname -r in the console, i see that the kernel version is 2.6.15. nothing is broken on my system, all previous programs / wireless / externals work.

yet however, i go into the /usr/src/linux folder and try to config the kernel, using make menuconfig, it reported that the kernel version it was trying to configure was 2.6.14ck1. also, the 2.6.14ck1 folder is in the /usr/src folder. i am not sure how to fix this, or what i should do in order to overwrite with the proper 2.6.15 source and config files. any help is greatly appreciated. sorry for the long post, i just wanted to explain in detail. thank you.

---

### Post by al108 on 2006-04-09
Assuming that you did everything else right - like installing necessary packages you probably still have an old simlink the procedure of fixing it is in this guide [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) by tseliot in step 3 in the notes. ..."sudo rm /usr/src/linux" (this will remove the old link)...

---

