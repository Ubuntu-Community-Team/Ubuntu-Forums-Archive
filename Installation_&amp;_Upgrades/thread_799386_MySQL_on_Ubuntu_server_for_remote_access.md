---
title: "MySQL on Ubuntu server for remote access"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-19
I am trying to setup my Ubuntu server, which includes NOW also the MySQL server for the web pages. I used the same MySQL server for another server to access the data.

I could not figure it out how to do it.

I tried to change on the server the file my.cnf file to:
bind-address = 192.168.1.22

with the result that the local web server cannot access it, AND that the machine 192.168.1.22 also cannot access the mysql server.

What do I need to do that local web server can access (bind-address = 127.0.9.1) and the remote machien 192.168.1.22 can access.

R.

---

### Post by pdescham49 on 2008-06-05
sad that no one has yet replied to your issue here. 

I too am having issues with this exact problem.

What i have found on "google" it is your friend ;) is that you need to comment out the bind-address in my.conf to get mysqld to listen to any tcp address.

let me know if that worked for you. 

However that didn't work for me perhaps it will work for you. 

Can anyone pleas please assist us?

Here's my issue. a slight variation to yours. 

locally I can do "telnet mywebhost.com 3306" and I get:

```
telnet mywebhost.com 3306
Trying mywebhost.com...
Connected to mywebhost.com.
Escape character is '^]'.
J
5.0.45-Debian_1ubuntu3.3-log&#65533;KNiE\~)K|,Q_gkc.[`QR,!
```

I can also do the same with localhost and the outside ip address it all comes back fine. when i am logged in the servers shell.

From the outside I get noting no response just an infinite hang.  


here's my netstat:```

root@server~$ netstat -a | grep -v listen
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State           
tcp        0      0 *:mysql                 *:*                     LISTEN   

```

So the server is not bound to an ip address it looks like something is blocking it but the problem is where. 

so I disabled my firewall: 
```
root@server:~# iptables -P INPUT ACCEPT
root@server:~# iptables -P OUTPUT ACCEPT
root@server:~# iptables -P FORWARD ACCEPT
root@server:~# iptables -F
root@server:~# iptables -X
root@server:~# iptables -L -v -n 
Chain INPUT (policy ACCEPT 12 packets, 784 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 12 packets, 6880 bytes)
 pkts bytes target     prot opt in     out     source               destination        
``` 

and tried again no go. Then I though perhaps my internet provider is blocking traffic to that port. So I tried accessing it from another remote server. same thing. 

I really don't post that often this is maybe my second post in the past 4 years of running a web server google is a good friend of mine and i just keep hitting the wall with this one. 

Your assistance is appreciated.

below is more debug info if you need it. 

Cheers

Paul

```
root@pserver:/sbin# mysql -u root -p -h webserver.com
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 19719
Server version: 5.0.45-Debian_1ubuntu3.3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show variables;

