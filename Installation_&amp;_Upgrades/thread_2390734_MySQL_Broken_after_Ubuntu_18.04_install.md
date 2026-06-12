---
title: "MySQL Broken after Ubuntu 18.04 install"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2018-05-01
Because the 18.04 install insisted on wiping out 4 years of work on my laptop I had to reinstall LAMP from scratch.  I just spent two hours fixing the apache settings and the PHP settings.  Now I am trying to get into MySQL but something in the LAMP install screwed up the root password.  I do not recall being prompted for the root password and if I had been I have a standard password that I use in all installs until I have the system running, and that is not what is set.  So I follow the instructions for how to get around that but they don't work!

```
$ sudo service mysql stop
$ sudo mysqld_safe --skip-grant-tables &
[3] 29329
jcobban@jcobban-lemur:~$ 2018-05-02T01:04:11.333470Z mysqld_safe Logging to syslog.
2018-05-02T01:04:11.336592Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2018-05-02T01:04:11.338975Z mysqld_safe Directory '/var/run/mysqld' for UNIX socket file don't exists.
$mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[3]   Exit 1                  sudo mysqld_safe --skip-grant-tables
```

I tried uninstalling and reinstalling mysql-server but it did not prompt for the root password.  It seems to use the contents of /var/lib/mysql, which is not removed when mysql-server is removed.  So I tried to remove the contents of /var/lib/mysql:

```
$ sudo ls /var/lib/mysql
auto.cnf     ib_buffer_pool  ib_logfile0  mysql          sys
debian-5.7.flag  ibdata1     ib_logfile1  performance_schema
jcobban@jcobban-lemur:~$ sudo rm /var/lib/mysql/*
rm: cannot remove '/var/lib/mysql/*': No such file or directory
$ cd /var/lib/mysql
bash: cd: /var/lib/mysql: Permission denied
jcobban@jcobban-lemur:~$ sudo cd /var/lib/mysql
sudo: cd: command not found
```


Why can I not even with root authority remove the files that ls says are present?

So I completely removed and reinstalled MySql and tried to start it again:

```
jcobban@jcobban-lemur:~$ sudo service mysql start
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
jcobban@jcobban-lemur:~$ sudo systemctl status mysql.service
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-05-01 21:35:52 EDT; 3s ago
  Process: 28923 ExecStart=/usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid (code=exited, status=0/SUCCESS)
  Process: 30463 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=217/USER)
 Main PID: 28925 (code=exited, status=0/SUCCESS)

May 01 21:35:52 jcobban-lemur systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
May 01 21:35:52 jcobban-lemur systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
May 01 21:35:52 jcobban-lemur systemd[1]: Stopped MySQL Community Server.
May 01 21:35:52 jcobban-lemur systemd[1]: mysql.service: Start request repeated too quickly.
May 01 21:35:52 jcobban-lemur systemd[1]: mysql.service: Failed with result 'exit-code'.
May 01 21:35:52 jcobban-lemur systemd[1]: Failed to start MySQL Community Server.

```

I am sorry if I seem to be complaining to the wrong audience but if Ubuntu had not insisted on wiping out my system I wouldn't be in this situation.  I am annoyed that I am forced to reinstall and reconfigure every single piece of software that I had installed on the system, and that restoring the contents of my home directory is not enough to get all of this working without days of labor.

---

