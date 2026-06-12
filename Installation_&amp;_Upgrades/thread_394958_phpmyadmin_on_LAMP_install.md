---
title: "phpmyadmin on LAMP install?"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by polopolo on 2007-03-27
Dear users.

If I install a LAMP install of ubuntu server 6.10, is in that install also included phpmyadmin?

Regards,
polopolo

---

### Post by twistedknight on 2007-03-27
Quick answer no
but to install it you just do sudo apt-get install phpmyadmin

---

### Post by mateuszbaranski on 2007-04-05
> **twistedknight said:**
> Quick answer no
but to install it you just do sudo apt-get install phpmyadmin

But not on the fresh ubuntu server installation. !

Firstly you have to uncomment *universe repositories* in /etc/apt/sources.list to have an access to not restricted ubuntu packages.
Then sudo apt-get update
a then sudo apt-get install phpmyadmin

Gtx 

Mateusz

---

### Post by mateuszbaranski on 2007-04-05
> **twistedknight said:**
> Quick answer no
but to install it you just do sudo apt-get install phpmyadmin

But not on the fresh ubuntu server installation. !

Firstly you have to uncomment *universe repositories* in /etc/apt/sources.list to have an access to not restricted ubuntu packages.
Then sudo apt-get update
a then sudo apt-get install phpmyadmin

Gtx :) 

Mateusz

---

