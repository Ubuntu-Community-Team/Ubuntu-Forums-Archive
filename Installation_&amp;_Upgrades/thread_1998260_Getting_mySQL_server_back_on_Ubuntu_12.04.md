---
title: "Getting mySQL server back on Ubuntu 12.04"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by lads on 2012-06-06
Dear all,

I found out today that the upgrade to Ubuntu 12.04 send out mySQL to the void. I immediately tried to get it back but got an error:

```
$ sudo apt-get install mysql-server
[sudo] password for desousa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.5 mysql-server-core-5.5
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server mysql-server-5.5 mysql-server-core-5.5
0 upgraded, 3 newly installed, 0 to remove and 26 not upgraded.
Need to get 14.9 MB of archives.
After this operation, 52.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://de.archive.ubuntu.com/ubuntu/ precise/main mysql-server-core-5.5 amd64 5.5.22-0ubuntu1 [6,022 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ precise/main mysql-server-5.5 amd64 5.5.22-0ubuntu1 [8,816 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ precise/main mysql-server all 5.5.22-0ubuntu1 [11.8 kB]
Fetched 14.9 MB in 2s (4,960 kB/s)       
Preconfiguring packages ...
Selecting previously unselected package mysql-server-core-5.5.
(Reading database ... 412919 files and directories currently installed.)
Unpacking mysql-server-core-5.5 (from .../mysql-server-core-5.5_5.5.22-0ubuntu1_amd64.deb) ...
Selecting previously unselected package mysql-server-5.5.
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/mysql/plugin/ha_example.so', which is also in package libmysqlclient-dev 5.5.23-1~dotdeb.0
Selecting previously unselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.5.22-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

After this mySQL is not available:

```
$ sudo netstat -tap | grep mysql
$ sudo /etc/init.d/mysql restart
sudo: /etc/init.d/mysql: command not found
```

The first web search results pointed to an issue with the root password. I tried to reconfigure:

```
$ sudo dpkg-reconfigure mysql-server
/usr/sbin/dpkg-reconfigure: mysql-server is broken or not fully installed
```

After some more duckduckgoing I found a reference to the old packages disturbing the new installation. Indeed some old packages were still there:

```
$ dpkg --get-selections | grep mysql
gambas2-gb-db-mysql				install
libdbd-mysql-perl				install
libmysqlclient-dev				install
libmysqlclient16				install
libmysqlclient18				install
libqt4-sql-mysql				install
mysql-admin					deinstall
mysql-client-5.5				install
mysql-client-core-5.5				install
mysql-common					install
mysql-query-browser				deinstall
mysql-server					install
mysql-server-5.1				deinstall
mysql-server-core-5.5				install
mysql-workbench					install
mysql-workbench-data				install
python-mysql.connector				install

$ sudo dpkg --purge mysql-admin mysql-query-browser mysql-server-5.1
(Reading database ... 413009 files and directories currently installed.)
Removing mysql-admin ...
Purging configuration files for mysql-admin ...
Removing mysql-query-browser ...
Purging configuration files for mysql-query-browser ...
Removing mysql-server-5.1 ...
Purging configuration files for mysql-server-5.1 ...
Processing triggers for ureadahead ...

$ dpkg --get-selections | grep mysql
gambas2-gb-db-mysql				install
libdbd-mysql-perl				install
libmysqlclient-dev				install
libmysqlclient16				install
libmysqlclient18				install
libqt4-sql-mysql				install
mysql-client-5.5				install
mysql-client-core-5.5				install
mysql-common					install
mysql-server-core-5.5				install
mysql-workbench					install
mysql-workbench-data				install
python-mysql.connector				install
```

Still, after purging the old packages I'm getting the same error as above.  What is going wrong here? Is mySQL supposed to run on 12.04? If yes how can I install it?

Thanks.

---

### Post by lads on 2012-06-07
There's a new development today. As I tried to run the morning upgrade I got this:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.5 but it is not installed
E: Unmet dependencies. Try using -f.
```

