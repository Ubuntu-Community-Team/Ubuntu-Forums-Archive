---
title: "root password"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by behrad_es on 2005-10-08
hi
i install the ubuntu 5.04 . in the instalation never ask me root password.
now ,that i want use root user for managing system ask me root password and i dont no password, because i didnt define it.

please tell me how can i get my root password?
thanks

---

### Post by xristos on 2005-10-08
when it asks you for password it doesn't ask for the root password but for YOUR  
password .
In Ubuntu the root account is disabled by default

---

### Post by tehwa on 2005-10-08
Hi,

This wiki entry should answer some questions for you:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You have entered your user password during setup, this password will be the sudo password, the password used whenever an application requests root priveleges.

---

### Post by behrad_es on 2005-10-08
my self find the answer
i must type :

sudo passwd root

its run first time with my user password.:p

---

