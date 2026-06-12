---
title: "pci bus fatal error 18.04 on DELL OPTIPLEX using pcie wireless card"
date: 2019-01-05
forum: Installation &amp; Upgrades
---

### Post by craigjwallace on 2019-01-05
18.04 LTS install on DELL OPTIPLEX MINITOWER 3050 

After 18.04 install and update, "pci bus error" encountered on shutdown and next boot failed to complete after login (hung at black screen).

Solution:
---------

- remove pcie wireless card
- boot and login
- execute update to /etc/default/grub as per: 
  [https://www.youtube.com/watch?v=C3QFt4KL5Fk](https://www.youtube.com/watch?v=C3QFt4KL5Fk)

Boot and login now appears fine.

Regards CJW

---

