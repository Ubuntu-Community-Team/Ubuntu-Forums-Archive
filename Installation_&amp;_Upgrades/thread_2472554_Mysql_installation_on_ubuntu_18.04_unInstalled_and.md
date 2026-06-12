---
title: "Mysql installation on ubuntu 18.04: unInstalled and reinstalled"
date: 2022-03-03
forum: Installation &amp; Upgrades
---

### Post by zak100 on 2022-03-03
Hi,

I uninstall and then reintall mysql on ubuntu 18.04, and after that I tried the following:

 ```
$ sudo service mysql start
~$ sudo /etc/init.d/mysql start
[ ok ] Starting mysql (via systemctl): mysql.service.
~$ sudo systemctl start mysqld
```
Failed to start mysqld.service: Unit mysqld.service not found. I used the following command for removing mysql and its out is also given below:

 ```
$ sudo apt-get remove --purge mysql-\*
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'mysql-workbench' for glob 'mysql-*'
Note, selecting 'mysql-client-5.5' for glob 'mysql-*'
Note, selecting 'mysql-client-5.6' for glob 'mysql-*'
Note, selecting 'mysql-client-5.7' for glob 'mysql-*'
Note, selecting 'mysql-common-5.6' for glob 'mysql-*'
Note, selecting 'mysql-server-5.0' for glob 'mysql-*'
Note, selecting 'mysql-server-5.1' for glob 'mysql-*'
Note, selecting 'mysql-server-5.5' for glob 'mysql-*'
Note, selecting 'mysql-server-5.6' for glob 'mysql-*'
Note, selecting 'mysql-server-5.7' for glob 'mysql-*'
Note, selecting 'mysql-utilities' for glob 'mysql-*'
Note, selecting 'mysql-testsuite' for glob 'mysql-*'
Note, selecting 'mysql-server' for glob 'mysql-*'
Note, selecting 'mysql-client' for glob 'mysql-*'
Note, selecting 'mysql-sandbox' for glob 'mysql-*'
Note, selecting 'mysql-client-core-5.5' for glob 'mysql-*'
Note, selecting 'mysql-client-core-5.6' for glob 'mysql-*'
Note, selecting 'mysql-client-core-5.7' for glob 'mysql-*'
Note, selecting 'mysql-testsuite-5.5' for glob 'mysql-*'
Note, selecting 'mysql-testsuite-5.6' for glob 'mysql-*'
Note, selecting 'mysql-testsuite-5.7' for glob 'mysql-*'
Note, selecting 'mysql-common' for glob 'mysql-*'
Note, selecting 'mysql-workbench-data' for glob 'mysql-*'
Note, selecting 'mysql-server-core-5.1' for glob 'mysql-*'
Note, selecting 'mysql-server-core-5.5' for glob 'mysql-*'
Note, selecting 'mysql-server-core-5.6' for glob 'mysql-*'
Note, selecting 'mysql-server-core-5.7' for glob 'mysql-*'
Note, selecting 'mysql-source-5.7' for glob 'mysql-*'
Package 'mysql-client-5.5' is not installed, so not removed
Package 'mysql-client-5.6' is not installed, so not removed
Package 'mysql-server-core-5.6' is not installed, so not removed
Package 'mysql-client-core-5.5' is not installed, so not removed
Package 'mysql-client-core-5.6' is not installed, so not removed
Note, selecting 'mysql-common' instead of 'mysql-common-5.6'
Package 'mysql-server-5.5' is not installed, so not removed
Package 'mysql-server-5.6' is not installed, so not removed
Package 'mysql-server-core-5.5' is not installed, so not removed
Package 'mysql-testsuite-5.5' is not installed, so not removed
Package 'mysql-testsuite-5.6' is not installed, so not removed
Package 'mysql-server-5.0' is not installed, so not removed
Package 'mysql-server-5.1' is not installed, so not removed
Package 'mysql-server-core-5.1' is not installed, so not removed
Package 'mysql-sandbox' is not installed, so not removed
Package 'mysql-source-5.7' is not installed, so not removed
Package 'mysql-testsuite' is not installed, so not removed
Package 'mysql-testsuite-5.7' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gdal-data libaec0 libarmadillo8 libarpack2 libatkmm-1.6-1v5 libblas3
  libcairomm-1.0-1v5 libcoin80v5 libctemplate3 libdap25 libdapclient6v5
  libepsilon1 libevent-core-2.1-6 libfreexl1 libfyba0 libgeos-3.6.2
  libgeos-c1v5 libgeos-dev libgeotiff2 libglibmm-2.4-1v5
  libgnome-keyring-common libgnome-keyring0 libgraphicsmagick-q16-3
  libgtkmm-2.4-1v5 libhdf4-0-alt libhdf5-100 libiso9660-10 libkmlbase1
  libkmldom1 libkmlengine1 liblapack3 libmad0 libmng2 libnetcdf13 libodbc1
  libogdi3.2 libopenthreads-dev libopenthreads20 libpangomm-1.4-1v5 libpq5
  libproj12 libqhull7 libspatialite7 libsuperlu5 libsz2 libtinyxml2.6.2v5
  liburiparser1 libvcdinfo0 libvsqlitepp3v5 libxerces-c3.2 libxine2
  libxine2-bin libxine2-doc libxine2-ffmpeg libxine2-misc-plugins
  libxine2-plugins odbcinst odbcinst1debian2 proj-bin proj-data
  python-mysql.connector python-paramiko python-pexpect python-ptyprocess
  python-pyodbc python-pysqlite2
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  dbconfig-no-thanks
The following packages will be REMOVED:
  dbconfig-mysql* libgdal20* libmysqlclient20* libmysqlcppconn7v5*
  libopenscenegraph-3.4-131* libopenscenegraph-3.4-dev* libosgearth-dev*
  libosgearth5* libosgearthannotation5* libosgearthfeatures5*
  libosgearthqt5-5* libosgearthsplat5* libosgearthsymbology5*
  libosgearthutil5* mysql-client* mysql-client-5.7* mysql-client-core-5.7*
  mysql-common* mysql-server* mysql-server-5.7* mysql-server-core-5.7*
  mysql-utilities* mysql-workbench* mysql-workbench-data*
  openscenegraph-plugin-osgearth*
The following NEW packages will be installed:
  dbconfig-no-thanks
0 upgraded, 1 newly installed, 25 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 1,314 B of archives.
After this operation, 337 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 dbconfig-no-thanks all 2.0.9 [1,314 B]
Fetched 1,314 B in 0s (3,420 B/s)              
dpkg: warning: files list file for package 'mysql-common' missing; assuming package has no files currently installed
(Reading database ... 230311 files and directories currently installed.)
Removing mysql-server (5.7.37-0ubuntu0.18.04.1) ...
Removing mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
dpkg: dbconfig-mysql: dependency problems, but removing anyway as you requested:
 phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); however:
  Package dbconfig-mysql is to be removed.
  Package dbconfig-no-thanks is not installed.
  Version of dbconfig-common on system is 2.0.9.

Removing dbconfig-mysql (2.0.9) ...
Selecting previously unselected package dbconfig-no-thanks.
dpkg: warning: files list file for package 'mysql-common' missing; assuming package has no files currently installed
(Reading database ... 230233 files and directories currently installed.)
Preparing to unpack .../dbconfig-no-thanks_2.0.9_all.deb ...
Unpacking dbconfig-no-thanks (2.0.9) ...
dpkg: warning: files list file for package 'mysql-common' missing; assuming package has no files currently installed
(Reading database ... 230234 files and directories currently installed.)
Removing openscenegraph-plugin-osgearth (2.9.0+dfsg-1) ...
Removing mysql-workbench (6.3.8+dfsg-1build3) ...
Removing libosgearth-dev (2.9.0+dfsg-1) ...
Removing libmysqlcppconn7v5:amd64 (1.1.9-1) ...
Removing libopenscenegraph-3.4-dev (3.4.1+dfsg1-3) ...
Removing libosgearthsplat5 (2.9.0+dfsg-1) ...
Removing libosgearthqt5-5 (2.9.0+dfsg-1) ...
Removing mysql-client (5.7.37-0ubuntu0.18.04.1) ...
Removing mysql-client-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Removing mysql-client-core-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Removing mysql-server-core-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Removing mysql-utilities (1.6.4-1) ...
Removing mysql-workbench-data (6.3.8+dfsg-1build3) ...
Removing libosgearthutil5 (2.9.0+dfsg-1) ...
Removing libosgearthannotation5 (2.9.0+dfsg-1) ...
Removing libosgearthfeatures5 (2.9.0+dfsg-1) ...
Removing libosgearthsymbology5 (2.9.0+dfsg-1) ...
Removing libosgearth5 (2.9.0+dfsg-1) ...
Removing libopenscenegraph-3.4-131:amd64 (3.4.1+dfsg1-3) ...
Removing libgdal20 (2.2.3+dfsg-2) ...
Removing libmysqlclient20:amd64 (5.7.37-0ubuntu0.18.04.1) ...
Removing mysql-common (5.8+1.0.4) ...
Setting up dbconfig-no-thanks (2.0.9) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
(Reading database ... 227342 files and directories currently installed.)
Purging configuration files for mysql-common (5.8+1.0.4) ...
Purging configuration files for mysql-utilities (1.6.4-1) ...
Purging configuration files for mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Processing triggers for systemd (237-3ubuntu10.53) ...
Processing triggers for ureadahead (0.100.0-21) ...
ureadahead will be reprofiled on next reboot and then I tried to reinstall using following command, I got stat file errors:
 :~$ sudo apt-get install mysql-server mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gdal-data libaec0 libarmadillo8 libarpack2 libatkmm-1.6-1v5 libblas3
  libcairomm-1.0-1v5 libcoin80v5 libctemplate3 libdap25 libdapclient6v5
  libepsilon1 libfreexl1 libfyba0 libgeos-3.6.2 libgeos-c1v5 libgeos-dev
  libgeotiff2 libglibmm-2.4-1v5 libgnome-keyring-common libgnome-keyring0
  libgraphicsmagick-q16-3 libgtkmm-2.4-1v5 libhdf4-0-alt libhdf5-100
  libiso9660-10 libkmlbase1 libkmldom1 libkmlengine1 liblapack3 libmad0
  libmng2 libnetcdf13 libodbc1 libogdi3.2 libopenthreads-dev libopenthreads20
  libpangomm-1.4-1v5 libpq5 libproj12 libqhull7 libspatialite7 libsuperlu5
  libsz2 libtinyxml2.6.2v5 liburiparser1 libvcdinfo0 libvsqlitepp3v5
  libxerces-c3.2 libxine2 libxine2-bin libxine2-doc libxine2-ffmpeg
  libxine2-misc-plugins libxine2-plugins odbcinst odbcinst1debian2 proj-bin
  proj-data python-mysql.connector python-paramiko python-pexpect
  python-ptyprocess python-pyodbc python-pysqlite2
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server-5.7
  mysql-server-core-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-client mysql-client-5.7 mysql-client-core-5.7 mysql-common
  mysql-server mysql-server-5.7 mysql-server-core-5.7
0 upgraded, 7 newly installed, 0 to remove and 12 not upgraded.
Need to get 7,308 B/18.9 MB of archives.
After this operation, 154 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 mysql-common all 5.8+1.0.4 [7,308 B]
Fetched 7,308 B in 0s (23.3 kB/s)       
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 227329 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.8+1.0.4_all.deb ...
Unpacking mysql-common (5.8+1.0.4) ...
Selecting previously unselected package mysql-client-core-5.7.
Preparing to unpack .../mysql-client-core-5.7_5.7.37-0ubuntu0.18.04.1_amd64.deb ...
Unpacking mysql-client-core-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.37-0ubuntu0.18.04.1_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Selecting previously unselected package mysql-server-core-5.7.
Preparing to unpack .../mysql-server-core-5.7_5.7.37-0ubuntu0.18.04.1_amd64.deb ...
Unpacking mysql-server-core-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Setting up mysql-common (5.8+1.0.4) ...
update-alternatives: warning: alternative /etc/mysql/mysql.cnf (part of link group my.cnf) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/my.cnf is dangling; it will be updated with best choice
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mysql-server-5.7.
(Reading database ... 227485 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.37-0ubuntu0.18.04.1_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Selecting previously unselected package mysql-client.
Preparing to unpack .../mysql-client_5.7.37-0ubuntu0.18.04.1_all.deb ...
Unpacking mysql-client (5.7.37-0ubuntu0.18.04.1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.7.37-0ubuntu0.18.04.1_all.deb ...
Unpacking mysql-server (5.7.37-0ubuntu0.18.04.1) ...
Setting up mysql-server-core-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Setting up mysql-client-core-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Setting up mysql-client-5.7 (5.7.37-0ubuntu0.18.04.1) ...
Setting up mysql-client (5.7.37-0ubuntu0.18.04.1) ...
Setting up mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
Cannot stat file /proc/10333/fd/4: Permission denied
Cannot stat file /proc/10333/fd/5: Permission denied
Cannot stat file /proc/10333/fd/14: Permission denied
Cannot stat file /proc/10333/fd/15: Permission denied
Cannot stat file /proc/10333/fd/16: Permission denied
Cannot stat file /proc/10333/fd/17: Permission denied
Cannot stat file /proc/10333/fd/48: Permission denied
Cannot stat file /proc/10333/fd/72: Permission denied
Cannot stat file /proc/10333/fd/87: Permission denied
Cannot stat file /proc/10333/fd/90: Permission denied
Cannot stat file /proc/10333/fd/93: Permission denied
Cannot stat file /proc/10333/fd/96: Permission denied
Cannot stat file /proc/10333/fd/1023: Permission denied
Cannot stat file /proc/10341/fd/5: Permission denied
Cannot stat file /proc/10341/fd/6: Permission denied
Cannot stat file /proc/10341/fd/7: Permission denied
Cannot stat file /proc/10341/fd/8: Permission denied
Cannot stat file /proc/10341/fd/9: Permission denied
Cannot stat file /proc/10341/fd/10: Permission denied
Cannot stat file /proc/10363/fd/3: Permission denied
Cannot stat file /proc/10375/fd/3: Permission denied
Cannot stat file /proc/10375/fd/4: Permission denied
Cannot stat file /proc/10375/fd/7: Permission denied
Cannot stat file /proc/10375/fd/8: Permission denied
Cannot stat file /proc/10375/fd/9: Permission denied
Cannot stat file /proc/10375/fd/10: Permission denied
Cannot stat file /proc/10375/fd/103: Permission denied
Cannot stat file /proc/10377/fd/13: Permission denied
Cannot stat file /proc/10377/fd/14: Permission denied
Cannot stat file /proc/10377/fd/15: Permission denied
Cannot stat file /proc/10377/fd/16: Permission denied
Cannot stat file /proc/10377/fd/17: Permission denied
Cannot stat file /proc/10377/fd/18: Permission denied
Cannot stat file /proc/10377/fd/41: Permission denied
Cannot stat file /proc/10377/fd/103: Permission denied
Cannot stat file /proc/10423/fd/4: Permission denied
Cannot stat file /proc/10423/fd/5: Permission denied
Cannot stat file /proc/10423/fd/11: Permission denied
Cannot stat file /proc/10423/fd/14: Permission denied
Cannot stat file /proc/10423/fd/15: Permission denied
Cannot stat file /proc/10423/fd/16: Permission denied
Cannot stat file /proc/10423/fd/17: Permission denied
Cannot stat file /proc/10423/fd/24: Permission denied
Cannot stat file /proc/10423/fd/48: Permission denied
Cannot stat file /proc/10423/fd/72: Permission denied
Cannot stat file /proc/10423/fd/87: Permission denied
Cannot stat file /proc/10423/fd/90: Permission denied
Cannot stat file /proc/10423/fd/93: Permission denied
Cannot stat file /proc/10423/fd/96: Permission denied
Cannot stat file /proc/10423/fd/1023: Permission denied
Cannot stat file /proc/10424/fd/4: Permission denied
Cannot stat file /proc/10424/fd/5: Permission denied
Cannot stat file /proc/10424/fd/11: Permission denied
Cannot stat file /proc/10424/fd/14: Permission denied
Cannot stat file /proc/10424/fd/15: Permission denied
Cannot stat file /proc/10424/fd/16: Permission denied
Cannot stat file /proc/10424/fd/17: Permission denied
Cannot stat file /proc/10424/fd/24: Permission denied
Cannot stat file /proc/10424/fd/48: Permission denied
Cannot stat file /proc/10424/fd/72: Permission denied
Cannot stat file /proc/10424/fd/87: Permission denied
Cannot stat file /proc/10424/fd/90: Permission denied
Cannot stat file /proc/10424/fd/93: Permission denied
Cannot stat file /proc/10424/fd/96: Permission denied
Cannot stat file /proc/10424/fd/1023: Permission denied
AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld at line 9: Could not open 'abstractions/mysql'
Setting up mysql-server (5.7.37-0ubuntu0.18.04.1) ...
Processing triggers for systemd (237-3ubuntu10.53) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for ureadahead (0.100.0-21) …

I found one soluion at:



	
	
	
	


[h=1][https://askubuntu.com/questions/1393745/uninstalled-and-reinstalled-mysql-on-ubuntiu-18-04-mysqld-not-found](https://askubuntu.com/questions/1393745/uninstalled-and-reinstalled-mysql-on-ubuntiu-18-04-mysqld-not-found)[/h]
Is the solution provided by above link good?
  Somebody please guide me how to solve the mysqld problem.
 Zulfi.

---

### Post by TheFu on 2022-03-03
You told it to purge?  That removes all configs ... like the DB name ... from the system. Ouch.
I don't know the solution, as we stopped using mysql about 9 yrs ago and switched to mariadb + postgres.
But if it were me, I'd ensure my backups from before the mistake were all great and restore them, especially the actually DBs, indexes, and all the settings.  Then I'd try starting again - using systemctl and check that it worked with journalctl.  If it doesn't work, I'd google the exact error messages that journalctl kicked out for a solution.

---

