---
title: "mysql installation problem"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by hughh on 2008-01-12
Lately whenever I run the Update Manager, I get the following error messages:

```
E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured
```The console window shows the following:

```
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.45-1unbuntu3.1) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysqld, action 'start' failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
```Running 'sudo apt-get -f install' gives the same results.

Here are the last few entries in /var/log/syslog:

```
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER ![/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: To do so, start the server, then issue the following commands:[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: /usr/bin/mysqladmin -u root password 'new-password'[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: /usr/bin/mysqladmin -u root -h Ubuntu password 'new-password'[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: See the manual for more instructions.[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: Please report any problems with the /usr/bin/mysqlbug script![/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: [/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: The latest information about MySQL is available on the web at[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: http://www.mysql.com[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25493]: Support MySQL by buying support/licenses at http://shop.mysql.com[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25550]: ERROR: 1046  No database selected[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25550]: 080112 11:24:38 [ERROR] Aborting[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25550]: [/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25550]: 080112 11:24:38 [Note] /usr/sbin/mysqld: Shutdown complete[/FONT]
[FONT=Courier New]Jan 12 11:24:38 Ubuntu mysqld_safe[25550]: [/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld_safe[25642]: started[/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld[25645]: 080112 11:24:39 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address[/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld[25645]: 080112 11:24:39 [ERROR] Do you already have another mysqld server running on port: 3306 ?[/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld[25645]: 080112 11:24:39 [ERROR] Aborting[/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld[25645]: [/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld[25645]: 080112 11:24:39 [Note] /usr/sbin/mysqld: Shutdown complete[/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld[25645]: [/FONT]
[FONT=Courier New]Jan 12 11:24:39 Ubuntu mysqld_safe[25647]: ended[/FONT]
[FONT=Courier New]Jan 12 11:24:53 Ubuntu /etc/init.d/mysql[25791]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in[/FONT]
[FONT=Courier New]Jan 12 11:24:53 Ubuntu /etc/init.d/mysql[25791]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed[/FONT]
[FONT=Courier New]Jan 12 11:24:53 Ubuntu /etc/init.d/mysql[25791]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'[/FONT]
[FONT=Courier New]Jan 12 11:24:53 Ubuntu /etc/init.d/mysql[25791]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/FONT]
[FONT=Courier New]Jan 12 11:24:53 Ubuntu /etc/init.d/mysql[25791]:[/FONT]
```'mysqld' is NOT running and the directory '/var/run/mysqld' exists, but it's empty.  Any suggestions or help would be much appreciated!

---

### Post by Robster2 on 2008-01-12
Have you added a mysql user and group?

useradd mysql -g mysql
groupadd mysql


Ownership of mysql directories has to be mysql

/var/lib/mysql is where the files exist.

rob@rob-desktop:/var/lib$ ls -l mys*
mysql:
total 20528
-rw-r--r-- 1 mysql mysql        0 2008-01-10 22:13 debian-5.0.flag
-rw-rw---- 1 mysql mysql 10485760 2008-01-12 23:49 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2008-01-13 03:37 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2008-01-10 22:13 ib_logfile1
drwxr-xr-x 2 mysql mysql     4096 2008-01-11 00:12 mysql
-rw------- 1 mysql mysql        6 2008-01-11 00:12 mysql_upgrade_info

sudo -s
chown -R mysql /var/lib/mysql

---

### Post by hughh on 2008-01-12
mysql user and group already exist.

---

### Post by Robster2 on 2008-01-12
Please post the output from. 

ls -l /var/lib/mys*

---

### Post by hughh on 2008-01-12
```

/var/lib/mysql:
total 4
-rw-r--r-- 1 mysql root    0 2008-01-12 11:24 debian-5.0.flag
drwxr-xr-x 2 mysql root 4096 2008-01-12 11:24 mysql

/var/lib/mysql-cluster:
total 0

```

---

### Post by Robster2 on 2008-01-12
Ah HA 

There is your problem ! The group needs to be mysql

# chgrp -R mysql /var/lib/mysql


Have you run mysql_install_db?

---

### Post by hughh on 2008-01-14
>  There is your problem ! The group needs to be mysql

# chgrp -R mysql /var/lib/mysql

OK, I changed the group to mysql but I still get the same errors running 'sudo apt-get -f install'.

> Have you run mysql_install_db?

No.  Do I need to?

---

### Post by Robster2 on 2008-01-16
OK Repeat the install  (I am including the commands for anyone reading this later):

sudo apt-get install mysql-server

become the root:

 sudo -s

run the install script:

mysql_install_db

start the MySQL server using the mysqld_safe script (as the root):


mysqld_safe --user=mysql &

you should get 
[2] 6978
[1]   Exit 127                usr/local/mysql/bin/mysql_safe --user=mysql
root@rob-desktop:~# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7015]: started

test that every thing works log into mysql:

mysql -u root -p

now exit restart the machine and log into mysql again:

---

### Post by Tobberoth on 2008-01-17
I have the same problem as the creator of the topic, but the solution did not work for me. Insted of:

[2] 6978
[1] Exit 127 usr/local/mysql/bin/mysql_safe --user=mysql
root@rob-desktop:~# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7015]: started

I get:

