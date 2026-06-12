---
title: "java 7 installation problems in ubuntu 11.10"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2013-02-11
hi all
  i have just upgraded my ubuntu to version 11.10

 i followed htis link to install java 7 on ubuntu but i am getting this error


[http://www.liberiangeek.net/2012/03/install-oracle-java-7-jdk-jre-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/03/install-oracle-java-7-jdk-jre-in-ubuntu-11-10-oneiric-ocelot/)

[code]
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libjna-java libswing-layout-java junit4 libgladeui-1-11 libasm3-java libnb-platform-devel-java libfreemarker-java libcommons-compress-java
  javahelp2 libservlet2.4-java liblucene2-java libbindex-java libcobertura-java libfelix-main-java libini4j-java libjline-java libasm2-java
  libcommons-beanutils-java libdb-je-java libswingworker-java libcommons-digester-java libhamcrest-java libjtidy-java
  libfelix-framework-java libjzlib-java libswingx-java libappframework-java libicu4j-java libgnome-desktop-2-17 libnb-javaparser-java
  libnb-svnclientadapter-java libbeansbinding-java libnb-platform12-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up oracle-java7-installer (7u3-0~eugenesan~oneiric4) ...
Downloading...
--2013-02-11 20:35:23--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com... 88.221.95.100, 88.221.94.242
Connecting to download.oracle.com|88.221.95.100|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2013-02-11 20:35:23--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com... 2.18.210.174
Connecting to edelivery.oracle.com|2.18.210.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2013-02-11 20:35:30--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com|88.221.95.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 1.79M=0.003s

2013-02-11 20:35:30 (1.79 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[code]

has anyone encountered similar problems? how to fix it?

w/kindest regards
 marco

---

