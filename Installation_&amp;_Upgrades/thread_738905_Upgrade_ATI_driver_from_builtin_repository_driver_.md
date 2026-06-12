---
title: "Upgrade ATI driver from builtin repository driver to ATI 8.3 driver"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by juky on 2008-03-29
Hi folks,


has anyone succeeded to upgrade ATI driver from built in repository 7.x version to the latest 8.3 version driver from ATI website? I have tried both Envy and this method: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)
 - but without any success. I am Gutsy user with ATI X700 PCIE graphic card.

Although I have been following instructions carefully in  both cases X system would not start :( and I had to revert to Xorg driver by executing 
> sudo dpkg-reconfigure xserver-xorg

Has anyone succeeded, and, if yes, what method did you use?


Thanks in advance,
juky

---

### Post by daveerickson on 2008-03-29
I have used these instructions and it has worked great for me.
[http://www.phoronix.com/forums/showthread.php?t=7193](http://www.phoronix.com/forums/showthread.php?t=7193)
I am running a Radeon 9700 pro. Also, in order to use these instructions you will need to change some of the commands so they point to the correct version you are installing, but other than that these instructions can be used for any version.

---

### Post by juky on 2008-03-29
Thanks, this guide you provided is like the guide i provided in first post, just bit shorter.

I'll try it again.

---

