---
title: "PHP MySQL library differs from your MySQL server"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by edenred on 2015-06-11
Hello,

after having compiled PHP, I got an issue, phpmyadmin is complaining about

"Your PHP MySQL library version 5.5.43 differs from your MySQL 
server version 5.6.19. This may cause unpredictable behavior."

On many forums I saw I had to reinstall it with apptitude, but I made a manual install/compile of PHP

so I guess I need to recompile PHP with 5.6.19 version of Mysql driver but how do I do that ?

ubuntu 14.04.2, php 5.6.9, apache 2.4.7, mysql 5.6.19 (Let me know if you need more info.)

thanks

---

### Post by SeijiSensei on 2015-06-11
I just updated my 14.04.2 testbed server to all current packages.  Here are my versions:

Apache2: 2.4.7-1ubuntu4.4
php5-common: 5.5.9+dfsp-1ubuntu4.9
php5-mysql: 5.5.9+dfsp-1ubuntu4.9
mysql-server: 5.5.43 - 0ubuntu0.14.01

You've either installed some packages from source or used a repository for a more recent version of Ubuntu than 14.04.2. If so, you're pretty much on your own.  Unless you need a specific feature not available in the Ubuntu repository, you should always rely on the repository versions as they are guaranteed to work together.

It sounds like the major culprit is php5-mysql.  You can try compiling that from source if you find a compatible version.

---

### Post by edenred on 2015-06-12
sh... , I wanted to have the very last version of php
ok thanks then

---