So I did as it suggested:

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 55 not upgraded.
1 not fully installed or removed.
Need to get 0 B/8,816 kB of archives.
After this operation, 32.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 413000 files and directories currently installed.)
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/mysql/plugin/ha_example.so', which is also in package libmysqlclient-dev 5.5.23-1~dotdeb.0
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So it seems mysql-server has even embroiled the upgrade. Any clues on how to fix this? 

Thank you.

---

### Post by lads on 2012-06-08
Today I tried to install mySQL with aptitude to see if something would come up in the log:

```
$ sudo aptitude install mysql-server
The following NEW packages will be installed:
  mysql-server mysql-server-5.5{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
Need to get 0 B/8,828 kB of archives. After unpacking 32.8 MB will be used.
Do you want to continue? [Y/n/?] Y
Preconfiguring packages ...              
(Reading database ... 413046 files and directories currently installed.)
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/mysql/plugin/ha_example.so', which is also in package libmysqlclient-dev 5.5.23-1~dotdeb.0
No apport report written because MaxReports is reached already
                                                              Selecting previously unselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.5.22-0ubuntu1_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server
                                         
Current status: 1 broken [+1].

$ cat /var/log/aptitude
Aptitude 0.6.6: log report
Fri, Jun  8 2012 11:26:43 +0200

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 2 packages, and remove 0 packages.
32.8 MB of disk space will be used
===============================================================================
[HOLD, DEPENDENCIES] libcairo-gobject2:amd64
[HOLD, DEPENDENCIES] libcairo-gobject2:i386
[HOLD, DEPENDENCIES] libcairo-script-interpreter2:amd64
[HOLD, DEPENDENCIES] libcairo2:i386
[HOLD, DEPENDENCIES] libcairo2-dev:amd64
[HOLD, DEPENDENCIES] libgdal1-1.7.0:amd64
[HOLD, DEPENDENCIES] printer-driver-ptouch:amd64
[HOLD, DEPENDENCIES] rpcbind:amd64
[INSTALL, DEPENDENCIES] mysql-server-5.5:amd64
[HOLD] libcairo2:amd64
[HOLD] libgdal1:amd64
[HOLD] ptouch-driver:amd64
[HOLD] python-cupshelpers:amd64
[HOLD] software-center:amd64
[HOLD] system-config-printer-common:amd64
[HOLD] system-config-printer-gnome:amd64
[HOLD] system-config-printer-udev:amd64
[INSTALL] mysql-server:amd64
===============================================================================

Log complete.
```

It doesn't say much to me. Any clues?

Thank you.

---

### Post by worthspending on 2012-06-08
I did a fresh install on three local machine directly from CD with no problem.  Leased a dedicated server from 1and1 running Ubuntu 12.04 LTS and had the same problems as you have described.  I will keep you in the loop if I figure something out.  This is really turning into a pain...

---

### Post by worthspending on 2012-06-08
I removed everything related to mysql-server.

sudo apt-get remove mysql-server

physically removed all of the files from the following search
find / -name 'mysql*'

then, I uninstalled apparmor.
sudo apt-get remove apparmor

then, reinstall mysql-server
sudo apt-get install mysql-server

it worked and started up.  rebooted and it was still working.  tried to reinstall apparmor and got the following:


Setting up apparmor (2.7.102-0ubuntu3) ...
 * Starting AppArmor profiles                                                                                                                                   Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'
AppArmor parser error for /etc/apparmor.d/sbin.dhclient in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'
AppArmor parser error for /etc/apparmor.d/usr.sbin.tcpdump in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'
                                                                                                                                                         [fail]
invoke-rc.d: initscript apparmor, action "start" failed.
 * Reloading AppArmor profiles                                                                                                                                  Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
AppArmor parser error for /etc/apparmor.d/sbin.dhclient in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'
AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'
AppArmor parser error for /etc/apparmor.d/usr.sbin.tcpdump in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'
invoke-rc.d: initscript apparmor, action "reload" failed.

seems like some files are jacked up.  hope that helps!!

---

