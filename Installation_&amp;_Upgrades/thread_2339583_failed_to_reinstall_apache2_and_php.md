---
title: "failed to reinstall apache2 and php"
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by Amaric on 2016-10-10
Hello, I'm a newbie and I messed up with a server trying to reinstall apache2 and php, I did extensive searches inside this forum and in the interwebs but no solution for similar problems helped me.
At the moment my web server downloads files instead of opening the web pages so i'm trying to clean up my php installation, I think I messed up my package list or php installation.

apt-get install php5

```

# apt-get install php5Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 php5 : Depends: libapache2-mod-php5 (>= 5.3.10-1ubuntu3.25) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.3.10-1ubuntu3.25) but it is not going to be installed or
                 php5-cgi (>= 5.3.10-1ubuntu3.25) but it is not going to be installed or
                 php5-fpm (>= 5.3.10-1ubuntu3.25) but it is not going to be installed
        Depends: php5-common (>= 5.3.10-1ubuntu3.25) but it is not going to be installed
 php5.6-fpm : Depends: php5.6-common (= 5.6.26-1+deb.sury.org~precise+1) but 5.6.26-2+deb.sury.org~precise+1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

apt-get install php

```

# apt-get install phpReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 php : Depends: php7.0 but it is not going to be installed
 php5.6-fpm : Depends: php5.6-common (= 5.6.26-1+deb.sury.org~precise+1) but 5.6.26-2+deb.sury.org~precise+1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

apt-get -f install

```

# apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  php5.6-fpm
Suggested packages:
  php-pear
The following packages will be upgraded:
  php5.6-fpm
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1569 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of php5.6-fpm:
 php5.6-fpm depends on php5.6-common (= 5.6.26-1+deb.sury.org~precise+1); however:
  Version of php5.6-common on system is 5.6.26-2+deb.sury.org~precise+1.
dpkg: error processing php5.6-fpm (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                       Errors were encountered while processing:
 php5.6-fpm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any help will be appreciated.

---

### Post by mastablasta on 2016-10-11
use the purge command in apt get to remove it all and then install form scratch (if you haven't done any major config that is...)

---

### Post by SeijiSensei on 2016-10-11
Installing the [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") package is the most reliable way to make sure all the dependencies are handled correctly.

```
sudo apt-get install lamp-server^
```

The circumflex ("^") is required.

---

