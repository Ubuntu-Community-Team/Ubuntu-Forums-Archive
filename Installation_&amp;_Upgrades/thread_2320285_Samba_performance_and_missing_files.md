---
title: "Samba performance and missing files"
date: 2016-04-12
forum: Installation &amp; Upgrades
---

### Post by Hadden89 on 2016-04-12
Hi to all,
I've some troubles with samba yet (all pcs are in the same LAN)
My lubuntu 15.10 can communicate with windows 10 and access to his shares..



I'll post only the modifications I did in smb.conf

[global]
# Tweak performance
  socket options = TCP_NODELAY
(without this the opening was very slow to any share)

[share]
 ;  comment = Ubuntu File Server Share
    path = /home/hadden/share
    browsable = yes
    guest ok = no
    read only = no
    create mask = 0755
(changing LMpolicies in windows I made this work^^)

Everything seems to works quite well, expect for music shared folder, which list only few files, and about performance if it can boost is some way, I'll try it ;)

PS
Sorry for wrong section :(
Please move to networking

---

