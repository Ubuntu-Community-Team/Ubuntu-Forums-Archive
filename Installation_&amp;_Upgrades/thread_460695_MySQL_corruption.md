---
title: "MySQL corruption"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Pollywoggy on 2007-05-31
I am getting these errors in Feisty and I did not mess with the maintenance account:


/usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) when trying to connect

 Improperly closed tables are also reported if clients are accessing
 the tables *now*. A list of current connections is below.


That is the error but it does not show any current connections
Is there a fix?

---

### Post by Pollywoggy on 2007-06-01
> **Pollywoggy said:**
> I am getting these errors in Feisty and I did not mess with the maintenance account:


/usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) when trying to connect

 Improperly closed tables are also reported if clients are accessing
 the tables *now*. A list of current connections is below.


That is the error but it does not show any current connections
Is there a fix?

It appears that my database for Postfix caused the problem.  I changed the password in /etc/mysql/debian.cnf and then set the password for the debian-sys-maint user from within MySQL so that it matches the one in debian.cnf

I also fixed the corrupted mysql database and the error messages have disappeared.

---