+---------------------------------+------------------------------+
| Variable_name                   | Value                        |
+---------------------------------+------------------------------+
| auto_increment_increment        | 1                            | 
| auto_increment_offset           | 1                            | 
| automatic_sp_privileges         | ON                           | 
| back_log                        | 50                           | 
| basedir                         | /usr/                        | 
| binlog_cache_size               | 32768                        | 
| bulk_insert_buffer_size         | 8388608                      | 
| character_set_client            | latin1                       | 
| character_set_connection        | latin1                       | 
| character_set_database          | latin1                       | 
| character_set_filesystem        | binary                       | 
| character_set_results           | latin1                       | 
| character_set_server            | latin1                       | 
| character_set_system            | utf8                         | 
| character_sets_dir              | /usr/share/mysql/charsets/   | 
| collation_connection            | latin1_swedish_ci            | 
| collation_database              | latin1_swedish_ci            | 
| collation_server                | latin1_swedish_ci            | 
| completion_type                 | 0                            | 
| concurrent_insert               | 1                            | 
| connect_timeout                 | 5                            | 
| datadir                         | /var/lib/mysql/              | 
| date_format                     | %Y-%m-%d                     | 
| datetime_format                 | %Y-%m-%d %H:%i:%s            | 
| default_week_format             | 0                            | 
| delay_key_write                 | ON                           | 
| delayed_insert_limit            | 100                          | 
| delayed_insert_timeout          | 300                          | 
| delayed_queue_size              | 1000                         | 
| div_precision_increment         | 4                            | 
| engine_condition_pushdown       | OFF                          | 
| expire_logs_days                | 10                           | 
| flush                           | OFF                          | 
| flush_time                      | 0                            | 
| ft_boolean_syntax               | + -><()~*:""&|               | 
| ft_max_word_len                 | 84                           | 
| ft_min_word_len                 | 4                            | 
| ft_query_expansion_limit        | 20                           | 
| ft_stopword_file                | (built-in)                   | 
| group_concat_max_len            | 1024                         | 
| have_archive                    | YES                          | 
| have_bdb                        | NO                           | 
| have_blackhole_engine           | YES                          | 
| have_compress                   | YES                          | 
| have_crypt                      | YES                          | 
| have_csv                        | YES                          | 
| have_dynamic_loading            | YES                          | 
| have_example_engine             | NO                           | 
| have_federated_engine           | YES                          | 
| have_geometry                   | YES                          | 
| have_innodb                     | YES                          | 
| have_isam                       | NO                           | 
| have_merge_engine               | YES                          | 
| have_ndbcluster                 | DISABLED                     | 
| have_openssl                    | DISABLED                     | 
| have_ssl                        | DISABLED                     | 
| have_query_cache                | YES                          | 
| have_raid                       | NO                           | 
| have_rtree_keys                 | YES                          | 
| have_symlink                    | YES                          | 
| hostname                        | servername                   | 
| init_connect                    |                              | 
| init_file                       |                              | 
| init_slave                      |                              | 
| innodb_additional_mem_pool_size | 1048576                      | 
| innodb_autoextend_increment     | 8                            | 
| innodb_buffer_pool_awe_mem_mb   | 0                            | 
| innodb_buffer_pool_size         | 8388608                      | 
| innodb_checksums                | ON                           | 
| innodb_commit_concurrency       | 0                            | 
| innodb_concurrency_tickets      | 500                          | 
| innodb_data_file_path           | ibdata1:10M:autoextend       | 
| innodb_data_home_dir            |                              | 
| innodb_doublewrite              | ON                           | 
| innodb_fast_shutdown            | 1                            | 
| innodb_file_io_threads          | 4                            | 
| innodb_file_per_table           | OFF                          | 
| innodb_flush_log_at_trx_commit  | 1                            | 
| innodb_flush_method             |                              | 
| innodb_force_recovery           | 0                            | 
| innodb_lock_wait_timeout        | 50                           | 
| innodb_locks_unsafe_for_binlog  | OFF                          | 
| innodb_log_arch_dir             |                              | 
| innodb_log_archive              | OFF                          | 
| innodb_log_buffer_size          | 1048576                      | 
| innodb_log_file_size            | 5242880                      | 
| innodb_log_files_in_group       | 2                            | 
| innodb_log_group_home_dir       | ./                           | 
| innodb_max_dirty_pages_pct      | 90                           | 
| innodb_max_purge_lag            | 0                            | 
| innodb_mirrored_log_groups      | 1                            | 
| innodb_open_files               | 300                          | 
| innodb_rollback_on_timeout      | OFF                          | 
| innodb_support_xa               | ON                           | 
| innodb_sync_spin_loops          | 20                           | 
| innodb_table_locks              | ON                           | 
| innodb_thread_concurrency       | 8                            | 
| innodb_thread_sleep_delay       | 10000                        | 
| interactive_timeout             | 28800                        | 
| join_buffer_size                | 131072                       | 
| key_buffer_size                 | 36700160                     | 
| key_cache_age_threshold         | 300                          | 
| key_cache_block_size            | 1024                         | 
| key_cache_division_limit        | 100                          | 
| language                        | /usr/share/mysql/english/    | 
| large_files_support             | ON                           | 
| large_page_size                 | 0                            | 
| large_pages                     | OFF                          | 
| lc_time_names                   | en_US                        | 
| license                         | GPL                          | 
| local_infile                    | ON                           | 
| locked_in_memory                | ON                           | 
| log                             | OFF                          | 
| log_bin                         | ON                           | 
| log_bin_trust_function_creators | OFF                          | 
| log_error                       |                              | 
| log_queries_not_using_indexes   | ON                           | 
| log_slave_updates               | OFF                          | 
| log_slow_queries                | ON                           | 
| log_warnings                    | 1                            | 
| long_query_time                 | 2                            | 
| low_priority_updates            | OFF                          | 
| lower_case_file_system          | OFF                          | 
| lower_case_table_names          | 0                            | 
| max_allowed_packet              | 33553408                     | 
| max_binlog_cache_size           | 4294967295                   | 
| max_binlog_size                 | 104857600                    | 
| max_connect_errors              | 10                           | 
| max_connections                 | 100                          | 
| max_delayed_threads             | 20                           | 
| max_error_count                 | 64                           | 
| max_heap_table_size             | 16777216                     | 
| max_insert_delayed_threads      | 20                           | 
| max_join_size                   | 18446744073709551615         | 
| max_length_for_sort_data        | 1024                         | 
| max_prepared_stmt_count         | 16382                        | 
| max_relay_log_size              | 0                            | 
| max_seeks_for_key               | 4294967295                   | 
| max_sort_length                 | 1024                         | 
| max_sp_recursion_depth          | 0                            | 
| max_tmp_tables                  | 32                           | 
| max_user_connections            | 0                            | 
| max_write_lock_count            | 4294967295                   | 
| multi_range_count               | 256                          | 
| myisam_data_pointer_size        | 6                            | 
| myisam_max_sort_file_size       | 2147483647                   | 
| myisam_recover_options          | OFF                          | 
| myisam_repair_threads           | 1                            | 
| myisam_sort_buffer_size         | 8388608                      | 
| myisam_stats_method             | nulls_unequal                | 
| ndb_autoincrement_prefetch_sz   | 32                           | 
| ndb_force_send                  | ON                           | 
| ndb_use_exact_count             | ON                           | 
| ndb_use_transactions            | ON                           | 
| ndb_cache_check_time            | 0                            | 
| ndb_connectstring               |                              | 
| net_buffer_length               | 16384                        | 
| net_read_timeout                | 30                           | 
| net_retry_count                 | 10                           | 
| net_write_timeout               | 60                           | 
| new                             | OFF                          | 
| old_passwords                   | OFF                          | 
| open_files_limit                | 1024                         | 
| optimizer_prune_level           | 1                            | 
| optimizer_search_depth          | 62                           | 
| pid_file                        | /var/run/mysqld/mysqld.pid   | 
| port                            | 3306                         | 
| preload_buffer_size             | 32768                        | 
| profiling                       | OFF                          | 
| profiling_history_size          | 15                           | 
| protocol_version                | 10                           | 
| query_alloc_block_size          | 8192                         | 
| query_cache_limit               | 268435456                    | 
| query_cache_min_res_unit        | 4194304                      | 
| query_cache_size                | 1073741824                   | 
| query_cache_type                | ON                           | 
| query_cache_wlock_invalidate    | OFF                          | 
| query_prealloc_size             | 8192                         | 
| range_alloc_block_size          | 2048                         | 
| read_buffer_size                | 131072                       | 
| read_only                       | OFF                          | 
| read_rnd_buffer_size            | 262144                       | 
| relay_log_purge                 | ON                           | 
| relay_log_space_limit           | 0                            | 
| rpl_recovery_rank               | 0                            | 
| secure_auth                     | OFF                          | 
| secure_file_priv                |                              | 
| server_id                       | 1                            | 
| skip_external_locking           | ON                           | 
| skip_networking                 | OFF                          | 
| skip_show_database              | OFF                          | 
| slave_compressed_protocol       | OFF                          | 
| slave_load_tmpdir               | /tmp/                        | 
| slave_net_timeout               | 3600                         | 
| slave_skip_errors               | OFF                          | 
| slave_transaction_retries       | 10                           | 
| slow_launch_time                | 2                            | 
| socket                          | /var/run/mysqld/mysqld.sock  | 
| sort_buffer_size                | 2097144                      | 
| sql_big_selects                 | ON                           | 
| sql_mode                        |                              | 
| sql_notes                       | ON                           | 
| sql_warnings                    | OFF                          | 
| ssl_ca                          |                              | 
| ssl_capath                      |                              | 
| ssl_cert                        |                              | 
| ssl_cipher                      |                              | 
| ssl_key                         |                              | 
| storage_engine                  | MyISAM                       | 
| sync_binlog                     | 0                            | 
| sync_frm                        | ON                           | 
| system_time_zone                | EDT                          | 
| table_cache                     | 64                           | 
| table_lock_wait_timeout         | 50                           | 
| table_type                      | MyISAM                       | 
| thread_cache_size               | 8                            | 
| thread_stack                    | 524288                       | 
| time_format                     | %H:%i:%s                     | 
| time_zone                       | SYSTEM                       | 
| timed_mutexes                   | OFF                          | 
| tmp_table_size                  | 33554432                     | 
| tmpdir                          | /tmp                         | 
| transaction_alloc_block_size    | 8192                         | 
| transaction_prealloc_size       | 4096                         | 
| tx_isolation                    | REPEATABLE-READ              | 
| updatable_views_with_limit      | YES                          | 
| version                         | 5.0.45-Debian_1ubuntu3.3-log | 
| version_comment                 | Debian etch distribution     | 
| version_compile_machine         | i486                         | 
| version_compile_os              | pc-linux-gnu                 | 
| wait_timeout                    | 28800                        | 
+---------------------------------+------------------------------+
```

Running processes:
```
root@server:/sbin# ps -uax | grep mysqld
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root      5759  0.0  0.0   1756   532 pts/0    S    23:29   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5796 22.0 35.0 1180596 1178948 pts/0 SLl  23:29   0:01 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5797  0.0  0.0   2892   688 pts/0    S    23:29   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      5867  0.0  0.0   2980   772 pts/0    S+   23:29   0:00 grep mysqld
```


mysql config file:
```

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
port            = 3306
#socket         = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
#socket         = /var/run/mysqld/mysqld.sock
port            = 3306
nice            = 0