[2] 12904
[1]   Exit 127                myseld_safe --user=mysql
root@TobbeLinux:~# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[12941]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[12954]: ended

After that, logging into the mysql server obviously doesn't work.

---

### Post by Robster2 on 2008-01-24
Please post the output from. 

ls -l /var/lib/mys*

---

### Post by Tobberoth on 2008-01-24
Nevermind, I got it working. The problem was that i had, for some reason, deleted all the loopback info  in /etc/network/interfaces , so I couldn't even ping localhost.

---

### Post by cozmicharlie on 2008-01-24
I am having the same problem.  I followed your instructions and when I restart the computer and try and start mysql I get the following message:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

the output from ls -l /var/lib/mys* is
/var/lib/mysql:
total 20528
-rw-r--r-- 1 mysql mysql        0 2008-01-24 10:40 debian-5.0.flag
-rw-rw---- 1 mysql mysql 10485760 2008-01-24 10:46 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2008-01-24 10:46 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2007-11-02 15:49 ib_logfile1
drwxr-xr-x 2 mysql mysql     4096 2008-01-24 10:40 mysql
-rw------- 1 mysql mysql        6 2007-11-02 15:49 mysql_upgrade_info

/var/lib/mysql-cluster:
total 0

Thanks for your help

---

### Post by spitbox63 on 2008-01-28
> **Robster2 said:**
> OK Repeat the install  (I am including the commands for anyone reading this later):

sudo apt-get install mysql-server

become the root:

 sudo -s

run the install script:

mysql_install_db

start the MySQL server using the mysqld_safe script (as the root):


mysqld_safe --user=mysql &

you should get 
[2] 6978
[1]   Exit 127                usr/local/mysql/bin/mysql_safe --user=mysql
root@rob-desktop:~# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7015]: started

test that every thing works log into mysql:

mysql -u root -p

now exit restart the machine and log into mysql again:

Hi. I've also had this problem. It occurred after I had a system crash. All symptoms appeared as above but when I came to follow the re-install, as above when I entered the mysql_install_db command, I got the following: -

Installing MySQL system tables...
ERROR: 1136  Column count doesn't match value count at row 1
080128 22:09:45 [ERROR] Aborting

080128 22:09:45 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!

Examine the logs in /var/lib/mysql for more information.
You can try to start the mysqld daemon with:
/usr/sbin/mysqld --skip-grant &
and use the command line tool
/usr/bin/mysql to connect to the mysql
database and look at the grant tables:

I'm not too hot on this stuff, as I'm only just learning PHP and using Mysql. Can anyone help please as I'm half way through a project.

Thanks!!!!

---

### Post by ziopippo on 2008-01-29
Same problem of cozmicharlie :( Nobody have more solutions?

---

### Post by hughh on 2008-01-30
I ran these commands, but it still doesn't seem to be working:

> **hugh@Ubuntu:~$ sudo apt-get install mysql-server**
[sudo] password for hugh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
** hugh@Ubuntu:~$ sudo -s**
** root@Ubuntu:~# mysql_install_db**
Installing MySQL system tables...
OK
Filling help tables...
OK

To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h Ubuntu password 'new-password'
See the manual for more instructions.
You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with mysql-test-run.pl
cd mysql-test ; perl mysql-test-run.pl

Please report any problems with the /usr/bin/mysqlbug script!

The latest information about MySQL is available on the web at
[http://www.mysql.com](http://www.mysql.com)
Support MySQL by buying support/licenses at [http://shop.mysql.com](http://shop.mysql.com)
** root@Ubuntu:~# mysqld_safe --user=mysql &**
[1] 11398
root@Ubuntu:~# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[11435]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[11440]: ended
mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[1]+  Done                    mysqld_safe --user=mysql
** root@Ubuntu:~# **


---

### Post by Select* on 2008-03-09
Hope this helps.

This should fix your MYSQL installation / reinstallation issues, if your getting "dpkg: error processing mysql-server-5.0 (--configure):
" or other similar error.

If you have downloaded an already tried to install make sure all your mysql packages are removed. This step can be skipped, but I found when I had this issue I tried many different installation commands and wanted to remove all. The following command will remove MYSQL and MYSQL 5.0.

sudo apt-get autoremove --purge mysql-server mysql-server-5.0 
(^if root remove sudo)

Now reinstall with the following command, which will install the latest MYSQL

sudo apt-get install mysql-server 
(^if root remove sudo)

You will probably get the same error again, but don't dispair. Change to directory /etc/mysql/ and edit the my.cnf file by doing the following.

cp my.cnf my.cnf.bak
vi my.cnf

Once you have the file open navigate down till you see the bind-address setting. You may see two but only one should be un-commented. Change the bind-address setting so it looks like bind-address = 0.0.0.0 and save the file.

Now we will finish configuration of MYSQL by using the following command.

sudo dpkg --configure -a
(^if root remove sudo)

This command will continue all unfinished software auto configurations, in this case MYSQL. The database should start this time.

Edit the my.cnf file again to change the bind-address to the IP address of choice (127.0.0.0 for local only) or external interface IP address. Issue command to restart MYSQL and you should be good to go.

sudo /etc/init.d/mysql restart
(^if root remove sudo)

---

### Post by hughh on 2008-03-17
Thank you very much, Select*; this seems to have worked!

---