### Post by lads on 2012-06-11
Thank you for the reply worthspending. I tried it the way you suggested but the end result is the same. The log goes below.

Thank you anyway.


```
$ sudo rm -r /usr/lib/mysql
$ sudo rm -r /usr/sbin/mysqld
$ sudo rm -r /usr/share/mysql
$ sudo rm -r /usr/bin/mysqlrepair
$ sudo rm -r /usr/bin/mysql_config
$ sudo rm -r /usr/bin/mysqldumpslow
$ sudo rm -r /usr/bin/mysqlbug
$ sudo rm -r /usr/bin/mysql_plugin
$ sudo rm -r /usr/bin/mysqlslap
$ sudo rm -r /usr/bin/mysqlcheck
$ sudo rm -r /usr/bin/mysqlshow
$ sudo rm -r /usr/bin/mysqldump
$ sudo rm -r /usr/bin/mysqlaccess
$ sudo rm -r /usr/bin/mysqlanalyze
$ sudo rm -r /usr/bin/mysql_install_db
$ sudo rm -r /usr/bin/mysqladmin
$ sudo rm -r /usr/bin/mysql_find_rows
$ sudo rm -r /usr/bin/mysql_upgrade
$ sudo rm -r /usr/bin/mysqlreport
$ sudo rm -r /usr/bin/mysql_fix_extensions
$ sudo rm -r /usr/bin/mysql_client_test
$ sudo rm -r /usr/bin/mysql
$ sudo rm -r /usr/bin/mysqlimport
$ sudo rm -r /usr/bin/mysql-workbench
$ sudo rm -r /usr/bin/mysqloptimize
$ sudo rm -r /usr/bin/mysql_waitpid
$ sudo rm -r /usr/include/mysql

$ sudo apt-get remove apparmor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apparmor apparmor-utils
0 upgraded, 0 newly installed, 2 to remove and 21 not upgraded.
After this operation, 1,607 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 413043 files and directories currently installed.)
Removing apparmor-utils ...
Removing apparmor ...
 * Clearing AppArmor profiles cache                                                                                                                                             [ OK ] 
All profile caches have been cleared, but no profiles have been unloaded.
Unloading profiles will leave already running processes permanently
unconfined, which can lead to unexpected situations.

To set a process to complain mode, use the command line tool
'aa-complain'. To really tear down all profiles, run the init script
with the 'teardown' option."
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

desousa@CRTE-LDS-15461:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server mysql-server-5.5
0 upgraded, 2 newly installed, 0 to remove and 21 not upgraded.
Need to get 0 B/8,828 kB of archives.
After this operation, 32.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 412972 files and directories currently installed.)
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/mysql/plugin/ha_example.so', which is also in package libmysqlclient-dev 5.5.23-1~dotdeb.0
Selecting previously unselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.5.22-0ubuntu1_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lads on 2012-06-12
At [AskUbuntu]("http://askubuntu.com/questions/149289/how-to-get-mysql-back-on-ubuntu-12-04") this is being diagnosed as a conflict with package(s) installed from dotdeb.org. Indeed I had PHP installed from there, but no clear way how to fix it yet.

```

$ sudo cat /etc/apt/sources.list | grep dotdeb.org 
# deb php53.dotdeb.org stable all # disabled on upgrade to precise 
# deb-src php53.dotdeb.org stable all # disabled on upgrade to precise 

$ sudo aptitude search "?installed?origin(dotdeb.org)" 

$ sudo aptitude search "?installed?origin(php53.dotdeb.org)"
```

Any more clues welcome.

---

### Post by lads on 2012-06-13
Today I downloaded the rpm from the mySQL website and tried to install it directly with alien. The result is essentially the same:

```
$ sudo alien -i MySQL-server-5.5.25-1.linux2.6.x86_64.rpm --scripts
	dpkg --no-force-overwrite -i mysql-server_5.5.25-2_amd64.deb
