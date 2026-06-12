---
title: "mysql direct connector no more working"
date: 2020-08-20
forum: Installation &amp; Upgrades
---

### Post by jduns on 2020-08-20
After upgrading to (k)ubuntu 20.04, both with LibreOffice 6.4. and LibreOffice 7, mysql direct connector doesn't work any more (unlike in (k)ubuntu 18.04 and LO 6.0). 
Mysql (mariadb, installed with lampp) is perfectly working in browsers: I can see php+mysql pages in localhost, without any problem.

But if I try to open a database odb connected with mysql I get an error message
```
SQL Status: HY000
Error code: 2003
Can't connect to MySQL server on 'localhost' (111) /build/libreoffice-ron9it/libreoffice-7.0.0~rc3/connectivity/source/drivers/mysqlc/mysqlc_general.cxx:119

```

I believe that is a problem of mysql-connector provided with Ubuntu, in the past so useful (because LO extension are not working).

Thanks

---

### Post by dino99 on 2020-08-20
Glance at log(s) about possible missing symlink(s)

---

### Post by jduns on 2020-08-20
Uhm, could you explain me what logs I should watch? In /opt/lampp? In /home?
Thank you!

---

### Post by vidtek on 2020-08-20
> **jduns said:**
> Uhm, could you explain me what logs I should watch? In /opt/lampp? In /home?
Thank you!

/var/log/mysql

or

/var/log/mariadb

Tony

---

### Post by jduns on 2020-08-21
Uhm... I have lampp.
So in /opt/lampp/logs I have error_log, and today these lines:
```
[Fri Aug 21 09:22:04.653134 2020] [ssl:warn] [pid 3153] AH01906: localhost:443:0 server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Fri Aug 21 09:22:04.654129 2020] [ssl:warn] [pid 3153] AH01909: localhost:443:0 server certificate does NOT include an ID which matches the server name
[Fri Aug 21 09:22:04.654267 2020] [suexec:notice] [pid 3153] AH01232: suEXEC mechanism enabled (wrapper: /opt/lampp/bin/suexec)
[Fri Aug 21 09:22:04.692763 2020] [ssl:warn] [pid 3158] AH01906: localhost:443:0 server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Fri Aug 21 09:22:04.692784 2020] [ssl:warn] [pid 3158] AH01909: localhost:443:0 server certificate does NOT include an ID which matches the server name
[Fri Aug 21 09:22:04.692957 2020] [lbmethod_heartbeat:notice] [pid 3158] AH02282: No slotmem from mod_heartmonitor
[Fri Aug 21 09:22:04.924808 2020] [mpm_prefork:notice] [pid 3158] AH00163: Apache/2.4.43 (Unix) OpenSSL/1.1.1g PHP/7.4.8 mod_perl/2.0.11 Perl/v5.32.0 configured -- resuming normal operations
[Fri Aug 21 09:22:04.924846 2020] [core:notice] [pid 3158] AH00094: Command line: '/opt/lampp/bin/httpd -E /opt/lampp/logs/error_log -D SSL -D PHP'
```

in /var/log I have auth.log with these lines today
```
Aug 21 10:06:21 duns-newneon-sir kcheckpass[6084]: pam_unix(kde:auth): Couldn't open /etc/securetty: No such file or directory
Aug 21 10:06:21 duns-newneon-sir kcheckpass[6185]: pam_unix(kde:auth): Couldn't open /etc/securetty: No such file or directory
Aug 21 10:06:21 duns-newneon-sir kcheckpass[6186]: pam_unix(kde:auth): Couldn't open /etc/securetty: No such file or directory
```

