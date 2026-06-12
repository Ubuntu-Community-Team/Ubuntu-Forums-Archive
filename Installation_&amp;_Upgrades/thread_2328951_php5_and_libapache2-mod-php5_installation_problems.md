---
title: "php5 and libapache2-mod-php5 installation problems."
date: 2016-06-26
forum: Installation &amp; Upgrades
---

### Post by ororor012 on 2016-06-26
Hello.
I've started developing a website on my local machine, and opened an apache server on it. At some point I messed around with the apache and phpmyadmin configurations, and broke them.
To fix it, I tried to reinstall the apache2, php5 and libapache2-mod-php5 packages (Note: I have the "mysql-server" and "php5-mysql" packages installed already. I'm not removing them since I have a database that I preffer to keep).
So I removed those 3 packeges, and reinstalled apache2. Now, when I type ```
sudo apt-get install php5 libapache2-mod-php5
```, this is the output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.4) ...
dpkg: error processing package libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.6.11+dfsg-1ubuntu3.4~) | libapache2-mod-php5filter (>= 5.6.11+dfsg-1ubuntu3.4~) | php5-cgi (>= 5.6.11+dfsg-1ubuntu3.4~) | php5-fpm (>= 5.6.11+dfsg-1ubuntu3.4~); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.

dpkg: error processing package php5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 libapache2-mod-php5
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Do you know why?
Thanks :D.

---

