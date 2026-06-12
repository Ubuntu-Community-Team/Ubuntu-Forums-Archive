---
title: "Error when try to install mysql 5.1"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by ghsx on 2008-03-27
Hi

I was reading this guide, how to install mysql,  [http://dev.mysql.com/doc/refman/6.0/en/installing-binary.html](http://dev.mysql.com/doc/refman/6.0/en/installing-binary.html) and i got an error in the step 7:

nyuf@nyuf-desktop:/usr/local/mysql$ scripts/mysql_install_db --user=mysql

FATAL ERROR: Could not find /fill_help_tables.sql

If you compiled from source, you need to run 'make install' to
copy the software into the correct location ready for operation.

If you are using a binary release, you must either be at the top
level of the extracted archive, or pass the --basedir option
pointing to that location.

nyuf@nyuf-desktop:/usr/local/mysql$   

Someone can help me plz?

---

### Post by jide on 2008-04-20
Hello, 
I do not if you have solved the problem, if not try nyuf@nyuf-desktop:/usr/local/mysql$ scripts/mysql_install_db --user=mysql --no-defaults

---

