---
title: "packages and dependencies issue. not even able to setup lamp :("
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by saffrongeek on 2011-12-20
Hi ,

     When I attempt to install LAMP on Ubuntu 11.10 oneiric, I get the following dependency issue.
harish@harish-Inspiron-N4010:~$ sudo apt-get install apache2 mysql-server mysql-admin mysql-query-browser mysql-client mysql-navigator php5 libapache2-mod-php5 php5-gd php5-mysql php5-cli  php5-curl kcachegrind  php5-ffmpeg php5-mcrypt php5-imagick php5-xdebug phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'mysql-cluster-server-5.1' instead of 'mysql-server'
Note, selecting 'mysql-cluster-client-5.1' instead of 'mysql-client'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.20-1ubuntu1.1) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.20-1ubuntu1.1) but it is not going to be installed or
                    apache2-mpm-event (= 2.2.20-1ubuntu1.1) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.20-1ubuntu1.1) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.20-1ubuntu1.1) but it is not going to be installed
 kcachegrind : Depends: kde-runtime but it is not going to be installed
               Depends: libkdecore5 (>= 4:4.4.0) but it is not going to be installed
               Depends: libkdeui5 (>= 4:4.3.4) but it is not going to be installed
               Depends: libkio5 (>= 4:4.3.4) but it is not going to be installed
               Depends: libqt4-qt3support (>= 4:4.5.3) but it is not installable
               Recommends: valgrind but it is not installable
               Recommends: graphviz but it is not installable
 libapache2-mod-php5 : Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed or
                                apache2-mpm-itk but it is not going to be installed
                       Depends: apache2.2-common but it is not going to be installed
 mysql-admin : Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not installable
 mysql-cluster-client-5.1 : Conflicts: libmysqlclient16 but 5.1.58-1ubuntu1 is to be installed
 mysql-navigator : Depends: libqt3-mt (>= 3:3.3.8-b) but it is not installable
 mysql-query-browser : Depends: libgnome2-0 (>= 2.17.3) but it is not installable
                       Depends: libgtkhtml3.14-19 (>= 1:3.30.2) but it is not installable
                       Depends: libgtkhtml3.14-19 (< 1:3.33) but it is not installable
                       Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not installable
 php5-curl : Depends: libcurl3 (>= 7.16.2-1) but it is not installable
 php5-ffmpeg : Depends: libavcodec53 (>= 4:0.7-1) but it is not installable or
                        libavcodec-extra-53 (>= 4:0.7-1) but it is not going to be installed
               Depends: libavformat53 (>= 4:0.7-1) but it is not installable or
                        libavformat-extra-53 (>= 4:0.7-1) but it is not going to be installed
 php5-imagick : Depends: libmagickcore3 (>= 7:6.6.2.6) but it is not installable
                Depends: libmagickwand3 (>= 7:6.6.2.6) but it is not installable
 phpmyadmin : Depends: dbconfig-common but it is not installable
E: Unable to correct problems, you have held broken packages.
harish@harish-Inspiron-N4010:~$ 

Was anyone able to install LAMP. I am not able to install synaptic nor aptitude package manager as these also get dependency issues.

Other information about my OS and Kernel versions:
harish@harish-Inspiron-N4010:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

harish@harish-Inspiron-N4010:~$ uname -a
Linux harish-Inspiron-N4010 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

I am getting no idea what could be the issue. Request your help and thanks in advance.

Regards

Harish

---

### Post by oldos2er on 2011-12-20
Have you run ```
sudo apt-get update
``` lately?

---

