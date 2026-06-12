---
title: "MySQL Startup Failing/Hanging in 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Thomas Gutzmann on 2010-05-07
Hi,

After upgrading to Ubuntu 10.04, MySQL wouldn't start up again. Several solutions had been discussed in this forum, but none of them would fit in my situation. I finally found a way which I want to outline here.

Symptom: "start mysql" or "service mysql start" (as root) hangs.

Reason: In /etc/init/mysql.conf, there is an infinite loop in the post-start script due to an incomplete migration of MySQL.

Fix: Create an additional user in the schema "mysql".

Steps:

1. Look at /etc/mysql/debian.cnf. Extract the cryptic, bun unencrypted password for user "debian-sys-maint".
2. Start mysql using "/usr/sbin/mysqld" (as root).
3. Log in as mysql (or "su - mysql").
4. Connect to mysql as root: "mysql -u root --password=XXXX".
5. Create the user "debian-sys-maint", using the password retrieved in step 1: "create user 'debian-sys-maint' identified by 'btIgH81mUXcfZdCQ';".
6. Get the pid of mysqld: "ps ax | grep -i mysqld". Example: "3024 ? Ssl 0:00 /usr/sbin/mysqld"
7. Kill this process: "kill -5 3024".
8. Start mysql (as root): "start mysql". Eventually you see an error message that mysql is already running; this can happen if you tried the command before and cancelled it with control-c. In this case, enter "stop mysql" and "start mysql".
9. Reboot to see if MySQL starts up automatically.
10. If the automatic startup still fails, you may follow the advice from a different thread: change the start condition in /etc/init/mysql.conf to "start on (net-device-up IFACE=ethX)", where "X" is the interface you have mysql bound to, e.g. ETH1.
11. In my case, I had another very specific problem: I'm running Ubuntu in a VM with several virtual disks which were not mounted yet when the network was up. Quite tricky to figure out. So I modified the start condition to "start on (net-device-up IFACE=eth1 and stopped mountall)", and now everything is fine.

Det var det det! :-)

Cheers,

Thomas

---

### Post by atmorell on 2010-05-07
Good work / godt arbejde ;)

---

### Post by Jordan Rusev on 2010-05-09
Hello,
I have the same problem in 10.04. I try to follow this steps, but when I start /usr/sbin/mysqld as root, it failed with messages:

100509 14:36:53 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!

100509 14:36:53 [ERROR] Aborting

100509 14:36:53 [Note] /usr/sbin/mysqld: Shutdown complete

and it's impossible to finish your instructions and start MySQL.

---

### Post by Thomas Gutzmann on 2010-05-15
Hi Jordan,

