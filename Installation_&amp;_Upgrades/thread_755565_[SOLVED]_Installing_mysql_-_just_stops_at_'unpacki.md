---
title: "[SOLVED] Installing mysql - just stops at 'unpacking'"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by NeoTaoistTechnoPagan on 2008-04-15
I can't get my head around this one - I've tried multiple times and have searched for months - nothing helps.

Here's the output so far:

root@turion64:~# apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.4MB of archives.
After unpacking 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-common 5.0.45-1ubuntu3.3 [56.4kB]
Get:2 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main libmysqlclient15off 5.0.45-1ubuntu3.3 [1867kB]
Get:3 [http://192.168.1.26](http://192.168.1.26) gutsy/main libdbd-mysql-perl 4.004-2 [136kB]
Get:4 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-client-5.0 5.0.45-1ubuntu3.3 [7494kB]
Get:5 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-server-5.0 5.0.45-1ubuntu3.3 [26.8MB]
Get:6 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-server 5.0.45-1ubuntu3.3 [50.4kB]                                                                                                                             
Fetched 36.4MB in 14s (2481kB/s)                                                                                                                                                                                 
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 185367 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.45-1ubuntu3.3_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.004-2_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Setting up mysql-common (5.0.45-1ubuntu3.3) ...
(Reading database ... 185449 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb) ...

And then nothing - it will sit at this point until I press <ctrl><c> to break so of course I get an error:

dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb (--unpack):
 subprocess pre-installation script killed by signal (Interrupt)
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.45-1ubuntu3.3_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then I have to  do a : 

aptitude purge mysql-server mysql

in order for apt-get to work again without complaining that I need to run dpkg -f install.

Why is mysql not working on this system ? (yes, it's a laptop) It's running 32-bit gutsy and I have another gutsy that is a server running websites with mysql just fine. Any suggestions? Is anyone else having this problem?

And BTW - the 192.168.1.26 is my personal local mirror that I maintain in-house, updated nightly with apt-mirror - just in case anyone thought the above output looked odd.

---

### Post by NeoTaoistTechnoPagan on 2008-04-15
I FIXED IT!!!

I dug around and found an error file :  /var/lib/mysql/turion64.err

080311 19:37:31  mysqld started
080311 19:37:31 [ERROR] Fatal error: Can't change to run as user 'mysql' ;  Please check that the user exists!

080311 19:37:31 [ERROR] Aborting

080311 19:37:31 [Note] /usr/sbin/mysqld: Shutdown complete

080311 19:37:31  mysqld ended

So this means that the user 'mysql' was missing.

Added it with:

 useradd -s /sbin/nologin -m -g mysql mysql

and then reinstalled mysql-server:

root@turion64:~# apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.4MB of archives.
After unpacking 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-common 5.0.45-1ubuntu3.3 [56.4kB]
Get:2 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main libmysqlclient15off 5.0.45-1ubuntu3.3 [1867kB]
Get:3 [http://192.168.1.26](http://192.168.1.26) gutsy/main libdbd-mysql-perl 4.004-2 [136kB]
Get:4 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-client-5.0 5.0.45-1ubuntu3.3 [7494kB]
Get:5 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-server-5.0 5.0.45-1ubuntu3.3 [26.8MB]
Get:6 [http://192.168.1.26](http://192.168.1.26) gutsy-updates/main mysql-server 5.0.45-1ubuntu3.3 [50.4kB]                                                                                                                             
Fetched 36.4MB in 16s (2273kB/s)                                                                                                                                                                                 
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 185374 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.45-1ubuntu3.3_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.004-2_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Setting up mysql-common (5.0.45-1ubuntu3.3) ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 185457 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.45-1ubuntu3.3_all.deb) ...
Stopping MySQL database server: mysqld.
Setting up libmysqlclient15off (5.0.45-1ubuntu3.3) ...

Setting up libdbd-mysql-perl (4.004-2) ...
Setting up mysql-client-5.0 (5.0.45-1ubuntu3.3) ...

Setting up mysql-server-5.0 (5.0.45-1ubuntu3.3) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
Checking for corrupt, not cleanly closed and upgrade needing tables..

Setting up mysql-server (5.0.45-1ubuntu3.3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


ALL WORKING!!! YAY!!!
Now off to happy webdevland for me!

---

