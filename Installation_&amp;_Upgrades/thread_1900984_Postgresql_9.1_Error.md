---
title: "Postgresql 9.1 Error"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by LucasCube on 2011-12-27
I've been getting this error after running this command sudo apt-get install postgrsql

I also am getting it every time I install any other program in the Ubuntu Software Center


Errors were encountered while processing:
 postgresql-9.1
 postgresql
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up postgresql-9.1 (9.1.1-1) ...
 * Starting PostgreSQL 9.1 database server
 * Error: could not exec /usr/lib/postgresql/9.1/bin/pg_ctl /usr/lib/postgresql/9.1/bin/pg_ctl start -D /var/lib/postgresql/9.1/main -l /var/log/postgresql/postgresql-9.1-main.log -s -o  -c config_file="/etc/postgresql/9.1/main/postgresql.conf" : 
   ...fail!
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-9.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-9.1; however:
  Package postgresql-9.1 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured

---

