---
title: "SAMBA on Alpha 6"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-09-23
For some reason my laptop doesn't show automatically, I have to start SAMBA manually. If anyone has that problem, I made a script to put in my /etc/init.d folder.
```
#!bin/bash
sudo -u [COLOR="Red"]<username>[/COLOR] ./samba start
```
it's simple but it works.

---

