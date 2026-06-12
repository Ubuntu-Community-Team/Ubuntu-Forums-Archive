---
title: "unable to install mysql 5.7 on ubuntu 18.04"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by aramis1212 on 2018-07-13
i am using the digital ocean instructions to install mysql [https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04)

after i type sudo apt install mysql-server
 iget the error msg
 unable to start mysql server
mysqld: can't read dir of '/etc/mysql/conf.d/'

i used chmod 777 to change permissions on that directory then i ran
sudi apt-get --fix-broken install

only to get the exact same error.

I have seen several threads with a similar issue but none of them ended in a resolution.

is it even possible to install mysql 5.7 on ubuntu 18.04.   If so how? where else can turn to for help on this issue?

---

