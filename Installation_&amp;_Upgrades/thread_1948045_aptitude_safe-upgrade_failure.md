---
title: "aptitude safe-upgrade failure"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by jfine on 2012-03-27
Hi all. I'm really hoping someone can help. I ran a simple aptitude update then aptitude safe-upgrade and it failed. I tried upgrading packages independently, downgrading, etc. Nothing seems to work. Below is the latest attempt at a safe-upgrade.

```
# aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common apt apt-utils cpp-4.4 cron libfreetype6 libgomp1 libmysqlclient16 libpng12-0 libpq5 libstdc++6 libxml2 mysql-client-5.1 mysql-client-core-5.1 
  mysql-server-5.1 mysql-server-core-5.1 procps python-libxml2 
22 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34.9MB of archives. After unpacking 197kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 52080 files and directories currently installed.)
Preparing to replace libmysqlclient16 5.1.41-3ubuntu12.10 (using .../libmysqlclient16_5.1.61-0ubuntu0.10.04.1_amd64.deb) ...
Unpacking replacement libmysqlclient16 ...
dpkg: error processing /var/cache/apt/archives/libmysqlclient16_5.1.61-0ubuntu0.10.04.1_amd64.deb (--unpack):
 unable to create `/usr/lib/libmysqlclient.so.16.0.0.dpkg-new' (while processing `./usr/lib/libmysqlclient.so.16.0.0'): Invalid argument
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libstdc++6 4.4.3-4ubuntu5 (using .../libstdc++6_4.4.3-4ubuntu5.1_amd64.deb) ...
Unpacking replacement libstdc++6 ...
dpkg: error processing /var/cache/apt/archives/libstdc++6_4.4.3-4ubuntu5.1_amd64.deb (--unpack):
 unable to create `/usr/lib/libstdc++.so.6.0.13.dpkg-new' (while processing `./usr/lib/libstdc++.so.6.0.13'): Invalid argument
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmysqlclient16_5.1.61-0ubuntu0.10.04.1_amd64.deb
 /var/cache/apt/archives/libstdc++6_4.4.3-4ubuntu5.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by sidzen on 2012-03-27
See thread here -- [http://ubuntuforums.org/showthread.php?t=1408490](http://ubuntuforums.org/showthread.php?t=1408490)

---

### Post by jfine on 2012-03-27
Thank you for the quick response but it doesn't seem to be a repository access issue. I don't get any 400 errors when downloading the packages. The errors seem to be problems with processing the .deb or creating files.

---

### Post by jfine on 2012-03-27
Looks like it may have been a filesystem issue. I rebooted did a clean, update, safe-upgrade and everything worked as expected.

---

