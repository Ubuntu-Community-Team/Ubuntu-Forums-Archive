---
title: "successful installing packages but dpkg has error"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by amerllica on 2014-07-15
Hello Ubuntu users, happy Ramadan

  I'm live in Iran and Some corporation ban us like ORACLE

  so I installed Oracle Java SDK 8 manually and after it my "dpkg" has been showing error always.

  no different between installation packages. each packages from  "Ubuntu Software Center" or "apt-get" install successfully but some  error has been shown and I'm very confused and angry

  somebody tell me what's wrong in my Ubuntu?

  the error is:

```
Package Operation Failed
The  installation or removal of a software package failed
------------------------------------------------------------------
Details
------------------------------------------------------------------
installArchives() failed: Selecting previously unselected package gnome-hearts. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 238764 files and directories currently installed.) 
Preparing to unpack .../gnome-hearts_0.3-2.1ubuntu1_amd64.deb ... 
Unpacking gnome-hearts (0.3-2.1ubuntu1) ... 
Processing triggers for man-db (2.6.7.1-1) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for mime-support (3.54ubuntu1) ... 
Setting up oracle-java7-installer (7u60-0~webupd8~0) ... 
Downloading Oracle Java 7... 
--2014-07-15 14:57:49--  http://download.oracle.com/otn-pub/java/jdk/7u60-b19/jdk-7u60-linux-x64.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 82.178.158.11, 82.178.158.24 
Connecting to download.oracle.com (download.oracle.com)|82.178.158.11|:80... connected. 
HTTP request sent, awaiting response... 403 Forbidden 
2014-07-15 14:57:51 ERROR 403: Forbidden. 
 
download failed 
Oracle JDK 7 is NOT installed. 
dpkg: error processing package oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up oracle-java8-installer (8u5-1~webupd8~3) ... 
Downloading Oracle Java 8... 
--2014-07-15 14:57:52--  http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 82.178.158.24, 82.178.158.11 
Connecting to download.oracle.com (download.oracle.com)|82.178.158.24|:80... connected. 
HTTP request sent, awaiting response... 403 Forbidden 
2014-07-15 14:57:52 ERROR 403: Forbidden. 
 
download failed 
Oracle JDK 8 is NOT installed. 
dpkg: error processing package oracle-java8-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of oracle-java8-set-default: 
 oracle-java8-set-default depends on oracle-java8-installer; however: 
  Package oracle-java8-installer is not configured yet. 
 
dpkg: error processing package oracle-java8-set-default (--configure): 
 dependency problems - leaving unconfigured 
Setting up gnome-hearts (0.3-2.1ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
Processing triggers for python-support (1.0.15) ... 
Errors were encountered while processing: 
 oracle-java7-installer 
 oracle-java8-installer 
 oracle-java8-set-default 
Error in function:  
Setting up oracle-java7-installer (7u60-0~webupd8~0) ... 
Downloading Oracle Java 7... 
--2014-07-15 14:57:55--  http://download.oracle.com/otn-pub/java/jdk/7u60-b19/jdk-7u60-linux-x64.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 82.178.158.11, 82.178.158.24 
Connecting to download.oracle.com (download.oracle.com)|82.178.158.11|:80... connected. 
HTTP request sent, awaiting response... 403 Forbidden 
2014-07-15 14:57:57 ERROR 403: Forbidden. 
 
download failed 
Oracle JDK 7 is NOT installed. 
dpkg: error processing package oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up oracle-java8-installer (8u5-1~webupd8~3) ... 
Downloading Oracle Java 8... 
--2014-07-15 14:57:58--  http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 82.178.158.24, 82.178.158.11 
Connecting to download.oracle.com (download.oracle.com)|82.178.158.24|:80... connected. 
HTTP request sent, awaiting response... 403 Forbidden 
2014-07-15 14:57:58 ERROR 403: Forbidden. 
 
download failed 
Oracle JDK 8 is NOT installed. 
dpkg: error processing package oracle-java8-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of oracle-java8-set-default: 
 oracle-java8-set-default depends on oracle-java8-installer; however: 
  Package oracle-java8-installer is not configured yet. 
 
dpkg: error processing package oracle-java8-set-default (--configure): 
 dependency problems - leaving unconfigured 

```

---

### Post by TheFu on 2014-07-15
As a US company, Oracle is required by law to prevent downloads to Iran (and other countries the government has deemed hostile). That is why the 
> HTTP request sent, awaiting response... 403 Forbidden 
2014-07-15 14:57:51 ERROR 403: Forbidden. 
is seen.

Installing any package outside the package manager can/often will cause dependency issues. If not at the installation time, later.  These other packages from .deb files sometimes lock outdated packages which prevent more and more packages from being updated/fixed over time.  The best solution that I know to attempt to resolve these things is to remove the manually installed .deb files, then use **aptitude** to find a workable dependency resolution.  Until the .deb packages manually installed are removed, it won't be solved without huge, huge, huge, manual effort - if that is even possible.

---

### Post by Nistegmos on 2014-07-15
Hello, I don't have much to add to this thread, except my condolences.  I am an American, but I know that not all Iranians are hostile of course.  Too bad government actions are tricky.  Happy Ramadan and especially peace to any Iranians who are B'hai too.  I used to have some B'hai friends here in USA.  (B'hai is an Iranian-originating world religion with very peaceful ethics).  I hope you find a solution to your software problems.  

And thanks, TheFu, for your reply also, because you inadvertently answered my question from a different thread.  I wanted to install Wine v1.7 manually and offline, but I got wierd dependency errors that didn't make any sense to me and I can't find any proper instructions anywhere.  Your warning is helpful so I don't end up messing up my system which doesn't have internet access.

---

