---
title: "error Installing oracle java 7 on 12.04"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by BigBaka on 2012-06-24
Dear all,

Following this [guide]("http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/") I was installing oracle java 7 and encountered the following errors.

> jvc@CountryRep:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-24 22:44:26--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 96.17.180.153, 96.17.180.138
Connecting to download.oracle.com (download.oracle.com)|96.17.180.153|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-06-24 22:44:27--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.26.22.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.26.22.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-24 22:44:27--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|96.17.180.153|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: './jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  102K=0.05s

2012-06-24 22:44:28 (102 KB/s) - './jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any advice appreciated.

BB

---

### Post by Lyfang on 2012-10-12
Try adding the following repository found from: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) (supports Ubuntu 12.04, 11.10, 11.04 and 10.04): 
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
or
```
sudo rm /var/lib/dpkg/info/oracle-java7-installer* sudo apt-get purge oracle-java7-installer* sudo rm /etc/apt/sources.list.d/*java* sudo apt-get update sudo add-apt-repository ppa:webupd8team/java sudo apt-get update sudo apt-get install oracle-java7-installer
```

Thread can still be useful, applies to Ubuntu 12.04. See also: [Ubuntu 12.04 Java Failed Install]("http://ubuntuforums.org/showthread.php?t=1977483")

---

