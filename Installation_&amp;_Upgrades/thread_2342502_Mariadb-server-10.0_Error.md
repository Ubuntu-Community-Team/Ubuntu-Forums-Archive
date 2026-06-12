---
title: "Mariadb-server-10.0 Error"
date: 2016-11-07
forum: Installation &amp; Upgrades
---

### Post by antoinehddd on 2016-11-07
Hello Ubuntu community :) ,

I came here as I am desperate to find a solution for this.
Recently, I installed mysql and mariadb but the error happened:

Everytime I try to install/uninstall/upgrade something (even not related to mariadb) I have this : 

**dpkg: error processing archive mariadb-server-10.0 (--install):**
**cannot access archive: No such file or directory**
**Errors were encountered while processing:**
[B]mariadb-server-10.0

[/B]or **dpkg: error processing package mariadb-server-10.0 (--remove):**
** subprocess installed post-removal script returned error exit status 1**
**Errors were encountered while processing:**
** mariadb-server-10.0**
**E: Sub-process /usr/bin/dpkg returned an error code (1)**




I tried everything :
sudo apt-get remove/clean/purge etc.... 
Nothing is working.

Here is the result of apt-cache search mariadb (maybe it can help...) 
:**dbconfig-common - framework that helps packages to manage databases**
**apophenia-bin - Apophenia Statistical C Library -- binary package**
**apophenia-doc - Apophenia Statistical C Library -- reference manual**
**auth2db - Powerful and eye-candy IDS logger, log viewer and alert generator**
**dbconfig-mysql - dbconfig-common MySQL/MariaDB support**
**libapophenia2 - Apophenia Statistical C Library -- library package**
**libapophenia2-dev - Apophenia Statistical C Library -- development package**
**libmariadb-client-lgpl-dev - MariaDB Client Library for C, development files**
**libmariadb-client-lgpl-dev-compat - MariaDB Client Library for C, compatibility symlinks**
**libmariadb2 - MariaDB Client Library for C**
**libmariadbd-dev - MariaDB embedded database, development files**
**libmariadbd18 - MariaDB embedded database**
**libreoffice-mysql-connector - MariaDB/MySQL Connector extension for LibreOffice**
**libwtdbomysql-dev - MySQL/MariaDB backend for Wt::Dbo [development]**
**libwtdbomysql38 - MySQL/MariaDB backend for Wt::Dbo [runtime]**
**mariadb-client - MariaDB database client (metapackage depending on the latest version)**
**mariadb-client-10.0 - MariaDB database client binaries**
**mariadb-client-core-10.0 - MariaDB database core client binaries**
**mariadb-common - MariaDB common metapackage**
**mariadb-plugin-connect - Connect storage engine for MariaDB**
**mariadb-plugin-mroonga - Mroonga storage engine for MariaDB**
**mariadb-plugin-oqgraph - OQGraph storage engine for MariaDB**
**mariadb-plugin-spider - Spider storage engine for MariaDB**
**mariadb-plugin-tokudb - TokuDB storage engine for MariaDB**
**mariadb-server - MariaDB database server (metapackage depending on the latest version)**
**mariadb-server-10.0 - MariaDB database server binaries**
**mariadb-server-core-10.0 - MariaDB database core server files**
**mariadb-test - MariaDB database regression test suite**
**mariadb-test-data - MariaDB database regression test suite - data files**
**mycli - CLI for MySQL/MariaDB**
**phpmyadmin - MySQL web administration tool**




Any help would be really appreciated,

Cheers,

A

---

### Post by antoinehddd on 2016-11-18
Up ! :)
I am still stuck with this and don't know what to do....

---

