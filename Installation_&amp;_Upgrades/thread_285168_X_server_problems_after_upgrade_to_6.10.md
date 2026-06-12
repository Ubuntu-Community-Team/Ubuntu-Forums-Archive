---
title: "X server problems after upgrade to 6.10"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Torgeir on 2006-10-26
Hello!
After upgrade to 6.10 this afternoon, I have big problems with X server. Ver 6.06 worked perfect, but after upgrade on my Dell Latitude D610, X server is not working at all. I have done a reinstall by using 'sudo aptitude install xserver-xorg-video-all', and everything looks perfect, but when running 'sudo dpkg-reconfigure xserver-xorg', the following message occurs: /usr/sbin/dpkg-reconfigure: xserver-xorg is destroyed or not completly installed. Cannot connect to X server.:confused: 

Any good suggestions??

Torgeir

---

### Post by h00RU on 2006-10-26
Hello,

You might also need to reinstall xserver-xorg and xserver-xorg-core. then run the reconfigure with dpkg.

H

---

