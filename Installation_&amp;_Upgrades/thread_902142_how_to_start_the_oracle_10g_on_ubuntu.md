---
title: "how to start the oracle 10g on ubuntu"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by bikramthakur on 2008-08-27
Hi all,


I hav installed oracle 10g on my ubuntu system and don't know hw to start and use the database....frankly speakin m the new user of oracle ..... so will u plz tell me hw to start the database ....

---

### Post by arch0njw on 2008-08-28
Are you using DCHP or a Static IP on the host machine?

I have had problems with DHCP on Windows.  Oracle does **not** play nicely with DHCP.  There is a loopback adapter (driver) to install on Windows, and there might be something similar to do on Linux.

One way I have "cheated" around this is to edit the appropriate Oracle configs to use the hostname instead of the IP.  Sometimes that has fixed it.

---