Selecting previously unselected package mysql-server.
(Reading database ... 409708 files and directories currently installed.)
Unpacking mysql-server (from mysql-server_5.5.25-2_amd64.deb) ...
dpkg: error processing mysql-server_5.5.25-2_amd64.deb (--install):
 trying to overwrite '/usr/sbin/mysqld', which is also in package mysql-server-core-5.5 5.5.24-0ubuntu0.12.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 mysql-server_5.5.25-2_amd64.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 192.
	find MySQL-server-5.5.25 -type d -exec chmod 755 {} ;
	rm -rf MySQL-server-5.5.25
```

The message is still quite cryptic and I don't see here any complain about dotdeb.org.

Shouldn't this be filed as a bug?

---

### Post by lads on 2012-06-13
Finally I managed to install mysql server using the -f argument in the apt-get command:

```
apt-get install -f mysql-server
```

Thanks to a tip at [AskUbuntu]("http://askubuntu.com/questions/149289/how-to-get-mysql-back-on-ubuntu-12-04/150313#150313").

---

### Post by nirwanadhiatma on 2012-06-30
> **lads said:**
> Finally I managed to install mysql server using the -f argument in the apt-get command:

```
apt-get install -f mysql-server
```Thanks to a tip at [AskUbuntu]("http://askubuntu.com/questions/149289/how-to-get-mysql-back-on-ubuntu-12-04/150313#150313").

i've tried your method but it didn't work either :
> 
root@linux:~# apt-get install -f mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help me :(

---

### Post by codeninja1 on 2012-08-13
For me, apparmor is preventing mysqld from starting, which prevents the aptitude configuration script from completing becasause it can't start and stop the server to set the root password.

---

### Post by Fnisse on 2012-08-22
Download the deb file on this site:
[http://www.ubuntuupdates.org/package/core/precise/main/base/mysql-server-core-5.5](http://www.ubuntuupdates.org/package/core/precise/main/base/mysql-server-core-5.5) (32bit or 64bit)

Install with:
dpkg -i mysql-server-core-5.5_5.5.22-0ubuntu1_amd64.deb

This should solve the problem.

---

### Post by auraithx on 2012-09-05
> **nirwanadhiatma said:**
> i've tried your method but it didn't work either :


Please help me :(

Same error for me, Fnisse what you suggested produced no errors but didn't fix anything either.

---

### Post by mdesign on 2012-09-07
I have this error too:/

---

### Post by mthornton on 2012-09-07
Hello!

I am getting all of the same errors that lads is getting, except for me sudo apt-get install -f, does not work at all.  I would simply like to revert to mysql-server-5.1 is there an easy way to do this?

Here is the output of sudo apt-get install -f mysql-server

```
 
apt-get install -f mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
120907 21:37:15 [Note] Plugin 'FEDERATED' is disabled.
120907 21:37:15 InnoDB: The InnoDB memory heap is disabled
120907 21:37:15 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120907 21:37:15 InnoDB: Compressed tables use zlib 1.2.3.4
120907 21:37:15 InnoDB: Initializing buffer pool, size = 128.0M
120907 21:37:15 InnoDB: Completed initialization of buffer pool
120907 21:37:15 InnoDB: highest supported file format is Barracuda.
120907 21:37:15  InnoDB: Waiting for the background threads to start
120907 21:37:16 InnoDB: 1.1.8 started; log sequence number 154164236
120907 21:37:16  InnoDB: Starting shutdown...
120907 21:37:16  InnoDB: Shutdown completed; log sequence number 154164236
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Er                   rors were encountered while processing:
 mysql-server-5.5
 mysql-server

