---
title: "Leaking memory 14.04 LTS"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-05-01
I made a fresh installation 14.04.2 LTS Server (AMD64) and after reboot I get as first message on system console:

"no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory"

During the installation I chose only 'SSH Server' and 'Samba server'

What is the reason for this error message and how do I get rid of it ?

---

### Post by zkab on 2015-05-01
I found the solution ... [http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory](http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory)

---

