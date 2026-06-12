---
title: "mysql fails after upgrade"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by mfalcon on 2007-08-07
After a recent upgrade and reboot, mySQL won't start. My DVR (MythTV) is a just a hunk of metal without mySQL... I've read through this and many forums seeking a solution, but there isn't an exact match. Any insight will be extremely helpful ... Thanks.

Ubuntu Edgy 6.10 kernel: 2.6.17-12-generic

The error generated when starting mySQL is:
  subprocess post-installation script returned error exit status 1
  dpkg: dependency problems prevent configuration of mysql-server:
  mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
  dpkg: error processing mysql-server (--configure):
  dependency problems - leaving unconfigured


Is this a clue?.... (see below from daemon.log) :
Incorrect information in file: './mysql/db.frm'


=== Output from dpkg configure ===
sudo dpkg --configure -a
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2) ...
* Stopping MySQL database server mysqld [ ok ]
* Starting MySQL database server mysqld [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
mysql-server depends on mysql-server-5.0; however:
Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
mysql-server-5.0
mysql-server

=== Output from dpkq ===
dpkg-query -l '*sql*' | grep ^ii
ii libapache2-mod-auth-mysql 4.3.9-2.1ubuntu1 Apache 2 module for MySQL authentication
ii libdbd-mysql-perl 3.0006-1 A Perl5 database interface to the MySQL data
ii libhsqldb-java 1.8.0.5-2ubuntu1 Java SQL database engine
ii libmono-sqlite1.0-cil 1.1.17.1-1ubuntu7.1 Mono Sqlite library
ii libmono-sqlite2.0-cil 1.1.17.1-1ubuntu7.1 Mono Sqlite library
ii libmysqlclient15off 5.0.24a-9ubuntu2 mysql database client library
ii libqt3-mt-mysql 3.3.6-3ubuntu3.1 MySQL database driver for Qt3 (Threaded)
ii libsqlite3-0 3.3.5-0.2 SQLite 3 shared library
ii mysql-client-5.0 5.0.24a-9ubuntu2 mysql database client binaries
ii mysql-common 5.0.24a-9ubuntu2 mysql database common files (e.g. /etc/mysql
ii php5-mysql 5.1.6-1ubuntu2.6 MySQL module for php5
ii php5-mysqli 5.1.6-1ubuntu2.6 MySQL Improved module for php5
ii python-mysqldb 1.2.1-p2-4ubuntu2 A Python interface to MySQL
ii python-pysqlite2 2.3.2-1build1 python interface to SQLite 3

=== Output from /var/log/daemon.log ===
Aug 3 16:08:43 mediabox mysqld_safe[22535]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Aug 3 16:08:43 mediabox mysqld_safe[22535]: To do so, start the server, then issue the following commands:
Aug 3 16:08:43 mediabox mysqld_safe[22535]: /usr/bin/mysqladmin -u root password 'new-password'
Aug 3 16:08:43 mediabox mysqld_safe[22535]: /usr/bin/mysqladmin -u root -h mediabox password 'new-password'
Aug 3 16:08:43 mediabox mysqld_safe[22535]: See the manual for more instructions.
Aug 3 16:08:43 mediabox mysqld_safe[22535]:
Aug 3 16:08:43 mediabox mysqld_safe[22535]: NOTE: If you are upgrading from a MySQL <= 3.22.10 you should run
Aug 3 16:08:43 mediabox mysqld_safe[22535]: the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
Aug 3 16:08:43 mediabox mysqld_safe[22535]: able to use the new GRANT command!
Aug 3 16:08:43 mediabox mysqld_safe[22535]:
Aug 3 16:08:43 mediabox mysqld_safe[22535]: Please report any problems with the /usr/bin/mysqlbug script!
Aug 3 16:08:43 mediabox mysqld_safe[22535]:
Aug 3 16:08:43 mediabox mysqld_safe[22535]: The latest information about MySQL is available on the web at
Aug 3 16:08:43 mediabox mysqld_safe[22535]: [http://www.mysql.com](http://www.mysql.com)
Aug 3 16:08:43 mediabox mysqld_safe[22535]: Support MySQL by buying support/licenses at [http://shop.mysql.com](http://shop.mysql.com)
Aug 3 16:08:44 mediabox mysqld_safe[22748]: started
Aug 3 16:08:45 mediabox mysqld[22751]: 070803 16:08:45 InnoDB: Started; log sequence number 0 43665
Aug 3 16:08:45 mediabox mysqld[22751]: 070803 16:08:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './mysql/db.frm'
Aug 3 16:08:45 mediabox mysqld[22751]: 070803 16:08:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './mysql/db.frm'
Aug 3 16:08:45 mediabox mysqld[22751]: 070803 16:08:45 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect information in file: './mysql/db.frm'
Aug 3 16:08:45 mediabox mysqld_safe[22762]: ended
Aug 3 16:08:59 mediabox /etc/init.d/mysql[22909]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Aug 3 16:08:59 mediabox /etc/init.d/mysql[22909]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Aug 3 16:08:59 mediabox /etc/init.d/mysql[22909]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Aug 3 16:08:59 mediabox /etc/init.d/mysql[22909]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Aug 3 16:08:59 mediabox /etc/init.d/mysql[22909]:

---

### Post by mfalcon on 2007-08-29
Is there a solution to this problem?

 sudo dpkg --configure mysql-server-5.0
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0

Help Please!

---

### Post by mfalcon on 2007-09-09
It seems a lot of people have having the same problem starting mySQL. Does anyone have a solution to this?

Thanks

---

### Post by transactionlogfiller on 2007-10-20
In my case, I seemed to have a copy of mysql already running which was preventing it from starting up.

I did ps -ef |grep mysql, killed the process, and then the upgrade went smoothly.

---

### Post by mfalcon on 2007-10-22
Even after uninstalling mySQL completely, and doing an upgrade from 6.10 to 7.04, mySQL was not starting. mySQL was never running for me; it failed to ever start after an inline upgrade during July/2007. 

I had to manually remove ALL the mysql database files and re-run the upgrade. Then I did a restore and it's been running since. Good thing that MythTV performs a backup of itself!

For me, this solved the problem.

---

### Post by jimip on 2007-10-31
I had this same error. I found out that I didn't have the loopback interface configured, it wasn't in /etc/network/interfaces. Added the following:

# The loopback network interface
auto lo
iface lo inet loopback

to that file, and restarted networking (/etc/init.d/networking restart) then mysql (/etc/init.d/mysql restart) and all worked OK

Ciao

JP

---

