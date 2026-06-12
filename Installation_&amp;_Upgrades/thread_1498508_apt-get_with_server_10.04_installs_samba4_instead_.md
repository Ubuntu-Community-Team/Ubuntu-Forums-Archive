---
title: "apt-get with server 10.04 installs samba4 instead of samba3"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by rsduhamel on 2010-05-31
I installed ubuntu 10.04 server in VBox. I forgot to check Samba during installation so I installed it later with apt-get. When it was finished, Samba 4 was installed. I did apt-get remove and tried to install samba 3 and can't figure out how to do it. It wants to install Samba4 again. I tried "apt-get install samba3" but no joy. Any suggestions?

---

### Post by lemming465 on 2010-06-04
Does *dpkg-query -l | grep samba* show any additional samba4 packages?  Try removing them too.

---

