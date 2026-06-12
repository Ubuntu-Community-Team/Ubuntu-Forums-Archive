---
title: "reinstall apache, mysql and php"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by jpgeerets on 2007-02-05
folks,

i want to re-install Apache2, mysql and php on my ubuntu server.
i have messed up the LAMP config.
at this moment i have troubles with the config of php5 and mysql.
therefor i guess the best is to re-install and make new config settings for apache2, mysql and php.

this machine is in production at this moment for dhcp, file server. 
its important that this will continuing...

i hope someon can give some advice....

tnx...
Jean-Paul

---

### Post by az on 2007-02-05
If you just messed up the configs, delete them from /etc and start over - reinstalling the packages will not get rid of the configs.  But, exactly what is wrong?

---

### Post by jpgeerets on 2007-02-05
tnx for fast reaction!

i installed a lamp-server.
this seems to work ok.
after that i install/config several of things... like dhcp.

when this works fine, i want to install cacti.

this went wrong.
finaly i installed php4 instead of php5.
i guess there all my connections r gone...

cacti still doesnt work.

install of php5 again. install / reconfig cacti again

finaly cacti seems to work. i can launch it. can login, can make devices
but, i can not make graph's....
this seems to be the problem there is not a good config of php5 and mysql.

i cost me so much hours of work.... 
therefor i was thinking, perhaps i need to re-install the apache2-mysql-php.

i guess my problem at this moment is a broken config between php5 and mysql.
when i give the command: php -m there is no mysql in the output list.

Jean-Paul

---

### Post by az on 2007-02-05
If you are using php5, be sure that you have the apache2-mod-php5 package installed.

---

### Post by jpgeerets on 2007-02-05
well,

php and apache2 works i think.
i can also run phpmyadmin.
this is no problem.

i guess the problem is to draw the graph's, php need the information of the mysql database.
and he wound make a connection to that.

Jean-Paul

---

### Post by blkmax on 2007-02-06
When you are connecting to the database, are you connecting localy or remotely.

If you are connecting remotely and have re-installed mysql, you may need to modify your /etc/mysql/my.cnf file to replace the default value of  bind-address          = 127.0.0.1 to  bind-address          = server.ip.address.

this will ensure that you are scanning for port 3306 on your external ipaddress and not just localy.


hope this helps.

Marc

---

### Post by jpgeerets on 2007-02-06
hi marc,

i connect localy to the database....

tnx for your advice!

Jean-Paul

---

