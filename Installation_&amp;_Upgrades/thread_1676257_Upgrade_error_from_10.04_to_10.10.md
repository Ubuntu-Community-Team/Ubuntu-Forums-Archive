---
title: "Upgrade error from 10.04 to 10.10"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by knichel on 2011-01-26
I got some error during the upgrade from 10.04 to 10.10.  After all was said and done, I opened terminal and tried 

sudo apt-get -f install

and got this...
```
knichel@Gumby:~$ sudo apt-get -f install
[sudo] password for knichel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 libgsf-1-common libopal3.6.6 esound-clients libbeagle1 libxcb-render-util0-dev libtelepathy-qt4-0
  libavutil-extra-49 libdns64 liblualib50 libedata-cal1.2-6 podsleuth libdirectfb-extra libmpfr1ldbl libdvbpsi5 unixodbc libx264-85
  libindicator0 cvs libesd0 libmatroska0 libgsf-1-114 libntfs-3g75 libwebkit1.1-cil libpoppler-glib4 hddtemp esound-common
  libappindicator0 libpt2.6.5 libpt2.6.5-plugins liblua50 libboo2.0.9-cil libdirectfb-dev libjpeg62-dev libebml0 libsysfs-dev
  libedataserver1.2-11 libaudiofile0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up apache2.2-common (2.2.16-1ubuntu3.1) ...
activating new config files ...
 done.
ERROR: Module reqtimeout does not exist!
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.16-1ubuntu3.1); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-auth-mysql:
 libapache2-mod-auth-mysql depends on apache2.2-common (>= 2.2.3-3); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-auth-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-itk is not installed.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                  No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
                                                                                         No apport report written because MaxReports is reached already
                  ing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.3-1ubuntu9.3) | libapache2-mod-php5filter (>= 5.3.3-1ubuntu9.3) | php5-cgi (>= 5.3.3-1ubuntu9.3) | php5-fpm (>= 5.3.3-1ubuntu9.3); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on libapache2-mod-php5 | php5-cgi | php5; however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
  Package php5 is not configured yet.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2.2-common
 apache2-mpm-prefork
 libapache2-mod-auth-mysql
 libapache2-mod-php5
 php5
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I fix?

---

### Post by zvacet on 2011-01-29
```
sudo dpkg --configure -a
```

---

