---
title: "php and mysql on Ubuntu 18.04"
date: 2022-10-25
forum: Installation &amp; Upgrades
---

### Post by merrittr2 on 2022-10-25
I have an ubuntu 18.04 install (needs to be that) I upgraded the php and mysql and now I am getting the errors below in syslog...any ideas?



Oct 24 21:39:06 qh systemd[1]: Starting Clean php session files...
Oct 24 21:39:08 qh sessionclean[6604]: PHP Warning:  PHP Startup: Unable to load dynamic library 'mysqli' (tried: /usr/lib/php/20210902/mysqli (/usr/lib/php/20210902/mysqli: cannot open shared object file: No such file or directory), /usr/lib/php/20210902/mysqli.so (/usr/lib/php/20210902/mysqli.so: undefined symbol: mysqlnd_global_stats)) in Unknown on line 0
Oct 24 21:39:08 qh sessionclean[6604]: PHP Warning:  PHP Startup: Unable to load dynamic library 'pdo_mysql' (tried: /usr/lib/php/20210902/pdo_mysql (/usr/lib/php/20210902/pdo_mysql: cannot open shared object file: No such file or directory), /usr/lib/php/20210902/pdo_mysql.so (/usr/lib/php/20210902/pdo_mysql.so: undefined symbol: pdo_parse_params)) in Unknown on line 0
Oct 24 21:39:11 qh sessionclean[6604]: PHP Warning:  PHP Startup: Unable to load dynamic library 'mysqli' (tried: /usr/lib/php/20210902/mysqli (/usr/lib/php/20210902/mysqli: cannot open shared object file: No such file or directory), /usr/lib/php/20210902/mysqli.so (/usr/lib/php/20210902/mysqli.so: undefined symbol: mysqlnd_global_stats)) in Unknown on line 0
Oct 24 21:39:11 qh sessionclean[6604]: PHP Warning:  PHP Startup: Unable to load dynamic library 'pdo_mysql' (tried: /usr/lib/php/20210902/pdo_mysql (/usr/lib/php/20210902/pdo_mysql: cannot open shared object file: No such file or directory), /usr/lib/php/20210902/pdo_mysql.so (/usr/lib/php/20210902/pdo_mysql.so: undefined symbol: pdo_parse_params)) in Unknown on line 0
Oct 24 21:39:13 qh systemd[1]: Started Clean php session files.

---

