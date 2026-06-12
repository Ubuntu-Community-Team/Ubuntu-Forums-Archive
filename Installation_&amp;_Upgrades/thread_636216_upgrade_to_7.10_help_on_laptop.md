---
title: "upgrade to 7.10 help on laptop"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by brucem91 on 2007-12-09
Hello. I run ubuntu on a dual boot laptop with vista, so I can boot the laptop to ubuntu or vista(my sisters laptop, and I occasionly need vista).  Regardless, I just used the internal upgrader to upgrade to 7.10. The upgrade worked fine. However, I can no longer get online via ethernet cable. The wireless card seems to be read, but I am not sure on that. Another error I get is that when I turn on the laptop, I get a HAL error after I log in. I dont know why this is, and does that have to do with ethernet connectoin? I am also using a ML1309 gateway laptop. 
Please help
Bruce

---

### Post by cmnorton on 2007-12-09
Hopefully, you backed up the VISTA portion of the system. If not, you will do that before doing anything else. I've found that by preserving some files allows you to do an upgrade but answer the various questions that ask you whether you want files overwritten or not, you can answer yes to overwrite.

I needed to preserve copies of /etc/hosts/, /etc/services, my /home directory, changes to sendmail, and so on, and then let the installation proceed by updating all the files it needed to.

I did not do this on a 6.06 --> 6.10 --> 7.04 --> and then the 7.10 upgrade resulted in a very slow desktop and, yes, HAL errors.

It may be you can clear these errors through re-installation. However, I've now gone through two 7.10 upgrades on two very different pieces of older hardware, and these went smoothly. In each case, I let the files be overwritten. One of these upgrades was the very same laptop that had the HAL errors.

---

### Post by brucem91 on 2007-12-11
Alright, yes, ubuntu was way slower when I upgraded. Today, I got my Ubuntu CD in the mail from Canonical Ltd. I got some space on the HD, unallocated, and ubuntu created a partition there and is installing 7.10 via CD, not as an upgrade from 7.10. I am okay now, at least I should be. If I still have trouble, I will reply
Thanks
Bruce

---

