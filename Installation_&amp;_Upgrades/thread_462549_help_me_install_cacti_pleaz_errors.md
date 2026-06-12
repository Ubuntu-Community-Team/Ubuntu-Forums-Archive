---
title: "help me install cacti pleaz errors"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by asnd16 on 2007-06-02
OK I am using the community guide to install but am unable to get past 

[https://help.ubuntu.com/community/Cacti?action=show&redirect=CactiHowTo]("https://help.ubuntu.com/community/Cacti?action=show&redirect=CactiHowTo")


Leave the question "MySQL application password for Cacti" blank and hit "Forward".
      Note: The system will create a random password for you, so you don't need to enter one
On the "Webserver type" question, select "Apache2" and then click "Forward"

after this is done I get 	ERROR 1049 I retry and it does not work, then ???? I really have no clue as to what happens.  . . . . when going to localhost/cacti/  I get the following . . .

> 
Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'cacti'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/php/adodb/drivers/adodb-mysql.inc.php:376) in /usr/share/cacti/site/include/auth.php on line 31

soooo I guess I need help here. . . . I am running Feisty Fawn

---

### Post by asnd16 on 2007-06-07
noone? :popcorn:

---

### Post by RedG on 2007-07-20
Sorry I can't help you... I've got the same problem....

Anyone???

Moving from MRTG to Cacti... for fun and for knowledge...

---

### Post by dan_linder on 2007-09-07
I haven't installed/used Cacti, but the error message you're seeing is coming from MySQL.  You might want to double/triple check your MySQL users/permissions and make sure that the "cacti" user IN THE MySQL PERMISSIONS FILE (not the /etc/password file) has the same password set that you've given Cacti and they also have the appropriate MySQL permissions to the Cacti database/tables.

Sorry I can't be more specific, it's been a long time since I used MySQL.

Maybe you can ask on the MySQL forums?

Dan

---