### Post by pqwoerituytrueiwoq on 2018-05-01
This thread has a link to a workaround
[https://ubuntuforums.org/showthread.php?t=2386426](https://ubuntuforums.org/showthread.php?t=2386426)

---

### Post by 7-webmaster on 2018-05-01
> **pqwoerituytrueiwoq said:**
> This thread has a link to a workaround
[https://ubuntuforums.org/showthread.php?t=2386426](https://ubuntuforums.org/showthread.php?t=2386426)

As I said I use a standard password for all root access during initial  setup.  So the password should have been the same.

I tried uninstalling and reinstalling mysql again, ensuring that all of the associated directories had been removed.  Then I try to set the initial root password as follows:

$ mysql_secure_installation

Securing the MySQL server deployment.

Enter password for user root: 
Error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

The directory /var/run/mysqld which is complained about above **does not exis**t.  So I tried creating it but I cannot chown the new directory to the owning userid for MySQL because that userid does not exist!

sudo chown mysqld /var/run/mysqld
chown: invalid user: &#8216;mysqld&#8217;

I even checked /etc/passwd and there is no userid with "sql" in the name.

I cannot even start the MySQL server:

```
$ sudo service mysql start
[sudo] password for jcobban: 
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
jcobban@jcobban-lemur:~$ systemctl status mysql.service
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
   Active: failed (Result: exit-code) since Tue 2018-05-01 21:47:57 EDT; 12s ago
  Process: 1919 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exit

May 01 21:47:57 jcobban-lemur systemd[1]: mysql.service: Service hold-off time o
May 01 21:47:57 jcobban-lemur systemd[1]: mysql.service: Scheduled restart job, 
May 01 21:47:57 jcobban-lemur systemd[1]: Stopped MySQL Community Server.
May 01 21:47:57 jcobban-lemur systemd[1]: mysql.service: Start request repeated 
May 01 21:47:57 jcobban-lemur systemd[1]: mysql.service: Failed with result 'exi
May 01 21:47:57 jcobban-lemur systemd[1]: Failed to start MySQL Community Server
```

The following is everything I did to remove mysql from the system and then reinstall it all according to the instructions:

```
jcobban@jcobban-lemur:~$ sudo -i
root@jcobban-lemur:~# service mysql stop
root@jcobban-lemur:~# killall -KILL mysql mysqld_safe mysqld
mysql: no process found
mysqld_safe: no process found
mysqld: no process found
root@jcobban-lemur:~# apt-get --yes purge mysql-server mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'mysql-client' is not installed, so not removed
Package 'mysql-server' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jcobban-lemur:~# apt-get --yes autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jcobban-lemur:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@jcobban-lemur:~# deluser --remove-home mysql
/usr/sbin/deluser: The user 'mysql' does not exist.
root@jcobban-lemur:~# delgroup mysql
The group `mysql' does not exist.
root@jcobban-lemur:~# rm -rf /etc/apparmor.d/abstractions/mysql /etc/apparmor.d/cache/usr.sbin.mysqld /etc/mysql /var/lib/mysql /var/log/mysql* /var/log/upstart/mysql.log* /var/run/mysqld
root@jcobban-lemur:~# updatedb
root@jcobban-lemur:~# exit
logout
jcobban@jcobban-lemur:~$ sudo apt install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,948 B of archives.
After this operation, 110 kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 mysql-server all 5.7.22-0ubuntu18.04.1 [9,948 B]
Fetched 9,948 B in 1s (10.2 kB/s)      
Selecting previously unselected package mysql-server.
(Reading database ... 131665 files and directories currently installed.)
Preparing to unpack .../mysql-server_5.7.22-0ubuntu18.04.1_all.deb ...
Unpacking mysql-server (5.7.22-0ubuntu18.04.1) ...
Setting up mysql-server (5.7.22-0ubuntu18.04.1) ...

jcobban@jcobban-lemur:~$ sudo apt install mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-client
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,820 B of archives.
After this operation, 110 kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 mysql-client all 5.7.22-0ubuntu18.04.1 [9,820 B]
Fetched 9,820 B in 0s (22.7 kB/s)       
Selecting previously unselected package mysql-client.
(Reading database ... 131669 files and directories currently installed.)
Preparing to unpack .../mysql-client_5.7.22-0ubuntu18.04.1_all.deb ...
Unpacking mysql-client (5.7.22-0ubuntu18.04.1) ...
Setting up mysql-client (5.7.22-0ubuntu18.04.1) ...
jcobban@jcobban-lemur:~$ sudo apt update
Hit:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:3 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) bionic InRelease        
Hit:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
jcobban@jcobban-lemur:~$ mysql_secure_installation

Securing the MySQL server deployment.

Enter password for user root: 
Error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
jcobban@jcobban-lemur:~$
```

---

### Post by 7-webmaster on 2018-05-04
I gave up on trying to install MySQL and tried to install MariaDB but I cannot install that either!

```
$ sudo apt install mariadb-server mariadb-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  galera-3 gawk libconfig-inifiles-perl libdbd-mysql-perl libdbi-perl
  libjemalloc1 libmysqlclient20 libreadline5 libsigsegv2 libterm-readkey-perl
  mariadb-client-10.1 mariadb-client-core-10.1 mariadb-common
  mariadb-server-10.1 mariadb-server-core-10.1 socat
Suggested packages:
  gawk-doc libmldbm-perl libnet-daemon-perl libsql-statement-perl mailx tinyca
The following packages will be REMOVED:
  mysql-client-5.7 mysql-client-core-5.7 mysql-server-5.7
  mysql-server-core-5.7
The following NEW packages will be installed:
  galera-3 gawk libconfig-inifiles-perl libdbd-mysql-perl libdbi-perl
  libjemalloc1 libmysqlclient20 libreadline5 libsigsegv2 libterm-readkey-perl
  mariadb-client mariadb-client-10.1 mariadb-client-core-10.1 mariadb-common
  mariadb-server mariadb-server-10.1 mariadb-server-core-10.1 socat
0 upgraded, 18 newly installed, 4 to remove and 0 not upgraded.
Need to get 24.0 MB of archives.
After this operation, 24.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libsigsegv2 amd64 2.12-1 [14.7 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 gawk amd64 1:4.1.4+dfsg-1build1 [401 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-common all 1:10.1.29-6 [15.3 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 galera-3 amd64 25.3.20-1 [947 kB]
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libdbi-perl amd64 1.640-1 [724 kB]
Get:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libreadline5 amd64 5.2+dfsg-3build1 [99.5 kB]
Get:7 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-client-core-10.1 amd64 1:10.1.29-6 [4,735 kB]
Get:8 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libconfig-inifiles-perl all 2.94-1 [40.4 kB]
Get:9 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 libjemalloc1 amd64 3.6.0-11 [82.4 kB]
Get:10 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-client-10.1 amd64 1:10.1.29-6 [5,624 kB]
Get:11 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-server-core-10.1 amd64 1:10.1.29-6 [4,929 kB]
Get:12 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 socat amd64 1.7.3.2-2ubuntu2 [342 kB]
Get:13 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-server-10.1 amd64 1:10.1.29-6 [5,086 kB]
Get:14 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libmysqlclient20 amd64 5.7.22-0ubuntu18.04.1 [815 kB]
Get:15 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 libdbd-mysql-perl amd64 4.046-1 [82.0 kB]
Get:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 libterm-readkey-perl amd64 2.37-1build1 [24.4 kB]
Get:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-client all 1:10.1.29-6 [12.8 kB]
Get:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-server all 1:10.1.29-6 [12.9 kB]
Fetched 24.0 MB in 25s (944 kB/s)                                              
Preconfiguring packages ...
(Reading database ... 131664 files and directories currently installed.)
Removing mysql-server-5.7 (5.7.22-0ubuntu18.04.1) ...
update-alternatives: warning: alternative /etc/mysql/my.cnf.fallback (part of link group my.cnf) doesn't exist; removing from list of alternatives
update-alternatives: warning: alternative /etc/mysql/mysql.cnf (part of link group my.cnf) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/my.cnf is dangling; it will be updated with best choice
Removing mysql-client-5.7 (5.7.22-0ubuntu18.04.1) ...
Removing mysql-client-core-5.7 (5.7.22-0ubuntu18.04.1) ...
Removing mysql-server-core-5.7 (5.7.22-0ubuntu18.04.1) ...
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 131449 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.12-1_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.12-1) ...
Setting up libsigsegv2:amd64 (2.12-1) ...
Selecting previously unselected package gawk.
(Reading database ... 131456 files and directories currently installed.)
Preparing to unpack .../00-gawk_1%3a4.1.4+dfsg-1build1_amd64.deb ...
Unpacking gawk (1:4.1.4+dfsg-1build1) ...
Selecting previously unselected package mariadb-common.
Preparing to unpack .../01-mariadb-common_1%3a10.1.29-6_all.deb ...
Unpacking mariadb-common (1:10.1.29-6) ...
Selecting previously unselected package galera-3.
Preparing to unpack .../02-galera-3_25.3.20-1_amd64.deb ...
Unpacking galera-3 (25.3.20-1) ...
Selecting previously unselected package libdbi-perl.
Preparing to unpack .../03-libdbi-perl_1.640-1_amd64.deb ...
Unpacking libdbi-perl (1.640-1) ...
Selecting previously unselected package libreadline5:amd64.
Preparing to unpack .../04-libreadline5_5.2+dfsg-3build1_amd64.deb ...
Unpacking libreadline5:amd64 (5.2+dfsg-3build1) ...
Selecting previously unselected package mariadb-client-core-10.1.
Preparing to unpack .../05-mariadb-client-core-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-client-core-10.1 (1:10.1.29-6) ...
Selecting previously unselected package libconfig-inifiles-perl.
Preparing to unpack .../06-libconfig-inifiles-perl_2.94-1_all.deb ...
Unpacking libconfig-inifiles-perl (2.94-1) ...
Selecting previously unselected package libjemalloc1.
Preparing to unpack .../07-libjemalloc1_3.6.0-11_amd64.deb ...
Unpacking libjemalloc1 (3.6.0-11) ...
Selecting previously unselected package mariadb-client-10.1.
Preparing to unpack .../08-mariadb-client-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-client-10.1 (1:10.1.29-6) ...
Selecting previously unselected package mariadb-server-core-10.1.
Preparing to unpack .../09-mariadb-server-core-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-server-core-10.1 (1:10.1.29-6) ...
Selecting previously unselected package socat.
Preparing to unpack .../10-socat_1.7.3.2-2ubuntu2_amd64.deb ...
Unpacking socat (1.7.3.2-2ubuntu2) ...
Setting up mariadb-common (1:10.1.29-6) ...
update-alternatives: using /etc/mysql/mariadb.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mariadb-server-10.1.
(Reading database ... 131973 files and directories currently installed.)
Preparing to unpack .../0-mariadb-server-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-server-10.1 (1:10.1.29-6) ...
Selecting previously unselected package libmysqlclient20:amd64.
Preparing to unpack .../1-libmysqlclient20_5.7.22-0ubuntu18.04.1_amd64.deb ...
Unpacking libmysqlclient20:amd64 (5.7.22-0ubuntu18.04.1) ...
Selecting previously unselected package libdbd-mysql-perl.
Preparing to unpack .../2-libdbd-mysql-perl_4.046-1_amd64.deb ...
Unpacking libdbd-mysql-perl (4.046-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../3-libterm-readkey-perl_2.37-1build1_amd64.deb ...
Unpacking libterm-readkey-perl (2.37-1build1) ...
Selecting previously unselected package mariadb-client.
Preparing to unpack .../4-mariadb-client_1%3a10.1.29-6_all.deb ...
Unpacking mariadb-client (1:10.1.29-6) ...
Selecting previously unselected package mariadb-server.
Preparing to unpack .../5-mariadb-server_1%3a10.1.29-6_all.deb ...
Unpacking mariadb-server (1:10.1.29-6) ...
Setting up libconfig-inifiles-perl (2.94-1) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Setting up libjemalloc1 (3.6.0-11) ...
Setting up socat (1.7.3.2-2ubuntu2) ...
Setting up gawk (1:4.1.4+dfsg-1build1) ...
Setting up libterm-readkey-perl (2.37-1build1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up galera-3 (25.3.20-1) ...
Processing triggers for systemd (237-3ubuntu10) ...
Processing triggers for man-db (2.8.3-2) ...
Setting up libmysqlclient20:amd64 (5.7.22-0ubuntu18.04.1) ...
Setting up libreadline5:amd64 (5.2+dfsg-3build1) ...
Setting up libdbi-perl (1.640-1) ...
Setting up mariadb-server-core-10.1 (1:10.1.29-6) ...
Setting up mariadb-client-core-10.1 (1:10.1.29-6) ...
Setting up libdbd-mysql-perl (4.046-1) ...
Setting up mariadb-client-10.1 (1:10.1.29-6) ...
Setting up mariadb-client (1:10.1.29-6) ...
Setting up mariadb-server-10.1 (1:10.1.29-6) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.mysqld ...
Installing new version of config file /etc/init.d/mysql ...
Installing new version of config file /etc/logrotate.d/mysql-server ...

Configuration file '/etc/mysql/debian-start'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** debian-start (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/mysql/debian-start ...
[B]dpkg: error processing package mariadb-server-10.1 (--configure):
 installed mariadb-server-10.1 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mariadb-server:
 mariadb-server depends on mariadb-server-10.1 (>= 1:10.1.29-6); however:
  Package mariadb-server-10.1 is not configured yet.

dpkg: error processing package mariadb-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10) ...
Errors were encountered while processing:
 mariadb-server-10.1
 mariadb-server[/B]
**E: Sub-process /usr/bin/dpkg returned an error code (1)**
jcobban@jcobban-lemur:~$ sudo mysql_secure_installation
/usr/bin/my_print_defaults: Can't read dir of '/etc/mysql/conf.d/' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2 "No such file or directory")
```

HOW DO I INSTALL A DATABASE SERVER IF ALL I GET IS USELESS MESSAGES LIKE THIS!

I gave up on trying to install MySQL and tried to install MariaDB but I cannot install that either!

```
$ sudo apt install mariadb-server mariadb-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  galera-3 gawk libconfig-inifiles-perl libdbd-mysql-perl libdbi-perl
  libjemalloc1 libmysqlclient20 libreadline5 libsigsegv2 libterm-readkey-perl
  mariadb-client-10.1 mariadb-client-core-10.1 mariadb-common
  mariadb-server-10.1 mariadb-server-core-10.1 socat
Suggested packages:
  gawk-doc libmldbm-perl libnet-daemon-perl libsql-statement-perl mailx tinyca
The following packages will be REMOVED:
  mysql-client-5.7 mysql-client-core-5.7 mysql-server-5.7
  mysql-server-core-5.7
The following NEW packages will be installed:
  galera-3 gawk libconfig-inifiles-perl libdbd-mysql-perl libdbi-perl
  libjemalloc1 libmysqlclient20 libreadline5 libsigsegv2 libterm-readkey-perl
  mariadb-client mariadb-client-10.1 mariadb-client-core-10.1 mariadb-common
  mariadb-server mariadb-server-10.1 mariadb-server-core-10.1 socat
0 upgraded, 18 newly installed, 4 to remove and 0 not upgraded.
Need to get 24.0 MB of archives.
After this operation, 24.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libsigsegv2 amd64 2.12-1 [14.7 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 gawk amd64 1:4.1.4+dfsg-1build1 [401 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-common all 1:10.1.29-6 [15.3 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 galera-3 amd64 25.3.20-1 [947 kB]
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libdbi-perl amd64 1.640-1 [724 kB]
Get:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libreadline5 amd64 5.2+dfsg-3build1 [99.5 kB]
Get:7 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-client-core-10.1 amd64 1:10.1.29-6 [4,735 kB]
Get:8 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 libconfig-inifiles-perl all 2.94-1 [40.4 kB]
Get:9 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 libjemalloc1 amd64 3.6.0-11 [82.4 kB]
Get:10 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-client-10.1 amd64 1:10.1.29-6 [5,624 kB]
Get:11 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-server-core-10.1 amd64 1:10.1.29-6 [4,929 kB]
Get:12 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 socat amd64 1.7.3.2-2ubuntu2 [342 kB]
Get:13 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-server-10.1 amd64 1:10.1.29-6 [5,086 kB]
Get:14 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libmysqlclient20 amd64 5.7.22-0ubuntu18.04.1 [815 kB]
Get:15 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 libdbd-mysql-perl amd64 4.046-1 [82.0 kB]
Get:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 libterm-readkey-perl amd64 2.37-1build1 [24.4 kB]
Get:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-client all 1:10.1.29-6 [12.8 kB]
Get:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 mariadb-server all 1:10.1.29-6 [12.9 kB]
Fetched 24.0 MB in 25s (944 kB/s)                                              
Preconfiguring packages ...
(Reading database ... 131664 files and directories currently installed.)
Removing mysql-server-5.7 (5.7.22-0ubuntu18.04.1) ...
update-alternatives: warning: alternative /etc/mysql/my.cnf.fallback (part of link group my.cnf) doesn't exist; removing from list of alternatives
update-alternatives: warning: alternative /etc/mysql/mysql.cnf (part of link group my.cnf) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/my.cnf is dangling; it will be updated with best choice
Removing mysql-client-5.7 (5.7.22-0ubuntu18.04.1) ...
Removing mysql-client-core-5.7 (5.7.22-0ubuntu18.04.1) ...
Removing mysql-server-core-5.7 (5.7.22-0ubuntu18.04.1) ...
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 131449 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.12-1_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.12-1) ...
Setting up libsigsegv2:amd64 (2.12-1) ...
Selecting previously unselected package gawk.
(Reading database ... 131456 files and directories currently installed.)
Preparing to unpack .../00-gawk_1%3a4.1.4+dfsg-1build1_amd64.deb ...
Unpacking gawk (1:4.1.4+dfsg-1build1) ...
Selecting previously unselected package mariadb-common.
Preparing to unpack .../01-mariadb-common_1%3a10.1.29-6_all.deb ...
Unpacking mariadb-common (1:10.1.29-6) ...
Selecting previously unselected package galera-3.
Preparing to unpack .../02-galera-3_25.3.20-1_amd64.deb ...
Unpacking galera-3 (25.3.20-1) ...
Selecting previously unselected package libdbi-perl.
Preparing to unpack .../03-libdbi-perl_1.640-1_amd64.deb ...
Unpacking libdbi-perl (1.640-1) ...
Selecting previously unselected package libreadline5:amd64.
Preparing to unpack .../04-libreadline5_5.2+dfsg-3build1_amd64.deb ...
Unpacking libreadline5:amd64 (5.2+dfsg-3build1) ...
Selecting previously unselected package mariadb-client-core-10.1.
Preparing to unpack .../05-mariadb-client-core-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-client-core-10.1 (1:10.1.29-6) ...
Selecting previously unselected package libconfig-inifiles-perl.
Preparing to unpack .../06-libconfig-inifiles-perl_2.94-1_all.deb ...
Unpacking libconfig-inifiles-perl (2.94-1) ...
Selecting previously unselected package libjemalloc1.
Preparing to unpack .../07-libjemalloc1_3.6.0-11_amd64.deb ...
Unpacking libjemalloc1 (3.6.0-11) ...
Selecting previously unselected package mariadb-client-10.1.
Preparing to unpack .../08-mariadb-client-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-client-10.1 (1:10.1.29-6) ...
Selecting previously unselected package mariadb-server-core-10.1.
Preparing to unpack .../09-mariadb-server-core-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-server-core-10.1 (1:10.1.29-6) ...
Selecting previously unselected package socat.
Preparing to unpack .../10-socat_1.7.3.2-2ubuntu2_amd64.deb ...
Unpacking socat (1.7.3.2-2ubuntu2) ...
Setting up mariadb-common (1:10.1.29-6) ...
update-alternatives: using /etc/mysql/mariadb.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mariadb-server-10.1.
(Reading database ... 131973 files and directories currently installed.)
Preparing to unpack .../0-mariadb-server-10.1_1%3a10.1.29-6_amd64.deb ...
Unpacking mariadb-server-10.1 (1:10.1.29-6) ...
Selecting previously unselected package libmysqlclient20:amd64.
Preparing to unpack .../1-libmysqlclient20_5.7.22-0ubuntu18.04.1_amd64.deb ...
Unpacking libmysqlclient20:amd64 (5.7.22-0ubuntu18.04.1) ...
Selecting previously unselected package libdbd-mysql-perl.
Preparing to unpack .../2-libdbd-mysql-perl_4.046-1_amd64.deb ...
Unpacking libdbd-mysql-perl (4.046-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../3-libterm-readkey-perl_2.37-1build1_amd64.deb ...
Unpacking libterm-readkey-perl (2.37-1build1) ...
Selecting previously unselected package mariadb-client.
Preparing to unpack .../4-mariadb-client_1%3a10.1.29-6_all.deb ...
Unpacking mariadb-client (1:10.1.29-6) ...
Selecting previously unselected package mariadb-server.
Preparing to unpack .../5-mariadb-server_1%3a10.1.29-6_all.deb ...
Unpacking mariadb-server (1:10.1.29-6) ...
Setting up libconfig-inifiles-perl (2.94-1) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Setting up libjemalloc1 (3.6.0-11) ...
Setting up socat (1.7.3.2-2ubuntu2) ...
Setting up gawk (1:4.1.4+dfsg-1build1) ...
Setting up libterm-readkey-perl (2.37-1build1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up galera-3 (25.3.20-1) ...
Processing triggers for systemd (237-3ubuntu10) ...
Processing triggers for man-db (2.8.3-2) ...
Setting up libmysqlclient20:amd64 (5.7.22-0ubuntu18.04.1) ...
Setting up libreadline5:amd64 (5.2+dfsg-3build1) ...
Setting up libdbi-perl (1.640-1) ...
Setting up mariadb-server-core-10.1 (1:10.1.29-6) ...
Setting up mariadb-client-core-10.1 (1:10.1.29-6) ...
Setting up libdbd-mysql-perl (4.046-1) ...
Setting up mariadb-client-10.1 (1:10.1.29-6) ...
Setting up mariadb-client (1:10.1.29-6) ...
Setting up mariadb-server-10.1 (1:10.1.29-6) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.mysqld ...
Installing new version of config file /etc/init.d/mysql ...
Installing new version of config file /etc/logrotate.d/mysql-server ...

Configuration file '/etc/mysql/debian-start'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** debian-start (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/mysql/debian-start ...
[B]dpkg: error processing package mariadb-server-10.1 (--configure):
 installed mariadb-server-10.1 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mariadb-server:
 mariadb-server depends on mariadb-server-10.1 (>= 1:10.1.29-6); however:
  Package mariadb-server-10.1 is not configured yet.

dpkg: error processing package mariadb-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10) ...
Errors were encountered while processing:
 mariadb-server-10.1
 mariadb-server[/B]
**E: Sub-process /usr/bin/dpkg returned an error code (1)**
jcobban@jcobban-lemur:~$ sudo mysql_secure_installation
/usr/bin/my_print_defaults: Can't read dir of '/etc/mysql/conf.d/' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2 "No such file or directory")
```

HOW DO I INSTALL A DATABASE SERVER IF ALL I GET IS USELESS MESSAGES LIKE THIS!

---

### Post by 7-webmaster on 2018-05-08
When I tried installing GIMP using the Ubuntu Software GUI it reported failure to install and blamed the incomplete MariaDB install.  So I tried installing through the command line which demonstrated that it was simply a misunderstanding by the GUI tool.
```

$ sudo apt install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version (2.8.22-1).
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up mariadb-server-10.1 (1:10.1.29-6) ...
dpkg: error processing package mariadb-server-10.1 (--configure):
 installed mariadb-server-10.1 package post-installation script subprocess returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of mariadb-server:
 mariadb-server depends on mariadb-server-10.1 (>= 1:10.1.29-6); however:
  Package mariadb-server-10.1 is not configured yet.

dpkg: error processing package mariadb-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mariadb-server-10.1
 mariadb-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
So I rebooted and tried various MySQL/MariaDB related commands trying to get a better idea of what was going wrong:
```

$ sudo mysql_install_db
/usr/bin/my_print_defaults: Can't read dir of '/etc/mysql/conf.d/' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted
Installing MariaDB/MySQL system tables in '/var/lib/mysql' ...
/usr/sbin/mysqld: Can't read dir of '/etc/mysql/conf.d/' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted

Installation of system tables failed!  Examine the logs in
/var/lib/mysql for more information.

The problem could be conflicting information in an external
my.cnf files. You can ignore these by doing:

    shell> /usr/bin/mysql_install_db --defaults-file=~/.my.cnf

You can also try to start the mysqld daemon with:

    shell> /usr/sbin/mysqld --skip-grant --general-log &

and use the command line tool /usr/bin/mysql
to connect to the mysql database and look at the grant tables:

    shell> /usr/bin/mysql -u root mysql
    mysql> show tables;

Try 'mysqld --help' if you have problems with paths.  Using
--general-log gives you a log in /var/lib/mysql that may be helpful.

The latest information about mysql_install_db is available at
[https://mariadb.com/kb/en/installing-system-tables-mysql_install_db](https://mariadb.com/kb/en/installing-system-tables-mysql_install_db)
MariaDB is hosted on launchpad; You can find the latest source and
email lists at [http://launchpad.net/maria](http://launchpad.net/maria)

Please check all of the above before submitting a bug report
at [http://mariadb.org/jira](http://mariadb.org/jira)

jcobban@jcobban-lemur:~$ sudo service mysql start

```
This hung and had to be terminated with Ctrl-C.
```

$ ls /etc/msql/conf.d
ls: cannot access '/etc/msql/conf.d': No such file or directory
$ sudo mkdir /etc/mysql/conf.d/
$ sudo mysql_install_db
Installing MariaDB/MySQL system tables in '/var/lib/mysql' ...
2018-05-08 16:27:09 140036134997120 [Note] /usr/sbin/mysqld (mysqld 10.1.29-MariaDB-6) starting as process 3553 ...
OK
Filling help tables...
2018-05-08 16:27:12 140134111333504 [Note] /usr/sbin/mysqld (mysqld 10.1.29-MariaDB-6) starting as process 3582 ...
OK
Creating OpenGIS required SP-s...
2018-05-08 16:27:15 139713894165632 [Note] /usr/sbin/mysqld (mysqld 10.1.29-MariaDB-6) starting as process 3611 ...
OK

To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MariaDB root USER !
To do so, start the server, then issue the following commands:

'/usr/bin/mysqladmin' -u root password 'new-password'
'/usr/bin/mysqladmin' -u root -h jcobban-lemur password 'new-password'

Alternatively you can run:
'/usr/bin/mysql_secure_installation'

which will also give you the option of removing the test
databases and anonymous user created by default.  This is
strongly recommended for production servers.

See the MariaDB Knowledgebase at [http://mariadb.com/kb](http://mariadb.com/kb) or the
MySQL manual for more instructions.

You can start the MariaDB daemon with:
cd '/usr' ; /usr/bin/mysqld_safe --datadir='/var/lib/mysql'

You can test the MariaDB daemon with mysql-test-run.pl
cd '/usr/mysql-test' ; perl mysql-test-run.pl

Please report any problems at [http://mariadb.org/jira](http://mariadb.org/jira)

The latest information about MariaDB is available at [http://mariadb.org/](http://mariadb.org/).
You can find additional information about the MySQL part at:
[http://dev.mysql.com](http://dev.mysql.com)
Consider joining MariaDB's strong and vibrant community:
[https://mariadb.org/get-involved/](https://mariadb.org/get-involved/)

$ sudo service mysql start
$ sudo mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] Y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] Y
 ... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!

```
However I still have the problem that caused me to try to remove and reinstall the DB server:  I cannot sign in to the server using the root password I just defined.
```

$ mysql -u root -p
Enter password: 
ERROR 1698 (28000): Access denied for user 'root'@'localhost'

```
I know I set the right password.  After all I had to enter it TWICE!

The problem turns out to be an improvement in security added some time ago in both MySQL and MariaDB in that they now default to requiring that use of the DB root user be done from the LINUX root user.  So "mysql -u root -p" no longer works, unless you change the definition of the DB root user to revert to using the password defined in the users table.  You have to do "sudo mysql -u root" instead.  This is obviously more secure but is not at all obvious to the blind-sided user.  This is the first time in years that I have installed MySQL or MariaDB from scratch.  To the best of my knowledge I have upgraded releases of Ubuntu for at least 12 years, which means that the new functionality did not take effect because MySQL/MariaDB were always working with an old users table and therefore continued to use the password from that table rather than requiring that I access the account with Linux root authority.  It would have been really nice if the mysql client had WARNED me that was the reason the signon was rejected instead of wasting a week of my time.

---

### Post by louis5 on 2018-05-13
Hi. Did you find a solution for this? I seem to have the exact same problem. I've uninstall and reinstalled a few times. 
It doesn't request a root password during install like it did on 16.04. Don't know if it's the mysql version or the new 18.04. 
Changing the password with     sudo mysql_secure_installation seems to have no affect. 
ERROR 1698 (28000): Access denied for user 'root'@'localhost'

---

### Post by wildmanne39 on 2018-05-13
Hello louis5, please create your own thread you will be more likely to get the help you need then if you post for help in another users thread.

Thanks

---

### Post by erikoma on 2018-06-01
I have spent days trying to solve this issue. Running the setup VALIDATE PASSWORD plugin never completes, and whether I set a password or not, there's no access to 'root'@'localhost', and no way (that I have tried) to (re)set the password. There's absolutely no access to the databases. Without using the setup VALIDATE PASSWORD plugin it's possible to get status from databases, but no application gets access.
The work with MySQL on 18.04 is evidently not completed. Fortunately, my main web server is still running 16.04 ... :)

---

### Post by hgkrug1 on 2019-02-16
I have encountered the same problem (Ubuntu 18.04 with Mariadb), I have yet to find a good solution.  The best I found ([https://askubuntu.com/questions/705458/ubuntu-15-10-mysql-error-1524-unix-socket](https://askubuntu.com/questions/705458/ubuntu-15-10-mysql-error-1524-unix-socket) - the answer by Roy Ran to wards the end) gave me a temporary solution that worked only until I have restarted my computer.

---

### Post by hgkrug1 on 2019-02-16
I also had many problem with both mysql and mariadb (ubuntu 18.04). I could not get mariadb to work. I both using instructions at [https://stackoverflow.com/questions/50573787/how-to-forcefully-remove-mysql-and-mariadb-from-ubuntu-16-04-without-apt-get](https://stackoverflow.com/questions/50573787/how-to-forcefully-remove-mysql-and-mariadb-from-ubuntu-16-04-without-apt-get) 

$ dpkg --list|grep -i mysql 
and 
$ dpkg --list|grep -i mariadb

$ dpkg -remove --force-remove-reinstreq <package-list>

Then installed mysql as described at [https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/) 

Works well now, even after reboot. Don't know why this solution is not more widely spreaded!

---

### Post by sparke2 on 2019-06-24
[COLOR=#DD4814][COLOR=#000000]Thanks, [7-webmaster]("https://ubuntuforums.org/member.php?u=1876621").
I set up MySql servers frequently and have not run across this issue until recently building a LAMP stack on Bionic Beaver. 
Been Googling the heck out of the internet and this is the ONLY place that has mentioned the new "sudo mysql" requirement. 
Seems like there would be more people talking about this.

I'm not sure what has been more frustrating this week, the MySQL issue or trying to get the SSO login setup on this forum ;-)[/COLOR][/COLOR]

---

