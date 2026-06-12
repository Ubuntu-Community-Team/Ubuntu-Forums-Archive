---
title: "truecrypt and samba - change of permissions to share"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by dracik on 2008-08-29
Hello,


I have interest to mount volume formated ext3 in truecrypt ver 6.0a with options for changing permissions to let share folders via samba. I have found commands to do it via :

sudo truecrypt --mount-options "rw,sync,utf8,uid=1000,umask=0000" /dev/sdb1 /storage
sudo truecrypt --mount-options=uid=1000,umask=0000 /dev/sda5
sudo truecrypt -m uid=1000,umask=0000 /dev/sda5
and few others variations


The problem is that none variations of those syntax doesn't work for mount options .
Could you help me to find appropriate syntax to provide share for everybody (chmod 777) ?

Thank you
dracik

P.S - I am real ubuntu newbie, so I would appreciate your answer in detailed way ; )

---

