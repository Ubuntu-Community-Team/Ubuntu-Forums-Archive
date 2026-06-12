---
title: "mysql-server-5.6 on Ubuntu 16.04 LTS xenial"
date: 2018-03-19
forum: Installation &amp; Upgrades
---

### Post by jeking on 2018-03-19
Hi,

I am currently running the following on a Ubuntu 16.04 LTS xenial server:

ii  mysql-client-5.6          5.6.16-1~exp1     amd64             MySQL database client 
ii  mysql-client-5.6          5.6.16-1~exp1     amd64             MySQL database client binaries
in  mysql-common-5.6          <none>            all               (no description available)
ii  mysql-server-5.6          5.6.16-1~exp1     amd64             MySQL database server binaries and system database 
ii  mysql-server-core-5.6     5.6.16-1~exp1     amd64             MySQL database server binaries

The server was recently patched which effectively hosed mysql-common when trying to update to mysql-common-5.7.

iF  mysql-common              5.7.21-0ubuntu0.1 all               MySQL database common files, e.g. /etc/mysql/my.cnf

Looking at the apt-cache policy for mysql-common:

apt-cache show mysql-common
Package: mysql-common
Architecture: all
Version: 5.7.21-0ubuntu0.16.04.1
Multi-Arch: foreign
Priority: optional
Section: database
Source: mysql-5.7
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 181
Provides: mysql-common-5.6
Conflicts: mariadb-server-5.5, mysql-common-5.6, mysql-server-5.5, percona-xtradb-cluster-common-5.5
Breaks: mariadb-common (<< 10.0.20-3~)
Replaces: mariadb-server-5.5, mysql-common-5.6, mysql-server-5.5, percona-xtradb-cluster-common-5.5
Filename: pool/main/m/mysql-5.7/mysql-common_5.7.21-0ubuntu0.16.04.1_all.deb
Size: 15656
MD5sum: 95fcc68e704fc4d527e40d17f3ff35a0
SHA1: a908d1eee1030cc3e22480ca54ce88388e586cfa
SHA256: 5a625083f76f30de312491e567dbb347c65ee940e090304c592b44c41ee90566
Homepage: [http://dev.mysql.com/](http://dev.mysql.com/)
Description-en: MySQL database common files, e.g. /etc/mysql/my.cnf
 MySQL is a fast, stable and true multi-user, multi-threaded SQL database
 server. SQL (Structured Query Language) is the most popular database query
 language in the world. The main goals of MySQL are speed, robustness and
 ease of use.
 .
 This package includes files needed by all versions of the client library,
 e.g. /etc/mysql/my.cnf.
Description-md5: 562d254c602f89e4390e28f6362283c8
Task: lamp-server, kubuntu-desktop, kubuntu-full, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, ubuntustudio-video, ubuntustudio-publishing, ubuntustudio-graphics, ubuntustudio-audio, ubuntu-sdk
Supported: 5y


Package: mysql-common
Priority: optional
Section: database
Installed-Size: 148
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>
Architecture: all
Source: mysql-5.7
Version: 5.7.15-0ubuntu0.16.04.1
Replaces: mariadb-server-5.5, mysql-common-5.6, mysql-server-5.5, percona-xtradb-cluster-common-5.5
Provides: mysql-common-5.6
Conflicts: mariadb-server-5.5, mysql-common-5.6, mysql-server-5.5, percona-xtradb-cluster-common-5.5
Breaks: mariadb-common (<< 10.0.20-3~)
Filename: pool/main/m/mysql-5.7/mysql-common_5.7.15-0ubuntu0.16.04.1_all.deb
Size: 16750
MD5sum: e98f24936e9ec685e49d5a3dae6d3132
SHA1: e6d467db6aed31ae39c550e41ad8708699949cb8
SHA256: 146dd4c7ffe9e78500e7901d1b8185694655dcbaa6d5cb6e3487917601cc6996
Description-en: MySQL database common files, e.g. /etc/mysql/my.cnf
 MySQL is a fast, stable and true multi-user, multi-threaded SQL database
 server. SQL (Structured Query Language) is the most popular database query
 language in the world. The main goals of MySQL are speed, robustness and
 ease of use.
 .
 This package includes files needed by all versions of the client library,
 e.g. /etc/mysql/my.cnf.
Description-md5: 562d254c602f89e4390e28f6362283c8
Multi-Arch: foreign
Homepage: [http://dev.mysql.com/](http://dev.mysql.com/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: lamp-server, kubuntu-desktop, kubuntu-full, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, ubuntustudio-video, ubuntustudio-publishing, ubuntustudio-graphics, ubuntustudio-audio, ubuntu-sdk


Package: mysql-common
Priority: optional
Section: database
Installed-Size: 199
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>
Architecture: all
Source: mysql-5.7
Version: 5.7.11-0ubuntu6
Replaces: mariadb-server-5.5, mysql-common-5.6, mysql-server-5.5, percona-xtradb-cluster-common-5.5
Provides: mysql-common-5.6
Conflicts: mariadb-server-5.5, mysql-common-5.6, mysql-server-5.5, percona-xtradb-cluster-common-5.5
Breaks: mariadb-common (<< 10.0.20-3~)
Filename: pool/main/m/mysql-5.7/mysql-common_5.7.11-0ubuntu6_all.deb
Size: 16596
MD5sum: a4e2affa0151c0322a520cb1937ea19d
SHA1: 7d8f318b34ae078ce4b1105568723d0f1933a0b6
SHA256: 7219d7e040fa7738b06274a673e8944ab4ec9fc84246bcf6799965e1e5f8ffeb
Description-en: MySQL database common files, e.g. /etc/mysql/my.cnf
 MySQL is a fast, stable and true multi-user, multi-threaded SQL database
 server. SQL (Structured Query Language) is the most popular database query
 language in the world. The main goals of MySQL are speed, robustness and
 ease of use.
 .
 This package includes files needed by all versions of the client library,
 e.g. /etc/mysql/my.cnf.
Description-md5: 562d254c602f89e4390e28f6362283c8
Multi-Arch: foreign
Homepage: [http://dev.mysql.com/](http://dev.mysql.com/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: lamp-server, kubuntu-desktop, kubuntu-full, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, ubuntustudio-video, ubuntustudio-publishing, ubuntustudio-graphics, ubuntustudio-audio, ubuntu-sdk

I have a craft cms on this server among some customized apps which require mysql-server-5.6.

How can I adjust the policy so that anytime the server is patched, the proper mysql-common is left in tact? I have searched numerous threads however I can't seem to find the correct thread for the issue I am seeing.

Regards,

John King

---

