---
title: "Dell Inspiron 5160"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by cage27 on 2007-05-07
I am using a Dell Inspiron 5160 with a XGI Volari-XP5 v2 Graphics card. I have used ubuntu 6.06 and everything worked well. I upgraided to ubuntu 6.10 and the screen goes blank after the splash load up screen, the same happens with ubuntu 7.04 Live CD. The graphics driver is vesa on 6.06 live cd and 7.04 live cd. 6.06 works but 7.04  does not. If its not a graphics driver problem what could it be?

---

### Post by jpmswiss on 2007-05-07
Something similar happened when I installed Ubuntu on my good ol' dell inspirion 4200. The ubuntu 6.10 live cd took forever to boot and eventually froze up.

Thank goodness for the alternate CD! The installation requires more human touch but at the end everything except the wireless lan was correctly installed. This forum solved that issue quickly - thanks to all!

Even just a few days ago I updated to Feisty on the old POS dell and everything is a-ok.

I've been an Ubuntu user for about 6 weeks and love it!

Good luck.

---

### Post by cage27 on 2007-05-09
possible fix... gksudo /boot/grub/menu.lst
remove quiet splash (or splash quiet, however it appears) from your grub entries

---

