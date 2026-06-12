---
title: "Eggdrop help"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by ruvil on 2005-09-10
Hello, i dont know if this post is matching here.. but nevermind.

Umm.. i tried to apt-get install eggdrop today, it downloaded fine and so on.. but now i want to configure it. Where is the config file? and when i tried to run 'eggdrop' this showed up: 
Eggdrop v1.6.17 (C) 1997 Robey Pointer (C) 2004 Eggheads
[22:22] --- Loading eggdrop v1.6.17 (Sat Sep 10 2005)
[22:22] * CONFIG FILE NOT LOADED (NOT FOUND, OR ERROR)

Anyone know how to solve this and where the config file are?

---

### Post by rafakl on 2005-09-10
try with 

man eggdrop

to see if it says where the config file is.

probably in /etc ??

---

### Post by ruvil on 2005-09-11
nope, i cant find it in /etc/ and man eggdrop didnt tell me that either.

---

### Post by xl8r on 2005-09-26
I've got the same problem. Does anyone know any solution to this?

---

### Post by SWAT on 2005-10-07
Just extract the example config file from /usr/share/doc/eggdrop-data/examples/eggdrop.conf.gz
Then you'll need to edit the config file to fit your needs. I recommend putting your config file somewhere like /home/<username>/eggdrop. Then you can run (1st time only) your eggdrop by doing a* "eggdrop -m <path.to.config.file>"*

---