```

any help would be greatly appreciated.

Thanks!

---

### Post by lads on 2012-09-10
Mthornton, please try:

```
sudo apt-get install -f mysql-server-5.5
```

I'm not sure it will succeed, but I'd like to see the results.

---

### Post by lads on 2012-09-10
> **mthornton said:**
> I would simply like to revert to mysql-server-5.1 is there an easy way to do this?

It is not in the repos, so, only compiling it.

---

### Post by spaceindaver on 2012-09-16
I had this problem also. After trying everything  posted here I thought it had something to do with accessing the mysqld to update it. I checked the running processes and found that there was a mysql process running. After I stopped it (it was lampp) I was able to install mysql 5.5 without error.

Hope this helps

---

### Post by leandroqm on 2012-09-18
Hi.

I've managed to get it working using this:

apt-get clean ; apt-get autoclean

apt-get remove --purge mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5

apt-get install mysql-server

That's it.
Let me know if it works for you.

---

### Post by MoongazerAlpha on 2012-10-05
In my case, the solution was much simpler as reinstalling MySQL.
I added these two lines into the /etc/apparmor.d/urs.sbin.mysqld file:

```

/home/moongazer/workspace/mysql/ r,
/home/moongazer/workspace/mysql/** rwk,

```This is the place where my databases are stored. After a restart of AppArmor
```
sudo /etc/init.d/apparmor restart
```MySQL was starting and running again without problems. Probably my mistake was to overwrite the AppArmor config during the upgrade process with a fresh one.

---

### Post by rgonnering on 2012-10-28
I had the same symptons as mthornton. The solution that leandroqm proposed worked great.

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get remove --purge mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5

sudo apt-get install mysql-server

Rant: I upgraded to 12.04, and all I can say is it sucks, and Unity is an abomination. Switching workspaces and applications is cumbersome, and there is effectively no configuration capability. People who want eye-candy can buy a Mac.

---

### Post by nacktduscher on 2012-11-06
[FONT="Arial"]**Thanks folks**, [/FONT]
this thread is an extremly usefull one! Not so common these days, but this solution worked for me. So, good job !!!

And btw,I AM happy with Ubuntu AND Unity, because i started with Linux at times when the final clou after installing linux on a Systems was:

"**root&:**  have fun ! "

This System today is not just "eye-candy" but Usability! It's in fact the first Linux that can be marketed to customers without except, because people don't have to be computer scientist to do effective work with it. And  that counts on propagation, so we will have to make some compromise.

---

### Post by archonic_one on 2012-11-06
I've tried

```

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get remove --purge mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5

sudo apt-get install mysql-server

```

I'm still getting the same results as before which are identical to mthorntons.

> **mthornton said:**
> 

```
 
apt-get install -f mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
120907 21:37:15 [Note] Plugin 'FEDERATED' is disabled.
120907 21:37:15 InnoDB: The InnoDB memory heap is disabled
120907 21:37:15 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120907 21:37:15 InnoDB: Compressed tables use zlib 1.2.3.4
120907 21:37:15 InnoDB: Initializing buffer pool, size = 128.0M
120907 21:37:15 InnoDB: Completed initialization of buffer pool
120907 21:37:15 InnoDB: highest supported file format is Barracuda.
120907 21:37:15  InnoDB: Waiting for the background threads to start
120907 21:37:16 InnoDB: 1.1.8 started; log sequence number 154164236
120907 21:37:16  InnoDB: Starting shutdown...
120907 21:37:16  InnoDB: Shutdown completed; log sequence number 154164236
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Er                   rors were encountered while processing:
 mysql-server-5.5
 mysql-server

```

**In addition:**
```

dpkg-reconfigure mysql-server-5.5
/usr/sbin/dpkg-reconfigure: mysql-server-5.5 is broken or not fully installed

```

Anyone else in my boat? I've been searching for a few hours and tried everything reasonable I've found.

---

### Post by J0llyr0ger on 2012-11-08
UGH   I have the same issue, I've tried every suggestion I could find, uninstalled and reinstalled mysql many times, and always with the same result.

HELP!!  :)

---

### Post by archonic_one on 2012-11-12
It's unfortunate this thread is marked as solved! There's some reputation and endless gratitude to anyone that provides the answer to this problem on superuser:
[superuser.com/questions/502822/cant-start-mysql5-5-on-ubuntu-12-04-dpkg-dependency-problems]("http://superuser.com/questions/502822/cant-start-mysql5-5-on-ubuntu-12-04-dpkg-dependency-problems")

If there's no love by tomorrow I'll check for an unsolved thread or post a new one.

---

### Post by lads on 2012-11-13
Looking at the logs it seems to me the issue reported here by archonic_one is different from what I had. In my case *mysql-server-5.5* was not even installing, while for archonic_one it installs but configuration fails.

I tried a bunch of other things before finding the proper solution, maybe the folk having this later issue could also try those. Apart from that I can't help much more.

Good luck.

---

### Post by archonic_one on 2012-11-14
Thanks for the reply. I've started a new thread for my issue (and hopefully others') here:
[http://ubuntuforums.org/showthread.php?t=2084083](http://ubuntuforums.org/showthread.php?t=2084083)

---

### Post by hvnsweeting on 2013-01-16
I 've solved this problem by not enter anything when it ask for root password when run apt-get purge mysql-server

---

### Post by ceadams on 2013-06-22
> **hvnsweeting said:**
> I 've solved this problem by not enter anything when it ask for root password when run apt-get purge mysql-server

I was getting this error because my loopback device was up but not responding (OpenVZ).  If your /var/log/mysql/error.log has this while installing:

```
130622 19:49:42 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306130622 19:49:42 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
130622 19:49:42 [Note] Server socket created on IP: '127.0.0.1'.
130622 19:49:42 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
130622 19:49:42 [ERROR] Do you already have another mysqld server running on port: 3306 ?
130622 19:49:42 [ERROR] Aborting

```

Try this
```
ifconfig lo up
```

Then re-try ```
apt-get install mysql-server
```

If that works, then you'll want to make sure the loopback interface comes up on reboot.  The work-around can be found here: [http://forum.openvz.org/index.php?t=msg&goto=26825&](http://forum.openvz.org/index.php?t=msg&goto=26825&)

> [COLOR=#000000][FONT=Verdana]A further tweak to the above:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Some init scripts (postfix in particular, in my case) expect the network interfaces to be available when they run, and rc.local is running too late (priority 99) in the init order.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]So I've moved the contents of the rc.local script posted earlier into a new /etc/init.d/networking-restart script, and set its priority to S15/K85, so that it runs before most other init scripts. (It could probably go earlier; I just chose 15 because it was before ssh and postfix.) The following installs the new init script into the init start/stop queues:[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace][COLOR=#202020]**Code: [[Select all]("http://forum.openvz.org/index.php?t=msg&goto=26825&#")] [[Show/ hide]("http://forum.openvz.org/index.php?t=msg&goto=26825&#")]**[/COLOR]

update-rc.d networking-restart start 15 2 3 4 5 . stop 85 0 1 6 .[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]Again, this doesn't solve the issue, only provides a work-around, each step a little better than the previous. I don't know how to incorporate this into the official Ubuntu image, but I would be pleased to see it. And, of course, suggestions for further improvements are welcomed.[/FONT][/COLOR]

---

### Post by Stanislav Yotov on 2013-06-24
Run _**one by one**_ the commands bellow, and not all together.
```

sudo apt-get remove --purge mysql-server mysql-client mysql-common mysql-client-*

sudo apt-get autoremove sudo

apt-get autoclean

```
#make sure you have backed up everything before you run this: 
```

rm -rf /var/lib/mysql
rm -rf /etc/mysql*

```

```

sudo dpkg-reconfigure mysql-server-5.5

```

I found most usefull:
[http://askubuntu.com/questions/125686/mysql-fails-to-start-after-upgrade-installation-etc](http://askubuntu.com/questions/125686/mysql-fails-to-start-after-upgrade-installation-etc)

and to some extend :
[http://knowledgelayer.softlayer.com/learning/changing-mysql-data-directory-within-unix-environment](http://knowledgelayer.softlayer.com/learning/changing-mysql-data-directory-within-unix-environment)

---

### Post by Yaser_Rahmani on 2013-08-29
I have same problem, I found that the content of /etc/mysql directory is corrupted and  my.cnf is missed, so I have copyed a correct fresh content in it and do install -f agin. It solved.

---

