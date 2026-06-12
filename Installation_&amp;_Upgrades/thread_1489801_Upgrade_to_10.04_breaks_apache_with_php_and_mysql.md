---
title: "Upgrade to 10.04 breaks apache with php and mysql"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by jxh on 2010-05-21
After upgrading from 9.04 to 10.04 I can no longer run any web apps that use mysql on my local server.

I have Zend Studio 7.1.2 installed.

In apache2 error.log
[INDENT]PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysql.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mcrypt.so' - /usr/lib/php5/ext/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mcrypt.so' - /usr/lib/php5/ext/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysql.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysqli.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/pdo_mysql.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
[Fri May 21 08:03:34 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.2.10-2ubuntu6 with Suhosin-Patch configured -- resuming normal operations
[/INDENT]

The Synaptic Package Manager has similar problems
[INDENT]/usr/sbin/synaptic: error while loading shared libraries: libxapian.so.15: cannot open shared object file: No such file or directory
[/INDENT]


Thanks for your help

---

### Post by jodaka on 2010-05-23
edit your /etc/php5/apache2/php.ini 
search for extension_dir param
it points to some place like /usr/lib/php5/20060613 (or similar)
and after upgrade it should point to /usr/lib/php5/20090626 (on my system at least)

so just fix extension_dir in php.ini and restart apache

---

