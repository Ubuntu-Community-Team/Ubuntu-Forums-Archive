---
title: "mysqld_multi won't start"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-09-27
hallo

I have compiled and installed mysql. mysql works fine but it won't work with mysqld_multi. i changed my my.cnf file to:

```

# Example MySQL config file for small systems.
#
# This is for a system with little memory (<= 64M) where MySQL is only used
# from time to time and it's important that the mysqld daemon
# doesn't use much resources.
#
# You can copy this file to
# /etc/my.cnf to set global options,
# mysql-data-dir/my.cnf to set server-specific options (in this
# installation this directory is /server/mysql/var) or
# ~/.my.cnf to set user-specific options.
#
# In this file, you can use all long options that a program supports.
# If you want to know which options a program supports, run the program
# with the "--help" option.

# The following options will be passed to all MySQL clients
[client]
#password       = your_password
port            = 3306
socket          = /tmp/mysql.sock

# Here follows entries for some specific programs

# The MySQL server
#[mysqld]
#port           = 3306
#socket         = /tmp/mysql.sock
#skip-locking
#key_buffer = 16K
#max_allowed_packet = 1M
#table_cache = 4
#sort_buffer_size = 64K
#read_buffer_size = 256K
#read_rnd_buffer_size = 256K
#net_buffer_length = 2K
#thread_stack = 64K

# Don't listen on a TCP/IP port at all. This can be a security enhancement,
# if all processes that need to connect to mysqld run on the same host.
# All interaction with mysqld must be made via Unix sockets or named pipes.
# Note that using this option without enabling named pipes on Windows
# (using the "enable-named-pipe" option) will render mysqld useless!
#
#skip-networking
server-id       = 1

# Uncomment the following if you want to log updates
#log-bin=mysql-bin

# Uncomment the following if you are using InnoDB tables
#innodb_data_home_dir = /server/mysql/var/
#innodb_data_file_path = ibdata1:10M:autoextend
#innodb_log_group_home_dir = /server/mysql/var/
#innodb_log_arch_dir = /server/mysql/var/
# You can set .._buffer_pool_size up to 50 - 80 %
# of RAM but beware of setting memory usage too high
#innodb_buffer_pool_size = 16M
#innodb_additional_mem_pool_size = 2M
# Set .._log_file_size to 25 % of buffer pool size
#innodb_log_file_size = 5M
#innodb_log_buffer_size = 8M
#innodb_flush_log_at_trx_commit = 1
#innodb_lock_wait_timeout = 50

[mysqldump]
quick
max_allowed_packet = 16M

[mysql]
no-auto-rehash
# Remove the next comment character if you are not familiar with SQL
#safe-updates

[isamchk]
key_buffer = 8M
sort_buffer_size = 8M

[myisamchk]
key_buffer = 8M
sort_buffer_size = 8M

[mysqlhotcopy]
interactive-timeout

[mysqld_multi]
mysqld     = /server/mysql/bin/mysqld_safe
mysqladmin = /server/mysql/bin/mysqladmin
user       = mysql_admin
password   = robbertbd

[mysqld2]
socket     = /tmp/mysql.sock2
port       = 3307
pid-file   = /server/mysql/var2/hostname.pid2
datadir    = /server/mysql/var2
language   = /server/mysql/share/mysql/english
user       = unix_user1

[mysqld3]
mysqld     = /path/to/safe_mysqld/safe_mysqld
ledir      = /path/to/mysqld-binary/
mysqladmin = /path/to/mysqladmin/mysqladmin
socket     = /tmp/mysql.sock3
port       = 3308
pid-file   = /server/mysql/var3/hostname.pid3
datadir    = /server/mysql/var3
language   = /server/mysql/share/mysql/swedish
user       = unix_user2


```

i don't get any errors from mysqld_multi, it just dont start the databases.

Robbert

---

### Post by theDaveTheRave on 2009-01-28
Hi herrbrand,

I am having a similar issue, but I am trying to run 2 MySQL servers on the same terminal.

From what i can tell everything is working fine, but when I try to start the second server with the command 

```

 mysqld_multi start 357 &

```

Nothing seems to happen.

