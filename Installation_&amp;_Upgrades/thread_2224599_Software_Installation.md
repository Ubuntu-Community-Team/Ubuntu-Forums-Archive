---
title: "Software Installation"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by anandarup on 2014-05-17
I had installed LAMP, and then installed Moodle in Ubuntu 13.10. After upgrading to 14.04 I encountered issue with LAMP, then I decided to do away with both LAMP and Moodle. I believe the uninstall didn't happen properly. Now whenever I try to install a software it throws an error. This even happens when I run sudo apt-get update or sudo apt-get upgrade. The following error message is shown

Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I rectify the same? Please guide. 

TIA

---

### Post by Ubi_one_2014 on 2014-05-17
whay shows dpkg -s moodle

---

### Post by anandarup on 2014-05-17
Running dpkg -s moodle 

Package: moodle
Status: install ok half-configured
Priority: optional
Section: web
Installed-Size: 113134
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2.5.4-1ubuntu1
Config-Version: 2.5.2-1
Replaces: moodle-book (<< 1.6.3-2~)
Depends: libapache2-mod-php5 | php5-cgi, php5-mysql | php5-pgsql, php5-gd, php5-curl, php5-cli, apache2 | httpd, ucf, postgresql-client | mysql-client | virtual-mysql-client, dbconfig-common, libphp-phpmailer, libphp-adodb, php-htmlpurifier, libphp-pclzip
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Recommends: postgresql | mysql-server | virtual-mysql-server, php5-ldap, php5-xmlrpc, aspell, mimetex
Suggests: clamav
Breaks: moodle-book (<< 1.6.3-2~)
Conffiles:
 /etc/cron.d/moodle b3b12610081ca3aadd996adce098b5f4
Description: course management system for online learning
 Moodle (Modular Object-Oriented Dynamic Learning Environment) is a course
 management system - a software package designed to help educators create
 quality online courses. One of the main advantages of Moodle over other
 systems is a strong grounding in social constructionist pedagogy.
Homepage: [http://www.moodle.org/](http://www.moodle.org/)
Original-Maintainer: Moodle Packaging Team <pkg-moodle-maintainers@lists.alioth.debian.org>



> **Ubi_one_2014 said:**
> whay shows dpkg -s moodle

---

### Post by Ubi_one_2014 on 2014-05-17
> **anandarup said:**
> I believe the uninstall didn't happen properly. Now whenever I try to install a software it throws an error.



> **anandarup said:**
> Running dpkg -s moodle 

Package: moodle
Status: install ok half-configured
Priority: optional
Section: web
Installed-Size: 113134
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2.5.4-1ubuntu1
Config-Version: 2.5.2-1
Replaces: moodle-book (<< 1.6.3-2~)
Depends: libapache2-mod-php5 | php5-cgi, php5-mysql | php5-pgsql,  php5-gd, php5-curl, php5-cli, apache2 | httpd, ucf, postgresql-client |  mysql-client | virtual-mysql-client, dbconfig-common, libphp-phpmailer,  libphp-adodb, php-htmlpurifier, libphp-pclzip
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Recommends: postgresql | mysql-server | virtual-mysql-server, php5-ldap, php5-xmlrpc, aspell, mimetex
Suggests: clamav
Breaks: moodle-book (<< 1.6.3-2~)
Conffiles:
 /etc/cron.d/moodle b3b12610081ca3aadd996adce098b5f4
Description: course management system for online learning
 Moodle (Modular Object-Oriented Dynamic Learning Environment) is a course
 management system - a software package designed to help educators create
 quality online courses. One of the main advantages of Moodle over other
 systems is a strong grounding in social constructionist pedagogy.
Homepage: [http://www.moodle.org/](http://www.moodle.org/)
Original-Maintainer: Moodle Packaging Team <pkg-moodle-maintainers@lists.alioth.debian.org>.


apt-get remove moodle

---

### Post by anandarup on 2014-05-17
Thanks. It worked.

---

### Post by Ubi_one_2014 on 2014-05-17
nice, :guitar:

---

