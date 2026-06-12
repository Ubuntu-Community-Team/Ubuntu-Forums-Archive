---
title: "Unable to install Java8 or Java9"
date: 2017-10-18
forum: Installation &amp; Upgrades
---

### Post by rick-blacker on 2017-10-18
Hi all. Trying to install java
```

sudo add-apt-repository ppa:webupd8team/java
sudo apt update 
sudo apt install oracle-java8-installer

```

This runs the java install but, the install fails, best I can tell, it can't connect to one of the servers to download the proper tar file.  Anyone else have this issue?  Here is what gets sent to the console.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java8-installer is already the newest version (8u144-1~webupd8~0).
0 upgraded, 0 newly installed, 0 to remove and 192 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up oracle-java9-installer (9b181-1~webupd8~2) ...
Using wget settings from /var/cache/oracle-jdk9-installer/wgetrc
Downloading Oracle Java 9...
--2017-10-18 15:56:45--  http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.3.105.48, 23.3.105.51
Connecting to download.oracle.com (download.oracle.com)|23.3.105.48|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz [following]
--2017-10-18 15:56:46--  https://edelivery.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 104.89.90.135, 2600:1409:0:4a0::2d3e, 2600:1409:0:49d::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|104.89.90.135|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz?AuthParam=1508367526_778f4f6d8a666dfe4ad6d79355674541 [following]
--2017-10-18 15:56:46--  http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz?AuthParam=1508367526_778f4f6d8a666dfe4ad6d79355674541
Connecting to download.oracle.com (download.oracle.com)|23.3.105.48|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-10-18 15:56:46 ERROR 404: Not Found.

download failed
Oracle JDK 9 is NOT installed.
dpkg: error processing package oracle-java9-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up oracle-java8-installer (8u144-1~webupd8~0) ...
Using wget settings from /var/cache/oracle-jdk8-installer/wgetrc
Downloading Oracle Java 8...
--2017-10-18 15:56:47--  http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.3.105.48, 23.3.105.51
Connecting to download.oracle.com (download.oracle.com)|23.3.105.48|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz [following]
--2017-10-18 15:56:47--  https://edelivery.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 104.89.90.135, 2600:1409:0:4a0::2d3e, 2600:1409:0:49d::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|104.89.90.135|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508367527_ad49846e42f54dbedbb5880c64507b94 [following]
--2017-10-18 15:56:47--  http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508367527_ad49846e42f54dbedbb5880c64507b94
Connecting to download.oracle.com (download.oracle.com)|23.3.105.48|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-10-18 15:56:47 ERROR 404: Not Found.

download failed
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of default-jre-headless:
 default-jre-headless depends on openjdk-8-jre-headless; however:
  Package openjdk-8-jre-headless is not installed.
  Package oracle-java9-installer which provides openjdk-8-jre-headless is not configured yet.
  Package oracle-java8-installer which provides openjdk-8-jre-headless is not configured yet.

dpkg: error processing package default-jre-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of default-jre:
 default-jre depends on default-jre-headless (= 2:1.8-56ubuntu2); however:
  Package default-jre-headless is not configured yet.
  Version of default-jre-headless on system, provided by oracle-java9-installer:amd64, is <none>.
  Version of default-jre-headless on system, provided by oracle-java8-installer:all, is <none>.
 default-jre depends on openjdk-8-jre; however:
  Package openjdk-8-jre is not installed.
  Package oracle-java9-installer which proNo apport report written because MaxReports is reached already
                                                                                                        No apport report written because MaxReports is reached already
                                                                                                                                                                      vides openjdk-8-jre is not configured yet.
  Package oracle-java8-installer which provides openjdk-8-jre is not configured yet.

dpkg: error processing package default-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of default-jdk-headless:
 default-jdk-headless depends on default-jre-headless (= 2:1.8-56ubuntu2); however:
  Package default-jre-headless is not configured yet.
  Version of default-jre-headless on system, provided by oracle-java9-installer:amd64, is <none>.
  Version of default-jre-headless on system, provided by oracle-java8-installer:all, is <none>.
 default-jdk-headless depends on openjdk-8-jdk-headless; however:
  Package openjdk-8-jdk-headless is not installed.
  Package oracle-java9-installer which provides openjdk-8-jdk-headless is not configured yet.
  Package oracle-java8-installer which provides openjdk-8-jdk-headless is not configured yet.

dpkg: error processing package default-jdk-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of default-jdk:
 default-jdk depends on default-jre (= 2:1.8-56ubuntu2); however:
  Package default-jre is not configured yet.
  Version of default-jre on system, provided by oracle-java9-installer:amd64, is <none>.
  Version of default-jre on system, provided by oracle-java8-installer:all, is <none>.
 default-jdk depends on default-jdk-headless (= 2:1.8-56ubuntu2); however:
  Package default-jdk-headless is not configured yet.
 default-jdk depends on openjdk-8-jdk; however:
  Package openjdk-8-jdk is not installed.
  Package oracle-java9-installer which provides openjdk-8-jdk is not configured yet.
  Package oracle-java8-installer which provides openjdk-8-jdk is not configured yet.

dpkg: error processing package default-jdk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java9-installer
 oracle-java8-installer
 default-jre-headless
 default-jre
 default-jdk-headless
 default-jdk
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by again? on 2017-10-18
See [HERE]("https://ubuntuforums.org/showthread.php?t=2374686&p=13699352#post13699352").

---

