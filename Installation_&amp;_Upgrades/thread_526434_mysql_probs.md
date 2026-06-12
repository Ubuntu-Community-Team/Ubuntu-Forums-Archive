---
title: "mysql probs"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by winlinfix on 2007-08-15
apt-get -f remove mysql-server-4.1       
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mailx: Depends: postfix but it is not going to be installed or
                  mail-transport-agent
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


mysqladmin password test123
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!


mysql is not able to start


let me know how to fix

---

