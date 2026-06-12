---
title: "Dell poweredge 840 and 12.04LTS server"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by Andy_Carver on 2014-07-30
Hi. 



The 860 is certified to run 10.04 server does anyone know how 12.04 or 14.04 server runs    on this hardware?



I am planning to run a plex media server and a few smb file shares that will be accessed infrequently. 



Can anyone see any problems with this setup?

---

### Post by mörgæs on 2014-07-30
Hi, welcome to the fora.

It's more than likely that it will work. If you run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags people can give a more precise answer.

---