so I do a ps aux....
```

davem@Dartagnon:~$ ps aux | grep mysql
root      5328  0.0  0.1   1772   520 ?        S    11:04   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5359  4.5  4.9 104384 24892 ?        Sl   11:04   1:19 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/lib/mysql/Dartagnon.pid --skip-external-locking --port=3308 --socket=/var/run/mysqld/mysqld.sock
root      5361  0.0  0.1   1700   556 ?        S    11:04   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
davem     6791  0.0  0.1   3008   756 pts/1    R+   11:33   0:00 grep mysql
davem@Dartagnon:~$  mysqld_multi report 2
Reporting MySQL servers
MySQL server from group: mysqld2 is running
davem@Dartagnon:~$ mysqld_multi report 357
Reporting MySQL servers
MySQL server from group: mysqld357 is not running
davem@Dartagnon:~$ 


```

and obviously there is only the first server appearing in the line.


I have checked the log files and it is get this info

```

davem@Dartagnon:~$ more /var/lib/mysql/mysqld_multi.log
Starting mysqld daemon with databases from /var/lib/mysqlTest
mysqld_safe[6780]: started
STOPPING server from pid file /var/lib/mysqlTest/mysql.pid
mysqld_safe[6786]: ended
mysqld_multi log file version 2.16; run: Wed Jan 28 11:35:53 2009

Reporting MySQL servers
MySQL server from group: mysqld2 is running
mysqld_multi log file version 2.16; run: Wed Jan 28 11:35:58 2009

Reporting MySQL servers
MySQL server from group: mysqld357 is not running

davem@Dartagnon:~$ more /var/lib/mysql/mysqld_safe_nostart.log
/var/lib/mysql/mysqld_safe_nostart.log: No such file or directory

davem@Dartagnon:~$ more /var/lib/mysql/mysqld_safe_err.log
/var/lib/mysql/mysqld_safe_err.log: No such file or directory
davem@Dartagnon:~$


```

I'm obviously missing something, I guess that I need to populate the mysql and information_schema databases... but when I run

[code]
sudo mysql_install_db
[code]

All the reports are fine but the contents of the data directory for the second server is't populated with anything??

My questions are this.

I can still log onto the first server, even if I use the port setting for the second "test" server?

here also is the copy of the /etc/mysql/my.cnf

> 
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
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
port            = 3308
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.

##############################################################################
###### please note, there are (or will be!) 2 servers on my laptop, ##########
###### this is the Master server that will talk to a slave located  ##########
###### at the UMR S 787 Myology team, if moving the master (eg when ##########
###### changing to "real" server for backup etc, only copy this part #########
###### of the file into the new location on the new server          ##########
############# Important note #################################################
###### When doing this is will be neccesary to change the name / mdp #########
###### of the server and new master host for the 'replicator' user  ##########
###### If this isn't done, the master / slave link will fail,       ##########
###### and you may LOOSE your data,  You have been warned !!! ################
##############################################################################

### the folowing lines enable the multiple servers to exist######

[mysqld_multi]
mysqld          = /usr/bin/mysqld_safe
mysqladmin      = /usr/bin/mysqladmin
log             = /var/lib/mysql/mysqld_multi.log
user		= mysql


[mysqld_safe]

socket		= /var/run/mysqld/mysqld.sock
nice		= 0
err-log		= /var/lib/mysql/mysql_safe_nostart.log
log-error	= /vqr/lib/mysql/mysql_safe_err.log
user		= mysql

#Use concurrent insert with MyISAM.
skip-concurrent-insert




#If no specific storage engine/table type is defined in an SQL-Create statement the default type will be used.
default-storage-engine=innodb




#Port number to use for connections.
port=3308

##### setting for the master server etc##################

[mysqld2]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#
server-id	= 2
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
#socket		= /var/run/mysqld/mysqld.sock # allready set on line 44.
port		= 3308
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
#skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 0.0.0.0
#
# * Fine Tuning
#
key_buffer_size		= 64M
max_allowed_packet	= 16M
thread_stack		= 128
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
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
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 2 #This has allready been set on line 28
log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 21
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/


############setting for the "test" server#######################
[mysqld357]
server-id	= 357
mysqld		= /usr/bin/mysqld_safe
socket		= /tmp/mysql.sock357
port 		= 1357
pid-file	= /var/lib/mysqlTest/mysql.pid
datadir		= /var/lib/mysqlTest
language	= usr/share/mysql/english
user		= mysql
bind-address 	= 'localhost'


Your help and advice is most appreciated.

David.

---

