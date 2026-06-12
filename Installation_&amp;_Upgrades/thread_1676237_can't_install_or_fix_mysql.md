---
title: "can't install or fix mysql"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by ubscott on 2011-01-26
hi,
in an effort to solve my much-discussed mysqld.sock file problem i tried to reinstall mysql.  Now my installation is messed up, and I can't figure out how to fix it.

here's my mysqld.sock file issue:
[http://ubuntuforums.org/showthread.php?p=10391165](http://ubuntuforums.org/showthread.php?p=10391165)

if i run this command:
sudo dpkg-reconfigure mysql-server

I get:
/usr/sbin/dpkg-reconfigure: mysql-server is not installed

so, i guess i'll reinstall it:
apt-get install mysql-server-5.1

I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.1 is already the newest version.
The following packages were automatically installed and are no longer required:
  mysql-client wwwconfig-common libx264-67 libjs-mootools javascript-common
  dbconfig-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Not upgraded?  I don't understand why. the message seems to indicate that mysql-server is already installed.  However, i can't reconfigure it because apparently it isn't installed.

if i try this:
udo mysqladmin -u root password mypass port=3306

i get:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

...so, I already have it installed, can't reconfigure it and can't set the root password.

does anyone have any ideas?  thanks.

---