#The memory allocated to store results from old queries.
#query_cache_size=256M
#Query cache type to use.
#query_cache_type=1






[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
#skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.

#bind-address           = 127.0.0.1
#bind-address           = 199.246.2.136

#
# * Fine Tuning
#
key_buffer_size=35M
max_allowed_packet      = 32M
thread_stack=512k
thread_cache_size       = 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit=256M
query_cache_size=1024M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log            = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
log_slow_queries        = /var/log/mysql/mysql-slow.log
long_query_time = 2
log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
log_bin                 = /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
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



#Each thread that needs to do a sort allocates a buffer of this size.
#sort_buffer_size=16M


#Block size to be used for MyISAM index pages.
#myisam_block_size=1024
#Used to help MySQL to decide when to use the slow but safe key cache index create method.
#myisam_max_extra_sort_file_size=256M
#Don't use the fast sort index method to created index if the temporary file would get bigger than this.
#myisam_max_sort_file_size=2047M
#Number of threads to use when repairing MyISAM tables.The value of 1 disables parallel repair.
#myisam_repair_threads=1
#The buffer that is allocated when sorting the index when doing a REPAIR or when creating indexes with CREATE INDEX or ALTER TABLE.
#myisam_sort_buffer_size=8192k


#minimal size of unit in wich space for results is allocated (last unit will be trimed after writing all result data
query_cache_min_res_unit=4096k
#Query cache type to use.
query_cache_type=1












#Lock mysqld in memory.(=Don't swap.)
memlock


#Don't cache host names.
skip-host-cache
#Don't resolve hostnames. All hostnames are IP's or 'localhost'.
skip-name-resolve


[mysqldump]
quick
quote-names
max_allowed_packet      = 32M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 32M

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
#
!includedir /etc/mysql/conf.d/


```

---

### Post by pdescham49 on 2008-06-13
Looks like we've bee warnocked. here :(

[http://en.wikipedia.org/wiki/Warnock's_Dilemma]("http://en.wikipedia.org/wiki/Warnock's_Dilemma")

Can anyone please assist? or is this an issue no one has the knowledge to resolve?

---

### Post by pdescham49 on 2008-06-13
Here's a solution for all you helpfull users.

I changed mysql to run under another port and presto. she's working

Somewhere between the server and the client 3306 was being blocked.

---

### Post by mdelaossa on 2011-01-17
Guys, the bind-address is the address you want mysql to listen in on... which means it should be the server's IP address.

So if the machine that mysql is running on has an IP 10.0.2.21 then your bind-address would be set to 10.0.2.21.

You also need to make sure the mysql server accepts logins from the IP you're coming from. For example let's say you want to connect to the database 'db' using username 'dbuser' with password 'dbpass' and you're coming from ip 10.0.2.112. You would get into the mysql prompt and issue the command 

GRANT USAGE ON db.* TO dbuser@10.0.2.112 IDENTIFIED BY 'dbpass'

If you want access from ANY IP, the command turns into

GRANT USAGE ON db.* TO dbuser IDENTIFIED BY 'dbpass'

Source: [http://www.debianhelp.co.uk/remotemysql.htm](http://www.debianhelp.co.uk/remotemysql.htm) (not all the info is there btw)

---

### Post by ZenMasta on 2011-01-21
The problem for me was that I did not use the identified by statement. I just assumed that because the user already existed the password it already had would work. So even though a the same username may exist with a working password, you still have to assign a password (the same or different) for the user you grant @ whatever host.

So, cliff notes: 
backup your my.cnf 
edit your my.cnf file and comment out
change this:bind-address=127.0.0.1 
to this:    #bind-address=127.0.0.1
service mysql restart
Then
grant all on yourdb.* to 'youruser'@'youripaddress' identified by 'secretpassword';

Connect remotely using your client of choice,  bingo!

---

