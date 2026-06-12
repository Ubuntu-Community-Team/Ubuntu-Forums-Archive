---
title: "Failed upgrade"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by blwegrzyn on 2010-09-16
I was upgrading from 10.04 to 10.10 and by mistake i closed the terminal window from where I run the :
sudo update-manager -d
now i am getting this error:

blwegrzyn@blwegrzyn-laptop:~$ sudo update-manager -d
ERROR:root:Bad upgrade: 'maverick' != 'karmic' 


is there anyway to force the upgrade or restart it?

thx

---

### Post by blwegrzyn on 2010-09-16
i modified the /etc/*release file to match old version and the upgrade started again, i hope this will help

---

