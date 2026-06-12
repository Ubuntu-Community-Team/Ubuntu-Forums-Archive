---
title: "Installed mysql 5.5 on Xub. 14.04 but can't login to it"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by mynot on 2014-11-19
Installed, removed and re-installed mysql several times using apt-get and Synaptic. It won't let me login as root. There's lots of advice, most of it like this:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
but nothing will fix it. I stop the demon and run mysqld with --skip-grant-tables option as the above reference suggests. The next step is:
~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost'....
Thanks

---

### Post by mynot on 2014-11-21
After 4 days of struggle I dicover that
$ mysql -u root -p
asks me for a password which then gets me in. Haven't noticed any reference to this anywhere.
On to the nest battle.

---

