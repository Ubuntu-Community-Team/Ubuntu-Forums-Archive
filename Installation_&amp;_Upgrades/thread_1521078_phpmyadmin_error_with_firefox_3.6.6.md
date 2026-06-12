---
title: "phpmyadmin error with firefox 3.6.6"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by gcaine on 2010-06-30
After upgrading firefox with the upgrade manager I can't run phpmyadmin on my local computer with firefox. 

phpmyadmin works with Epiphany,  just not firefox, however phpmyadmin works if I log into the server where my websites are located, so whatever the problem is it's on my local computer.

I get this error after logging in

phpMyAdmin - Error

Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

The only error logs I've been able to find are MySql and Apache

Here's what they say.
Apache
<b>Warning</b>:  Directive 'register_long_arrays' is deprecated in PHP 5.3 and greater in <b>Unknown</b> on line <b>0</b><br />
<br />
<b>Warning</b>:  Directive 'magic_quotes_gpc' is deprecated in PHP 5.3 and greater in <b>Unknown</b> on line <b>0</b><br />
[Wed Jun 30 07:48:32 2010] [notice] caught SIGTERM, shutting down
<br />
<b>Warning</b>:  Directive 'register_long_arrays' is deprecated in PHP 5.3 and greater in <b>Unknown</b> on line <b>0</b><br />
<br />
<b>Warning</b>:  Directive 'magic_quotes_gpc' is deprecated in PHP 5.3 and greater in <b>Unknown</b> on line <b>0</b><br />
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Wed Jun 30 07:49:32 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations

mysql
100630  7:48:25 [Note] /usr/sbin/mysqld: Normal shutdown

100630  7:48:25 [Note] Event Scheduler: Purging the queue. 0 events
100630  7:48:26  InnoDB: Starting shutdown...
100630  7:49:18 [Note] Plugin 'FEDERATED' is disabled.
100630  7:49:21  InnoDB: Started; log sequence number 0 43795
100630  7:49:22 [Note] Event Scheduler: Loaded 0 events
100630  7:49:22 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.3'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

---

### Post by Ilalmi on 2010-07-01
Hi,

this doesn't look like a firefox problem. 

Have a look at the  directory where your php sessions are stored (probably /var/lib/php5). Is  apache allowed to write to it?

Another idea: your php doesn't like some of the functions used by your phpmyadmin version. Those functions are deprecated, which means, they won't be available in future php versions.
Therefore upgrading phpmyadmin could also solve your problem.

---

