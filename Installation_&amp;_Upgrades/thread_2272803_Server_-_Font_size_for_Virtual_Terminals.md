---
title: "Server - Font size for Virtual Terminals"
date: 2015-04-08
forum: Installation &amp; Upgrades
---

### Post by WilliamColls on 2015-04-08
Afer installation of Server 14.04.1 the font size for the virtual terminals (tty1, tty2, etc.) is tiny. Where can I chnage this to make it larger?

Thanks for your time. 

William.

---

### Post by ubfan1 on 2015-04-08
Look in the file /etc/default/console-setup.  That contains the font face and font size variables to change.

---

### Post by WilliamColls on 2015-04-09
Thanks ubfan1. Works a treat.

---

