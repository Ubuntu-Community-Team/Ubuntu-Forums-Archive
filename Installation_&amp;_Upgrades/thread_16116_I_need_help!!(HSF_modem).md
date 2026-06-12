---
title: "I need help!!(HSF modem)"
date: 2005-02-19
forum: Installation &amp; Upgrades
---

### Post by dado on 2005-02-19
i have run make install all works all fine then i run HSF Config and then i got ERROR hsf modem not active (something like this)
what should i do next??
Thanks everyone!

---

### Post by GilGalad on 2005-02-19
Hi,

You can download a .deb package from linuxant which you can install in Ubuntu (hsfmodem_7.18.00.02full_i386.deb from linuxant).

Could you send the output of hsfconfig (_remove the license part_)? What happens if you type: modprobe hsfserial?

---

### Post by dado on 2005-02-19
No the problem was on LINUX HEADERS (wrong version)
now its all OK!!

---

