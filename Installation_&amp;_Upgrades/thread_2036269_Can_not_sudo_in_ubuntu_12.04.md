---
title: "Can not sudo in ubuntu 12.04"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by LT72884 on 2012-08-01
Ello all. I am running ubuntu 12.04 in vmplayer. When i open a erminal session, it syas i am running as:

guest-gT6v5g@ubuntu:~$

then i try to run sudo and get the following

guest-gT6v5g@ubuntu:~$ sudo
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [115, -1, -1]: Operation not permitted


why cant i run sudo?

Also it says i do not have permissions to view my home folder.hahaha

thanks

Matt

---

### Post by LT72884 on 2012-08-01
I will say this, every time my vmplayer starts, i log into to my account not guest. But i just noticed that it still says guest. odd.

---

### Post by ajgreeny on 2012-08-01
You do not run sudo with that sole one word command; you use ```
sudo *command*
```or have I totally misunderstood what you're doing?

---

