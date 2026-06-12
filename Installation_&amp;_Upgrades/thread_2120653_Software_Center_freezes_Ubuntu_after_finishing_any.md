---
title: "Software Center freezes Ubuntu after finishing any install"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by bellaseem on 2013-02-27
Hi, I'm having a problem with software center always freezing the computer (ubuntu 12.1) after I install anything, the freeze occurs after the files are downloaded and the changes are applied. The programs install succesfully and I find them when I reboot but the computer freezes and I have to shut it down by unplugging it... So, any solutions? I noticed this is after the new updates...

---

### Post by dino99 on 2013-02-27
you can watch .xsession-errors & /var/log/ to find some usefull warnings/errors

if the problem is really due to software-center (and not due to the unfinished indexing), then choose to use either apt-get or synaptic

---

