---
title: "mysql-server will not install"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by JvdS45 on 2011-10-26
sudo dpkg --configure mysql-server-5.1
    Instellen van mysql-server-5.1 (5.1.58-1ubuntu1) ...
    apparmor_parser: Regex grouping error: Unclosed grouping or character class, expecting close }
    apparmor_parser: Unable to parse input line '/{,var/run/mysqld/mysqld.pid'
    apparmor_parser: Regex grouping error: Unclosed grouping or character class, expecting close }
    apparmor_parser: Unable to parse input line '/{,var/run/mysqld/mysqld.sock'
    ERROR processing regexs for profile /usr/sbin/mysqld, failed to load
    start: Job failed to start
    invoke-rc.d: initscript mysql, action "start" failed.
    dpkg: fout bij afhandelen van mysql-server-5.1 (--configure):
     subproces installed post-installation script gaf een foutwaarde 1 terug
    Fouten gevonden tijdens behandelen van:
     mysql-server-5.1
     
     
I did uninstalled and re-install it nothing will help :| even configuring mysql will not boot up what can i do? to let work mysql?

---

### Post by raja.genupula on 2011-10-26
Hi try to remove the package with purging 

**sudo apt-get remove --purge <pkg_name>**

and then install it . 

to start the mysql server after installing it do this ...

**sudo /etc/init.d/mysql start**
and to login

**mysql -u root -p **

all the best .

---

