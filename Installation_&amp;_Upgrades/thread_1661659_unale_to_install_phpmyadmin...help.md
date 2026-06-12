---
title: "unale to install phpmyadmin...help"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by noobad@linux on 2011-01-07
root@ravi-laptop:/home/ravi# [B] apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dbconfig-common javascript-common libjs-mootools libmcrypt4 libt1-5 php5-gd php5-mcrypt wwwconfig-common
Suggested packages:
  libmcrypt-dev mcrypt postgresql-client apache apache-ssl
The following NEW packages will be installed:
  dbconfig-common javascript-common libapache2-mod-auth-mysql libjs-mootools libmcrypt4 libt1-5 php5-gd php5-mcrypt
  php5-mysql phpmyadmin wwwconfig-common
0 upgraded, 11 newly installed, 0 to remove and 203 not upgraded.
Need to get 5,404kB of archives.
After this operation, 21.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main dbconfig-common 1.8.44ubuntu1 [474kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe wwwconfig-common 0.2.1 [22.8kB]                             
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe javascript-common 7 [3,854B]                                
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libapache2-mod-auth-mysql 4.3.9-12ubuntu1 [25.6kB]              
Get:5 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe libjs-mootools 1.2.4.0~debian1-1 [248kB]                    
Get:6 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe libmcrypt4 2.5.8-3.1 [76.1kB]                               
Get:7 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe libmcrypt4 2.5.8-3.1 [76.1kB]                               
Get:8 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libt1-5 5.1.2-3build1 [155kB]
Get:9 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main php5-gd 5.3.2-1ubuntu4.5 [34.8kB]                       
Get:10 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe php5-mcrypt 5.3.2-0ubuntu1 [15.2kB]                        
Get:11 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main php5-mysql 5.3.2-1ubuntu4.5 [64.2kB]                   
Get:12 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe phpmyadmin 4:3.3.2-1 [4,285kB]                             
Fetched 5,390kB in 8min 30s (10.6kB/s)                                                                                
Preconfiguring packages ...
Selecting previously deselected package dbconfig-common.
(Reading database ... 158702 files and directories currently installed.)
Unpacking dbconfig-common (from .../dbconfig-common_1.8.44ubuntu1_all.deb) ...
Selecting previously deselected package wwwconfig-common.
Unpacking wwwconfig-common (from .../wwwconfig-common_0.2.1_all.deb) ...
Selecting previously deselected package javascript-common.
Unpacking javascript-common (from .../javascript-common_7_all.deb) ...
Selecting previously deselected package libapache2-mod-auth-mysql.
Unpacking libapache2-mod-auth-mysql (from .../libapache2-mod-auth-mysql_4.3.9-12ubuntu1_i386.deb) ...
Selecting previously deselected package libjs-mootools.
Unpacking libjs-mootools (from .../libjs-mootools_1.2.4.0~debian1-1_all.deb) ...
Selecting previously deselected package libmcrypt4.
Unpacking libmcrypt4 (from .../libmcrypt4_2.5.8-3.1_i386.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.1.2-3build1_i386.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.3.2-1ubuntu4.5_i386.deb) ...
Selecting previously deselected package php5-mcrypt.
Unpacking php5-mcrypt (from .../php5-mcrypt_5.3.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.3.2-1ubuntu4.5_i386.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.3.2-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                [ OK ]
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up dbconfig-common (1.8.44ubuntu1) ...

Creating config file /etc/dbconfig-common/config with new version

Setting up wwwconfig-common (0.2.1) ...
Setting up javascript-common (7) ...

Setting up libapache2-mod-auth-mysql (4.3.9-12ubuntu1) ...
Setting up libjs-mootools (1.2.4.0~debian1-1) ...
Setting up libmcrypt4 (2.5.8-3.1) ...

Setting up libt1-5 (5.1.2-3build1) ...

Setting up php5-gd (5.3.2-1ubuntu4.5) ...
Setting up php5-mcrypt (5.3.2-0ubuntu1) ...
Setting up php5-mysql (5.3.2-1ubuntu4.5) ...
Setting up phpmyadmin (4:3.3.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf

Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@ravi-laptop:/home/ravi# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                [ OK ]
root@ravi-laptop:/home/ravi# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

i have already installed mysql-server and apache2
unable to figure out what the problem is...please help

---

### Post by theDaveTheRave on 2011-01-07
Are you sure??

have you tried to access phpmyadmin from your web browser?

all the messages are reporting success, and apache restarted ok?

you should be able to go to 
http://<ipaddress>/phpmyadmin

if you are accessing a mysql dbase on your local machine change <ipaddress> to 127.0.0.1 or localhost
If it is another pc that is serving the web pages use the ip address of that terminal instead.

You may need to ensure that you have the php module correctly loaded into apache.
Also check the location of your <userdir> directory in the apache config, you may need a symbolic link or something?

Unfortunately I don't routinely use phpmyadmin, I use either the monitor or mysql gui tools.

David

---

