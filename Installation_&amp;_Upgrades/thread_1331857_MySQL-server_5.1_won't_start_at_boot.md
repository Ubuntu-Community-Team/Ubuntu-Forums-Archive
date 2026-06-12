---
title: "MySQL-server 5.1 won't start at boot"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Fizzdan on 2009-11-19
Hi,

After installing a fresh mythbuntu 9.10 server I have been unsuccessful in being able to get the mysql server to start at boot.

It will start manually with

> sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld
   ...done.
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

> $ sudo update-rc.d mysql defaults
 System start/stop links for /etc/init.d/mysql already exist.


Does anyone know what I have to do to get it going?

---

### Post by cftaupitz on 2009-11-20
I have the same problem, when try the manual start i get fail, i have no mysql at all now.

Also there is no service section in the system menu, that previous version of ubuntu did have.

---