### Post by theDaveTheRave on 2009-01-28
Hello again all,

I'm adding in some further information on another issue that may or may not be related to this, also it is still mysql_multi / mysqld that is potentially causing the issue.

here is the problem.....

a quick bit of background....

I'm trying to setup a master / slave process across 2 machines, one is my laptop (master), and the other my works desktop (slave).

but when I think that I have everything working happily, if I try to log onto the slave via the monitor or any other method I find that I have lost the connection.

```

davem@Anticlimax:/var/log/mysql$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
davem@Anticlimax:/var/log/mysql$ 

```

so I have a look at the error logs, and I can see that the server immediately shuts itself down as soon as I turn on the "slave" but that it keeps trying to restart (as you would expect if running mysql_safe).

here is a sample of the error log (essentially the same info is repeated all the time)

```
  
davem@Anticlimax:/var/log/mysql$ more /var/log/mysql/error.log
mysqld: File 'var/log/mysql/bin.log.index' not found (Errcode: 2)
090127 11:53:58 [ERROR] Aborting

090127 11:53:58 [Note] mysqld: Shutdown complete

mysqld: File 'var/log/mysql/log-bin.index' not found (Errcode: 2)
090128 14:45:15 [ERROR] Aborting

090128 14:45:15 [Note] mysqld: Shutdown complete

```

so I walked away and did something else for a while ..... 

```


/usr/sbin/mysqld: File '/var/log/mysql/log-bin.index' not found (Errcode: 13)
090128 16:04:15 [ERROR] Aborting

090128 16:04:15 [Note] /usr/sbin/mysqld: Shutdown complete

davem@Anticlimax:/var/log/mysql$ 


```


but when I came back I had the same problem, so I checked again for the <log-bin.index> file, and made sure the permissions were correct....


```

davem@Anticlimax:/var/log/mysql$ ls -la
total 7
drwxr-s---  2 mysql adm   208 2009-01-27 13:03 .
drwxr-xr-x 15 root  root 2944 2009-01-28 16:04 ..
-rw-r--r--  1 mysql adm     0 2009-01-27 12:54 bin.log.index
-rw-rw----  1 mysql adm  3122 2009-01-28 16:04 error.log
-rw-r--r--  1 mysql adm     0 2009-01-27 13:02 log-bin.index
-rw-r--r--  1 mysql adm     0 2009-01-27 13:03 relay.log
-rw-r--r--  1 mysql adm     0 2009-01-27 13:03 relay.log.info


```

the oddity is, where is the definition for the log-bin.index file? I don't have one in the my.cnf file?

should I have one? and if so what is causing MySQL to look for it, and how do I tell it to look elsewhere?

So for informtion here is the my.cnf

```


########now see entry for mysqld (line 48), and innodb (line 121) section for specifics ########

######Note, this terminial will actually be the "slave" to the laptop "Master", this is due to having a "secondary master" on the laptop that will not communicate with the master for use as a "test" server.

# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
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
port		= 3307
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0



#If no specific storage engine/table type is defined in an SQL-Create statement the default type will be used.
default-storage-engine=innodb




#Port number to use for connections.
#port=3307






[mysqld]
#
# * Basic Settings please note, there is only a single server on Anticlimax
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

server-id	= 1
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3307
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english

###Slave settings - various local log files etc###
log-bin			= /var/log/mysql/bin.log
log-bin-index 		= /var/log/mysql/log-bin.index
log-error		= /var/log/mysql/error.log
relay-log		= /var/log/mysql/relay/log
relay-log-info-file	= /var/log/mysql/relay-log.info
relay-log-index		= /var/log/mysql/relay-log.index
slave-load-tmpdir	= /var/log/mysql/
skip-slave-start

####end of slave config info ########


#skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.

#the folowing prevents connection from other hosts, uncomment if required
bind-address		= 0.0.0.0

#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack=128
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
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
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1 ##allready set>
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
######## * InnoDB *##################
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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

####Add these lines to the master server only ########

#innodb_flush_log_at_trx_commit = 1
#sync-binlog = 1

#If no specific storage engine/table type is defined in an SQL-Create statement the default type will be used.
default-storage-engine=innodb




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
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

```

Also I realise that I am posting some of the same stuff twice, I just wanted to keep it all in the same post, in the hopes that it will make things easier for everyone

As allways any help is hugely appreciated.

David

---

