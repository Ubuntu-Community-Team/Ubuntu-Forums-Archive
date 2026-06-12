---
title: "can't install anything"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by vito_huang on 2007-03-15
since i fail to install mysql-server-5.0 using apt-get install, i can't not install any other package now, everytime i run apt-get install something( like openssl) it stuck at stopping mysql server ( with the following message)

```
sudo apt-get install openssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.24a-9) ...
Stopping MySQL database server: mysqld.
/etc/lsb-base-logging.sh: line 34: RUNLEVEL: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
Starting MySQL database server: mysqld.
/etc/lsb-base-logging.sh: line 34: RUNLEVEL: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.

``` 

it will hang in here forever, when i press  Ctrl+c it have this 
```
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i can't even remove anything(i try dpkg -r mysql-server-5.0, it doesn't remove it).
i also try some post suggest remove bootsplash, but when i try it it prompt i haven't got it install 

what is going on here? how do i fix this problem

---

### Post by Arby on 2007-03-15
A few people seem to be having this problem with mysql. If you check this thread [http://ubuntuforums.org/showthread.php?t=339505](http://ubuntuforums.org/showthread.php?t=339505) there are several suggested fixes. It seems to be related to an incorrect setting in /etc/mysql/my.cnf related to handling InnoDB tables.

If you have trouble post your /etc/mysql/my.cnf here and see if we can spot the problem.

EDIT: you might need to run 'sudo dpkg --configure -a'  to reset apt-get first

---

### Post by vito_huang on 2007-03-15
thank you very much  for reply, i did what you say and i have uncomment skip-innodb in  /etc/mysql/my.cnf and udo dpkg --configure -a
but the problem still there, here is my computer's my.cnf 

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "/var/lib/mysql/my.cnf" to set server-specific options or
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# For compatibility to other Debian packages that still use
# libmysqlclient10 and libmysqlclient12.
old_passwords	= 1
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#
# * Query Cache Configuration
#
query_cache_limit	= 1048576
query_cache_size        = 16777216
query_cache_type        = 1
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#
# The following can be used as easy to replay backup logs or for replication.
#server-id		= 1
log_bin			= /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# According to an MySQL employee the use of BerkeleyDB is now discouraged
# and support for it will probably cease in the next versions.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the ndbd storage daemons,
# not from the ndb_mgmd management daemon.
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1

```

---

### Post by Arby on 2007-03-15
OK, I did some more searching on google. The problem could be this line from your original output ```
/etc/lsb-base-logging.sh: line 34: RUNLEVEL: unbound variable
``` Searching for that exact error in google led me to this thread [http://sidux.org/PNphpBB2-viewtopic-t-78.html](http://sidux.org/PNphpBB2-viewtopic-t-78.html) on another site.

According to that thread the problem is not actually mysql. It is caused by an incorrectly set variable in the file /etc/lsb-base-logging. How to fix it is described on the linked page. I know nothing about that file so read the linked thread carefully and  backup the file before making any changes.

---

### Post by vito_huang on 2007-03-15
cheers Arby, you are right this is nothing to do with mysql, is a basic bug in lsb-base-logging.sh script, because the RUNLEVEL variable is not initialize , so to solve this problem is to initialize the variable

RUNLEVEL =''
 
everything is working now after initialize this variable.

sorry to post this stupid question, i should know the variable is not initialize from this line.

/etc/lsb-base-logging.sh: line 34: RUNLEVEL: unbound variable

it seems quite a lots people have this problem, just wondering why the developer doesn't fix this simple problem

---

### Post by Arby on 2007-03-16
Glad to have helped. Looking at the sidux.org thread it seems like that guy tried to get the developers to fix it and they just ignored him.

---