in /opt/lampp/var/mysql I have log files with an hour of last modification before I tried to open an odb file, but any way I report [my-pc-name].err of today
```

2020-08-21  9:22:05 0 [Warning] WSREP: Failed to guess base node address. Set it explicitly via wsrep_node_address.
2020-08-21  9:22:05 0 [Warning] WSREP: Failed to guess base node address. Set it explicitly via wsrep_node_address.
2020-08-21  9:22:05 0 [Warning] WSREP: Guessing address for incoming client connections failed. Try setting wsrep_node_incoming_address explicitly.
2020-08-21  9:22:05 0 [Note] WSREP: Node addr: 
2020-08-21  9:22:05 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2020-08-21  9:22:05 0 [Note] InnoDB: Uses event mutexes
2020-08-21  9:22:05 0 [Note] InnoDB: Compressed tables use zlib 1.2.11
2020-08-21  9:22:05 0 [Note] InnoDB: Number of pools: 1
2020-08-21  9:22:05 0 [Note] InnoDB: Using SSE2 crc32 instructions
2020-08-21  9:22:05 0 [Note] InnoDB: Initializing buffer pool, total size = 16M, instances = 1, chunk size = 16M
2020-08-21  9:22:05 0 [Note] InnoDB: Completed initialization of buffer pool
2020-08-21  9:22:05 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2020-08-21  9:22:05 0 [Note] InnoDB: 128 out of 128 rollback segments are active.
2020-08-21  9:22:05 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2020-08-21  9:22:05 0 [Note] InnoDB: Setting file '/opt/lampp/var/mysql/ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2020-08-21  9:22:05 0 [Note] InnoDB: File '/opt/lampp/var/mysql/ibtmp1' size is now 12 MB.
2020-08-21  9:22:05 0 [Note] InnoDB: Waiting for purge to start
2020-08-21  9:22:05 0 [Note] InnoDB: 10.4.13 started; log sequence number 1800617; transaction id 2753
2020-08-21  9:22:05 0 [Note] Plugin 'FEEDBACK' is disabled.
2020-08-21  9:22:05 0 [Note] InnoDB: Loading buffer pool(s) from /opt/lampp/var/mysql/ib_buffer_pool
2020-08-21  9:22:05 0 [ERROR] Incorrect definition of table mysql.event: expected column 'sql_mode' at position 14 to have type set('REAL_AS_FLOAT','PIPES_AS_CONCAT','ANSI_QUOTES','IGNORE_SPACE','IGNORE_BAD_TABLE_OPTIONS','ONLY_FULL_GROUP_BY','NO_UNSIGNED_SUBTRACTION','NO_DIR_IN_CREATE','POSTGRESQL','ORACLE','MSSQL','DB2','MAXDB','NO_KEY_OPTIONS','NO_TABLE_OPTIONS','NO_FIELD_OPTIONS','MYSQL323','MYSQL40','ANSI','NO_AUTO_VALUE_ON_ZERO','NO_BACKSLASH_ESCAPES','STRICT_TRANS_TABLES','STRICT_ALL_TABLES','NO_ZERO_IN_DATE','NO_ZERO_DATE','INVALID_DATES','ERROR_FOR_DIVISION_BY_ZERO','TRADITIONAL','NO_AUTO_CREATE_USER','HIGH_NOT_PRECEDENCE','NO_ENGINE_SUBSTITUTION','PAD_CHAR_TO_FULL_LENGTH','EMPTY_STRING_IS_NULL','SIMULTANEOUS_ASSIGNMENT'), found type set('REAL_AS_FLOAT','PIPES_AS_CONCAT','ANSI_QUOTES','IGNORE_SPACE','IGNORE_BAD_TABLE_OPTIONS','ONLY_FULL_GROUP_BY','NO_UNSIGNED_SUBTRACTION','NO_DIR_IN_CREATE','POSTGRESQL','ORACLE','MSSQL','DB2','MAXDB','NO_KEY_OPTIONS','NO_TABLE_OPTIONS','NO_FIELD_OPTIONS','MYSQL323','MYSQL40','ANSI','NO_AUTO_V...
2020-08-21  9:22:05 0 [ERROR] mysqld: Event Scheduler: An error occurred when initializing system tables. Disabling the Event Scheduler.
2020-08-21  9:22:05 6 [Warning] InnoDB: Table mysql/innodb_table_stats has length mismatch in the column name table_name.  Please run mysql_upgrade
2020-08-21  9:22:05 6 [Warning] InnoDB: Table mysql/innodb_index_stats has length mismatch in the column name table_name.  Please run mysql_upgrade
2020-08-21  9:22:05 0 [Note] Reading of all Master_info entries succeeded
2020-08-21  9:22:05 0 [Note] Added new Master_info '' to hash table
2020-08-21  9:22:05 0 [Note] /opt/lampp/sbin/mysqld: ready for connections.
Version: '10.4.13-MariaDB'  socket: '/opt/lampp/var/mysql/mysql.sock'  port: 0  Source distribution
2020-08-21  9:22:05 0 [Note] InnoDB: Buffer pool(s) load completed at 200821  9:22:05
```

Note that my tables are myisam, not innodb.

Thank you for the help you give me.

---

### Post by jduns on 2020-08-22
Let me ask a question: there is somebody who is able to get mysql direct connection after upgrading to 20.04?
Otherwise I will open a bug report.

EDIT

Due to the fact that nobody answered, I will report a bug.

---

