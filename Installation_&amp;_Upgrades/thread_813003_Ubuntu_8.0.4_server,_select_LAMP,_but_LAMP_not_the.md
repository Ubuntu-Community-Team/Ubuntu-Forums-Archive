---
title: "Ubuntu 8.0.4 server, select LAMP, but LAMP not there"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by christiand88 on 2008-05-30
I'm installing Ubuntu Server 8.0.4. At the end of the setup when it asks me to install server software, I select LAMP so I can have Apache and MySQL on it automatically. However, when the installation is finished and it reboots, nothing is present. I enter 'mysql' and it tell me it's not currently installed. I tried searching my computer for apache/mysql and no results.

I realize this can be done manually with apt-get, however I would like to have it done this way.
I'm using 8.0.4 instead of 7.10 because 7.10 doesn't recognize the internal network adapter on my motherboard, ASUS P5E-VM HDMI.

Would anyone know the reason for this? Is LAMP supposed to install apache/mysql/php and deploy it like I expect??

thanks,

christian

---

### Post by christiand88 on 2008-05-30
That is, the networking works automatically when booting into 8.0.4 but not when booting into 7.10.
Would it be possible that the network isn't recognized in the middle of the installation properly, and it can't request the LAMP components?
although i get absolutely no error or anything, it just completes and reboots (doesn't ask me to setup mysql).

---

