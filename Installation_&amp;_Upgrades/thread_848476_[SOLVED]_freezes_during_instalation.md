---
title: "[SOLVED] freezes during instalation"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by alexmcfmartins on 2008-07-03
hi,

im trying to install ubuntu in a computer but when i boot it with the live dvd, it starts up well, i choose the install option,the screen goes blank and it freezes. tried disabling a few options with F6 but still got the same problem. do you think it might have to do with the screen resolution (1650x1050)? should i try to lower the resolution when installing it?

here goes my pc specs:

asus p5n-sli
intel q6600
nvidia 9600gt
4gb ram
500gb x 2 hd
dual monitor asus vw222u


thank you

---

### Post by avtolle on 2008-07-03
Have you seen [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) which may give you something to work from? BTW, on the two hd, are they SATA drives or set up in a RAID array? That also presents some possible problems.

---

### Post by alexmcfmartins on 2008-07-03
both are sata. i'll try to change the resolution and the vga parameter to 824 (1024x768-32bits) to see if something changes and will post the result.

---

### Post by alexmcfmartins on 2008-07-03
booting in safe graphics mode just solved my problems. thanks :)

---

