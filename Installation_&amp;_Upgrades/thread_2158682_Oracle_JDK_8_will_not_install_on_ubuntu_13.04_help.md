---
title: "Oracle JDK 8 will not install on ubuntu 13.04 help is needed"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2013-06-30
I have trian to install java oracle jdk8 but no matter how I get the following errors:
--------------------------------------------------------------------------------------------------
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java8-installer (8b94-0~webupd8~3) ...
Downloading Oracle Java 8...
--2013-06-30 08:57:49--  [http://www.java.net/download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz](http://www.java.net/download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz)
Resolving [www.java.net](www.java.net) ([www.java.net](www.java.net))... 209.189.227.38
Connecting to [www.java.net](www.java.net) ([www.java.net)|209.189.227.38|:80](www.java.net)|209.189.227.38|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://www.java.net//download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz](https://www.java.net//download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz) [following]
--2013-06-30 08:57:49--  [https://www.java.net//download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz](https://www.java.net//download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz)
Connecting to [www.java.net](www.java.net) ([www.java.net)|209.189.227.38|:443](www.java.net)|209.189.227.38|:443)... connected.
WARNING: cannot verify [www.java.net's](www.java.net's) certificate, issued by ‘/C=US/O=Oracle Corporation/OU=VeriSign Trust Network/OU=Class 3 MPKI Secure Server CA/CN=Oracle SSL CA’:
  Unable to locally verify the issuer's authority.
HTTP request sent, awaiting response... 303 See Other
Location: [http://download.java.net/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz?q=download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz](http://download.java.net/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz?q=download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz) [following]
--2013-06-30 08:57:50--  [http://download.java.net/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz?q=download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz](http://download.java.net/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz?q=download/jdk8/archive/b94/binaries/jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz)
Resolving download.java.net (download.java.net)... 137.254.120.26
Connecting to download.java.net (download.java.net)|137.254.120.26|:80... connected.
HTTP request sent, awaiting response... 416 Requested range not satisfiable

    The file is already fully retrieved; nothing to do.

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-8-ea-bin-b94-linux-x64-13_jun_2013.tar.gz
Oracle JDK 8 is NOT installed.
dpkg: error processing oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-java8-set-default:
 oracle-java8-set-default depends on oracle-java8-installer; however:
  Package oracle-java8-installer is not configured yet.

dpkg: error processing oracle-java8-set-default (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                     Errors were encountered while processing:
 oracle-java8-installer
 oracle-java8-set-default
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

