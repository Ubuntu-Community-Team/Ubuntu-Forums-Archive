---
title: "Can not install MySql 5.6 Ubuntu 16.04"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by ender7 on 2016-04-21
Hi,

First of all, I need to install MySql 5.6 not 5.7.

System: Dell Inspiron 7559 Ubuntu 16.04 Intel 6700HQ.

Before installation, I try to remove all MySql related files and configs:
[http://askubuntu.com/questions/640899/uninstall-mysql-completely](http://askubuntu.com/questions/640899/uninstall-mysql-completely)
[http://askubuntu.com/questions/172514/how-do-i-uninstall-mysql](http://askubuntu.com/questions/172514/how-do-i-uninstall-mysql)
[http://stackoverflow.com/questions/25244606/completely-remove-mysql-ubuntu-14-04-lts](http://stackoverflow.com/questions/25244606/completely-remove-mysql-ubuntu-14-04-lts)

I am following these instructions as I always do [https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/).
I use this ```
mysql-apt-config_0.7.2-1_all.deb]
``` for configuration suggested in this page [https://dev.mysql.com/downloads/repo/apt/](https://dev.mysql.com/downloads/repo/apt/)

Sometimes it says your version is not supported please select your distribution. Trusty Tahr etc. What should I select? Should I add the proper PPA to look at this repository?
During the configuration, it allows me to select the version of MySql. Even I choice 5.6 it installs 5.7.
Default installation commend: ```
d: **sudo apt-get install mysql-server**
``` &#305; tried it with version ```
**sudo apt-get install mysql-server-5.6**
``` gives me this:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package mysql-server-5.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mysql-community-server:i386 mysql-common:i386 mysql-community-server mysql-common
  percona-xtradb-cluster-server-5.6:i386 percona-server-server-5.6:i386 mysql-testsuite-5.7:i386
  mariadb-server-10.0:i386 percona-xtradb-cluster-server-5.6 percona-server-server-5.6
  mysql-testsuite-5.7 mariadb-server-10.0 mysql-server-core-5.7:i386 mysql-server-5.7:i386
  mysql-server-core-5.7 mysql-server-5.7


E: Package 'mysql-server-5.6' has no installation candidate
```

This was the way how I install MySql but in this case, I can not install what I want. Any help appreciated.

---

### Post by ender7 on 2016-04-24
ANSWER:

16.04 default packages do not containMySQLl 5.6.
Workaround that work for me is that I added 14.04 repositorys and I run these commends:
```
sudo apt-get install mysql-server-5.6
sudo apt-get install mysql-client-5.6
```

If there were dependency problems try to run ```
sudo apt-get -f install
```

Hope it helps someone.

---

