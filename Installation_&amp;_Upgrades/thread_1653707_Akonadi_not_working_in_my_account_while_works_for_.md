---
title: "Akonadi not working in my account while works for others"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by mhdbnoimi on 2010-12-27
Hi All,

I get error message whenever I run Kontact told me that Akonadi not working well because **it's not registered at D-Bus** in addition to **No resource agent found** while these error messages not appear at all for other users!!!

So I tried to fix this issue by deleting ~/.local/share/akonadi but it didn't fix the issue!

[color=#FF0000]**How I can reset Akonadi to default values for fixing error messages?**[/color]

---Error screenshot
[[img]http://i.imgur.com/Uy5oJs.jpg[/img]](http://i.imgur.com/Uy5oJ.png)
---Error log
```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/data/.config/akonadi/akonadiserverrc':
[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/data/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true


Test 2:  SUCCESS
--------

Akonadi is not running as root
Details: Akonadi is not running as a root/administrator user, which is the recommended setup for a secure system.

Test 3:  SUCCESS
--------

MySQL server found.
Details: You have currently configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld'; its location varies depending on the distribution.

Test 4:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.1.48-1ubuntu4 for debian-linux-gnu on x86_64 ((Ubuntu))


Test 5:  SUCCESS
--------

No current MySQL error log found.
Details: The MySQL server did not report any errors during this startup. The log can be found in '/data/.local/share/akonadi/db_data/mysql.err'.

Test 6:  SUCCESS
--------

MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href='/etc/akonadi/mysql-global.conf'>/etc/akonadi/mysql-global.conf</a>.

File content of '/etc/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=utf8
collation_server=utf8_general_ci
table_cache=200
thread_cache_size=3
#log_bin=mysql-bin
#expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2

# Do not drop the connection to the DB after 8 hours of inactivity
wait_timeout=1296000

[client]
default-character-set=utf8


Test 7:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 8:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/data/.local/share/akonadi/mysql.conf'>/data/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/data/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=utf8
collation_server=utf8_general_ci
table_cache=200
thread_cache_size=3
#log_bin=mysql-bin
#expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2

# Do not drop the connection to the DB after 8 hours of inactivity
wait_timeout=1296000

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.4.0


Test 10:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 12:  SUCCESS
--------

Nepomuk search service registered at D-Bus.
Details: The Nepomuk search service is registered at D-Bus which typically indicates it is operational.

Test 13:  SUCCESS
--------

Nepomuk search service uses an appropriate backend. 
Details: The Nepomuk search service uses one of the recommended backends.

Test 14:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 15:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share'; make sure this includes all paths where Akonadi agents are installed.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 16:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href='/data/.local/share/akonadi/akonadiserver.error'>/data/.local/share/akonadi/akonadiserver.error</a>.

File content of '/data/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/data/.local/share/akonadi//mysql.conf", "--datadir", "/data/.local/share/akonadi/db_data/", "--socket=/data/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /data/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
101226  5:32:17 [Warning] Can't create test file /data/.local/share/akonadi/db_data/admino-mbnoimi.lower-test
101226  5:32:17 [Warning] Can't create test file /data/.local/share/akonadi/db_data/admino-mbnoimi.lower-test
101226  5:32:17 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
101226  5:32:17 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101226  5:32:17  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40af99]
1: akonadiserver() [0x40b4ea]
2: /lib/libc.so.6(+0x33c20) [0x7f391ca56c20]
3: /lib/libc.so.6(gsignal+0x35) [0x7f391ca56ba5]
4: /lib/libc.so.6(abort+0x180) [0x7f391ca5a6b0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f391dc39864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c5d8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f391dccb4a7]
8: /usr/lib/libQtCore.so.4(+0x10ba59) [0x7f391dcd8a59]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f391dcd9c69]
10: akonadiserver(_ZN6QDebugD1Ev+0x49) [0x4068f9]
11: /usr/lib/libakonadiprivate.so.1(_ZN13DbConfigMysql19startInternalServerEv+0x19ad) [0x7f391e15b6ad]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xdd) [0x7f391e0c58cd]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xd7) [0x7f391e0c77e7]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f391e0c91ea]
15: akonadiserver(main+0x404) [0x405df4]
16: /lib/libc.so.6(__libc_start_main+0xfe) [0x7f391ca41d8e]
17: akonadiserver() [0x4058f9]
]
" 


Test 17:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href='/data/.local/share/akonadi/akonadiserver.error.old'>/data/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/data/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/data/.local/share/akonadi//mysql.conf", "--datadir", "/data/.local/share/akonadi/db_data/", "--socket=/data/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /data/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
101226  5:32:17 [Warning] Can't create test file /data/.local/share/akonadi/db_data/admino-mbnoimi.lower-test
101226  5:32:17 [Warning] Can't create test file /data/.local/share/akonadi/db_data/admino-mbnoimi.lower-test
101226  5:32:17 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
101226  5:32:17 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101226  5:32:17  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40af99]
1: akonadiserver() [0x40b4ea]
2: /lib/libc.so.6(+0x33c20) [0x7f9d8ec3cc20]
3: /lib/libc.so.6(gsignal+0x35) [0x7f9d8ec3cba5]
4: /lib/libc.so.6(abort+0x180) [0x7f9d8ec406b0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f9d8fe1f864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c5d8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f9d8feb14a7]
8: /usr/lib/libQtCore.so.4(+0x10ba59) [0x7f9d8febea59]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f9d8febfc69]
10: akonadiserver(_ZN6QDebugD1Ev+0x49) [0x4068f9]
11: /usr/lib/libakonadiprivate.so.1(_ZN13DbConfigMysql19startInternalServerEv+0x19ad) [0x7f9d903416ad]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xdd) [0x7f9d902ab8cd]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xd7) [0x7f9d902ad7e7]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f9d902af1ea]
15: akonadiserver(main+0x404) [0x405df4]
16: /lib/libc.so.6(__libc_start_main+0xfe) [0x7f9d8ec27d8e]
17: akonadiserver() [0x4058f9]
]
" 


Test 18:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 19:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


```

---Start-up log
```
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/data/.local/share/akonadi//mysql.conf", "--datadir", "/data/.local/share/akonadi/db_data/", "--socket=/data/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /data/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
101226  7:50:27 [Warning] Can't create test file /data/.local/share/akonadi/db_data/admino-mbnoimi.lower-test
101226  7:50:27 [Warning] Can't create test file /data/.local/share/akonadi/db_data/admino-mbnoimi.lower-test
101226  7:50:27 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
101226  7:50:27 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101226  7:50:27  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40af99]
1: akonadiserver() [0x40b4ea]
2: /lib/libc.so.6(+0x33c20) [0x7f4d8fea2c20]
3: /lib/libc.so.6(gsignal+0x35) [0x7f4d8fea2ba5]
4: /lib/libc.so.6(abort+0x180) [0x7f4d8fea66b0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f4d91085864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c5d8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f4d911174a7]
8: /usr/lib/libQtCore.so.4(+0x10ba59) [0x7f4d91124a59]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f4d91125c69]
10: akonadiserver(_ZN6QDebugD1Ev+0x49) [0x4068f9]
11: /usr/lib/libakonadiprivate.so.1(_ZN13DbConfigMysql19startInternalServerEv+0x19ad) [0x7f4d915a76ad]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xdd) [0x7f4d915118cd]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xd7) [0x7f4d915137e7]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f4d915151ea]
15: akonadiserver(main+0x404) [0x405df4]
16: /lib/libc.so.6(__libc_start_main+0xfe) [0x7f4d8fe8dd8e]
17: akonadiserver() [0x4058f9]
]
" 

```

Note:
After installing (k)ubuntu I created a new user with encrypted home directory in /data instead of /home/new_user because I've two partitions in my hard disk and /data is the mount point of second partition.

Here's the procedure I've did to create a new user:
System Settings->User Management->New User
[[img]http://i.imgur.com/V0xbLs.jpg[/img]](http://i.imgur.com/V0xbL.png)
[[img]http://i.imgur.com/06KpZs.jpg[/img]](http://i.imgur.com/06KpZ.png)[LIST=1]
[/LIST]

---

### Post by mhdbnoimi on 2010-12-31
Any suggest guys

---

### Post by mhdbnoimi on 2011-01-02
I found a partial solution at:
[http://forum.kde.org/viewtopic.php?f=20&t=92216](http://forum.kde.org/viewtopic.php?f=20&t=92216)

Could you plz find some time to help me?

---

