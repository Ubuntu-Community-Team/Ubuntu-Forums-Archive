---
title: "Remove mysql-server 5"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by LtPitt on 2007-04-13
Hello there!
I'm close to suicide:

if I try

sudo apt-get remove --purge mysql-server

I get:

Configuro mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                                        [ OK ]
chown: impossibile accedere a `/var/run/mysqld': Nessun file o directory
df: `/home/ltpitt/mysql/var/.': No such file or directory
 * /etc/init.d/mysql: ERROR: The partition with /home/ltpitt/mysql/var is too full!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: errore processando mysql-server-5.0 (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
Sono occorsi degli errori processando:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do to eradicate it? :(
I suppose it's some kind of error in my.cnf but I don't have the original file anymore...
:(

---

### Post by spaquet on 2007-07-05
apt-get --purge remove mysql-server-5.0
seems to be working.
I found out this answer having the same problem. When you look few lines above the error you are likely to notice a reference to mysql-server-5.0
Try it a tell me ;)

ERROR: The partition with /home/ltpitt/mysql/var is too full! Seems to be the cause in your case. Free some space on this partition before performing uninstall.

---

### Post by peterLinux on 2007-08-13
apt-get remove mysql* 

Did it for me. After hitting enter on the cmd above you get something like this:


Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting gambas-mysql for regex 'mysql*'
Note, selecting libdspam7-drv-mysql for regex 'mysql*'
Note, selecting mysql-gpl-client for regex 'mysql*'
Note, selecting tntdb-mysql0 for regex 'mysql*'
Note, selecting wzdftpd-back-mysql for regex 'mysql*'
Note, selecting libmysqlclient14-dev for regex 'mysql*'
Note, selecting libapache-mod-auth-mysql for regex 'mysql*'
Note, selecting libmysql-ocaml-dev for regex 'mysql*'
Note, selecting mysqltcl for regex 'mysql*'
Note, selecting mysql-client for regex 'mysql*'
Note, selecting libmysql-ruby for regex 'mysql*'
Note, selecting kmysqladmin for regex 'mysql*'
Note, selecting libqt3-mysql for regex 'mysql*'
Note, selecting ulogd-mysql for regex 'mysql*'
Note, selecting libqt3-mt-mysql for regex 'mysql*'
Note, selecting python2.4-mysqldb for regex 'mysql*'
Note, selecting python-mysqldb instead of python2.4-mysqldb
Note, selecting libdbd-mysql-ruby1.8 for regex 'mysql*'
Note, selecting mysql-query-browser-common for regex 'mysql*'
Note, selecting dpsyco-mysql for regex 'mysql*'
Note, selecting specter-mysql for regex 'mysql*'
Note, selecting mysql-query-browser for regex 'mysql*'
Note, selecting libmysql++-dev for regex 'mysql*'
Note, selecting python-mysqldb for regex 'mysql*'
Note, selecting libmysql++2 for regex 'mysql*'
Note, selecting php5-mysqli for regex 'mysql*'
Note, selecting dbmail-mysql for regex 'mysql*'
Note, selecting sqlrelay-mysql for regex 'mysql*'
Note, selecting openser-mysql-module for regex 'mysql*'
Note, selecting libdbd-mysql-perl for regex 'mysql*'
Note, selecting libapache-mod-acct-mysql for regex 'mysql*'
Note, selecting mysql-server-4.1 for regex 'mysql*'
Note, selecting radiusd-freeradius-mysql for regex 'mysql*'
Note, selecting mysql-server-5.0 for regex 'mysql*'
Note, selecting mydns-mysql for regex 'mysql*'
Note, selecting mysql-client-4.1 for regex 'mysql*'
Note, selecting mysql-client-5.0 instead of mysql-client-4.1
Note, selecting postfix-mysql for regex 'mysql*'
Note, selecting virtual-mysql-server for regex 'mysql*'
Note, selecting mysql-server-5.0 instead of virtual-mysql-server
Note, selecting mysql-client-5.0 for regex 'mysql*'
Note, selecting mysql-common for regex 'mysql*'
Note, selecting libmysqlclient15-dev for regex 'mysql*'
Note, selecting libmysql++2c2a for regex 'mysql*'
Note, selecting libmysqlclient-dev for regex 'mysql*'
Note, selecting libmysqlclient15-dev instead of libmysqlclient-dev
Note, selecting kexi-mysql-driver for regex 'mysql*'
Note, selecting libadamysql1 for regex 'mysql*'
Note, selecting ser-mysql-module for regex 'mysql*'
Note, selecting php4-mysql for regex 'mysql*'
Note, selecting gda2-mysql for regex 'mysql*'
Note, selecting pure-ftpd-mysql for regex 'mysql*'
Note, selecting perdition-mysql for regex 'mysql*'
Note, selecting libmysql-java for regex 'mysql*'
Note, selecting spl-mysql for regex 'mysql*'
Note, selecting libmysqlclient15off for regex 'mysql*'
Note, selecting nagios-mysql for regex 'mysql*'
Note, selecting zabbix-server-mysql for regex 'mysql*'
Note, selecting libmysqlclient12-dev for regex 'mysql*'
Note, selecting php3-cgi-mysql for regex 'mysql*'
Note, selecting proftpd-mysql for regex 'mysql*'
Note, selecting teapop-mysql for regex 'mysql*'
Note, selecting cl-sql-mysql for regex 'mysql*'
Note, selecting mysql-navigator for regex 'mysql*'
Note, selecting bacula-sd-mysql for regex 'mysql*'
Note, selecting libclass-dbi-mysql-perl for regex 'mysql*'
Note, selecting mysql-admin for regex 'mysql*'
Note, selecting nuauth-log-mysql for regex 'mysql*'
Note, selecting libdatetime-format-mysql-perl for regex 'mysql*'
Note, selecting libhk-classes-mysql for regex 'mysql*'
Note, selecting libdbd-mysql-ruby for regex 'mysql*'
Note, selecting python2.5-mysqldb for regex 'mysql*'
Note, selecting python-mysqldb instead of python2.5-mysqldb
Note, selecting liblua5.1-sql-mysql-dev for regex 'mysql*'
Note, selecting libmysql-ruby1.8 for regex 'mysql*'
Note, selecting libapache2-mod-auth-mysql for regex 'mysql*'
Note, selecting courier-authmysql for regex 'mysql*'
Note, selecting mysql-server for regex 'mysql*'
Note, selecting pdns-backend-mysql for regex 'mysql*'
Note, selecting collectd-mysql for regex 'mysql*'
Note, selecting bacula-director-mysql for regex 'mysql*'
Note, selecting mnogosearch-mysql for regex 'mysql*'
Note, selecting libgnademysql1 for regex 'mysql*'
Note, selecting mysql-admin-common for regex 'mysql*'
Note, selecting gnokii-smsd-mysql for regex 'mysql*'
Note, selecting php4-cgi-mysql for regex 'mysql*'
Note, selecting cvm-mysql for regex 'mysql*'
Note, selecting libmysql-ocaml for regex 'mysql*'
Note, selecting liblua5.1-sql-mysql2 for regex 'mysql*'
Note, selecting freeradius-mysql for regex 'mysql*'
Note, selecting alamin-mysql for regex 'mysql*'
Note, selecting yate-mysql for regex 'mysql*'
Note, selecting libdbd-mysql for regex 'mysql*'
Note, selecting snort-mysql for regex 'mysql*'
Note, selecting libmysqlclient15 for regex 'mysql*'
Note, selecting libgnademysql1.6 for regex 'mysql*'
Note, selecting phpbb2-conf-mysql for regex 'mysql*'
Note, selecting libqt3c102-mt-mysql for regex 'mysql*'
Note, selecting python2.3-mysqldb for regex 'mysql*'
Note, selecting www-mysql for regex 'mysql*'
Note, selecting libtime-piece-mysql-perl for regex 'mysql*'
Note, selecting python-mysqldb-dbg for regex 'mysql*'
Note, selecting gambas-gb-db-mysql for regex 'mysql*'
Note, selecting libghc6-hsql-mysql-dev for regex 'mysql*'
Note, selecting dbf2mysql for regex 'mysql*'
Note, selecting pennmush-mysql for regex 'mysql*'
Note, selecting virtual-mysql-client for regex 'mysql*'
Note, selecting mysql-client-5.0 instead of virtual-mysql-client
Note, selecting php5-mysql for regex 'mysql*'
Note, selecting mysql-common-4.1 for regex 'mysql*'
Note, selecting mysql-common instead of mysql-common-4.1
Note, selecting libnss-mysql for regex 'mysql*'
Note, selecting libgnademysql-dev for regex 'mysql*'
Note, selecting libmysqlclient10-dev for regex 'mysql*'
Note, selecting linesrv-mysql for regex 'mysql*'
Note, selecting pike7.6-mysql for regex 'mysql*'
Note, selecting lighttpd-mod-mysql-vhost for regex 'mysql*'
Note, selecting udmsearch-mysql for regex 'mysql*'
Note, selecting libpam-mysql for regex 'mysql*'
Note, selecting php3-mysql for regex 'mysql*'
Note, selecting pike7.4-mysql for regex 'mysql*'
Note, selecting r-cran-rmysql for regex 'mysql*'
Note, selecting courier-authlib-mysql for regex 'mysql*'
Note, selecting libqt3c-mt-mysql for regex 'mysql*'
Note, selecting libnss-mysql-bg for regex 'mysql*'
The following packages will be REMOVED:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0 php5-mysql
0 upgraded, 0 newly installed, 6 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 91.7MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 18741 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                                                                                                [ OK ]
Removing mysql-client-5.0 ...
Removing libdbd-mysql-perl ...
Removing php5-mysql ...
Removing libmysqlclient15off ...
Removing mysql-common ...

---

### Post by tuhin_sustcse on 2008-03-27
hello there,
i've faced problem with mysql server uninstallation. 
when i try 
sudo apt-get remove mysql*
it shows that
[I]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]
i can't understand where's the problem?
plz help me.

---