Please have a look at [http://dev.mysql.com/doc/mysql-security-excerpt/5.1/en/security-against-attack.html](http://dev.mysql.com/doc/mysql-security-excerpt/5.1/en/security-against-attack.html).

My guess is that in your /etc/mysql/my.cnf in section [mysqld] you have 

user = root

Change this to

user = mysql

If you have still problems, give me your my.cnf. You should also capture the messages in /var/log/messages while you run "start mysql" or "/usr/sbin/mysql" and include it, too.

Cheers,

Thomas

---

### Post by blaze042 on 2010-06-03
That's some great detective work there.

That fixed the hangs when trying to start/stop the service. And it fixed the "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)" message whenever I tried running mysql.

And Webmin is able to administer the database. Thanks!

---

### Post by fishgoat on 2010-06-17
Hello,

I had the same problem: infinite loop in "post-start script" in /etc/init/mysql.conf
Reason was a incorrect path to the socket in /etc/mysql/debian.cnf (there are two lines "socket = ..."!)
After correctiing the pathes everything worked fine.

---

### Post by j0nny on 2010-06-30
thanks for the post - fixed my issue. Step 10 was required (IFACE=eth2) before mysql would restart automatically or complete the upgrade.

---

### Post by crowdofone on 2011-08-19
Thomas,

Just came across this problem now on a server running 10.04 and your instructions have proved invaluable. 

Many thanks!

---

### Post by Hanine on 2012-03-13
for those having the problem in Ubuntu 11.10 and 12.04: do this :

sudo    **sudo dpkg-reconfigure mysql-server-5.X**

where X is the version of your installed Mysql.

Follow instructions and reboot.

MySQL Config mess can sometimes happen during version upgrade.

---

### Post by Shadow aok on 2012-03-25
Hello,

I have an issue due to a migration from a mysql 5.1.48 (OpenSolaris AMD64) to mysql 5.1.61 (Ubuntu 10.04 AMD64).

I transfered all my /var/lib/mysql folder and my my.ini (paths have been updated).
User debian-sys-maint have been created.

When i'm trying to start mysql, the init script get in a loop and i have these errors :
```
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27370]: Upgrading MySQL tables if necessary.
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27374]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27374]: Looking for 'mysql' as: /usr/bin/mysql
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27374]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27374]: This installation of MySQL is already upgraded to 5.1.61, use --force if you still need to run mysql_upgrade
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27382]: Checking for insecure root accounts.
Mar 25 23:32:57 ns309510 /etc/mysql/debian-start[27386]: Triggering myisam-recover for all MyISAM tables
Mar 25 23:32:57 ns309510 init: mysql main process (27393) terminated with status 1
Mar 25 23:32:57 ns309510 init: mysql main process ended, respawning
```

If i'm manually starting mysql using this command line, it works just fine :
sudo mysqld --user=mysql &

I read all the posts above but nothing solved my issue.

Thanks for your help.

---

### Post by Shadow aok on 2012-03-25
And if i'm running dpkg-reconfigure, I got this (the column which fails to be added already exists in my mysql.user table) :
(ns309510-bin.000093 does not exist, last file is 000091)
```
120325 23:41:59  InnoDB: Completed initialization of buffer pool
120325 23:41:59  InnoDB: Started; log sequence number 0 32783287
/usr/sbin/mysqld: File './ns309510-bin.000093' not found (Errcode: 13)
120325 23:41:59 [ERROR] Failed to open log (file './ns309510-bin.000093', errno 13)
120325 23:41:59 [ERROR] Could not open log file
120325 23:41:59 [ERROR] Can't init tc log
120325 23:41:59 [ERROR] Aborting

120325 23:41:59  InnoDB: Starting shutdown...

==> syslog <==
Mar 25 23:42:01 ns309510 CRON[27839]: (root) CMD (/usr/local/rtm/bin/rtm 50 > /dev/null 2> /dev/null)

==> /var/log/mysql/error.log <==
120325 23:42:04  InnoDB: Shutdown completed; log sequence number 0 32783287
120325 23:42:04 [Note] /usr/sbin/mysqld: Shutdown complete

120325 23:42:04  InnoDB: Initializing buffer pool, size = 8.0M
120325 23:42:04  InnoDB: Completed initialization of buffer pool
120325 23:42:04  InnoDB: Started; log sequence number 0 32783287
ERROR: 1064  You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ALTER TABLE user ADD column Show_view_priv enum('N','Y') CHARACTER SET utf8 NOT ' at line 1
120325 23:42:04 [ERROR] Aborting

120325 23:42:04  InnoDB: Starting shutdown...
120325 23:42:09  InnoDB: Shutdown completed; log sequence number 0 32783287
120325 23:42:09 [Note] /usr/sbin/mysqld: Shutdown complete

120325 23:42:09  InnoDB: Initializing buffer pool, size = 8.0M
120325 23:42:09  InnoDB: Completed initialization of buffer pool
120325 23:42:09  InnoDB: Started; log sequence number 0 32783287
120325 23:42:09  InnoDB: Starting shutdown...
120325 23:42:14  InnoDB: Shutdown completed; log sequence number 0 32783287
120325 23:42:15  InnoDB: Initializing buffer pool, size = 8.0M
120325 23:42:15  InnoDB: Completed initialization of buffer pool
120325 23:42:15  InnoDB: Started; log sequence number 0 32783287
ERROR: 1050  Table 'plugin' already exists
120325 23:42:15 [ERROR] Aborting

120325 23:42:15  InnoDB: Starting shutdown...
120325 23:42:20  InnoDB: Shutdown completed; log sequence number 0 32783287
120325 23:42:20 [Note] /usr/sbin/mysqld: Shutdown complete

```

---

### Post by lavajumper on 2012-06-25
I had this problem also. The fix listed here worked, but one extra step I had to take was to run:

```
chown -R mysql.mysql /var/lib/mysql
```

Starting the daemon as root created a bunch of files, owned by root, that could not be accessed when restarted as a daemon running as mysql.

I also had to copy a "my.cnf" from one of the choices in "/usr/share/doc/mysql-server-5.1/examples" to /etc/mysql/my.cnf. These also needed editing to get rid of some "unknown variable" errors.

---

### Post by arizonanoob on 2012-08-13
> **Thomas Gutzmann said:**
> Hi,

After upgrading to Ubuntu 10.04, MySQL wouldn't start up again. Several solutions had been discussed in this forum, but none of them would fit in my situation. I finally found a way which I want to outline here.

Symptom: "start mysql" or "service mysql start" (as root) hangs.

Reason: In /etc/init/mysql.conf, there is an infinite loop in the post-start script due to an incomplete migration of MySQL.

Fix: Create an additional user in the schema "mysql".

Steps:

1. Look at /etc/mysql/debian.cnf. Extract the cryptic, bun unencrypted password for user "debian-sys-maint".
2. Start mysql using "/usr/sbin/mysqld" (as root).
3. Log in as mysql (or "su - mysql").
4. Connect to mysql as root: "mysql -u root --password=XXXX".
5. Create the user "debian-sys-maint", using the password retrieved in step 1: "create user 'debian-sys-maint' identified by 'btIgH81mUXcfZdCQ';".
6. Get the pid of mysqld: "ps ax | grep -i mysqld". Example: "3024 ? Ssl 0:00 /usr/sbin/mysqld"
7. Kill this process: "kill -5 3024".
8. Start mysql (as root): "start mysql". Eventually you see an error message that mysql is already running; this can happen if you tried the command before and cancelled it with control-c. In this case, enter "stop mysql" and "start mysql".
9. Reboot to see if MySQL starts up automatically.
10. If the automatic startup still fails, you may follow the advice from a different thread: change the start condition in /etc/init/mysql.conf to "start on (net-device-up IFACE=ethX)", where "X" is the interface you have mysql bound to, e.g. ETH1.
11. In my case, I had another very specific problem: I'm running Ubuntu in a VM with several virtual disks which were not mounted yet when the network was up. Quite tricky to figure out. So I modified the start condition to "start on (net-device-up IFACE=eth1 and stopped mountall)", and now everything is fine.

Det var det det! :-)

Cheers,

Thomas

This could very well be a fix, however, I am not allowed to edit debian.cnf as it is owned by root. Any ideas on how to get around that?

EDIT: nevermind - figured it out via 
sudo gedit debian.cnf

---

