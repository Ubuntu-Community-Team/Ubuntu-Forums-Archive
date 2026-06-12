---
title: "java error during upgrade"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by oren tal on 2012-06-09
whenever I do sudo apt-get upgrade , I get the following error:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-09 22:00:20--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 80.239.148.26, 80.239.148.17
Connecting to download.oracle.com (download.oracle.com)|80.239.148.26|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-06-09 22:00:20--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 95.101.14.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|95.101.14.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-06-09 22:00:21--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|80.239.148.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 3.49M=0.001s

2012-06-09 22:00:21 (3.49 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
[B]Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
```
how can I solve this?

---

### Post by zvacet on 2012-06-12
```
sudo dpkg --configure -a
```

---

