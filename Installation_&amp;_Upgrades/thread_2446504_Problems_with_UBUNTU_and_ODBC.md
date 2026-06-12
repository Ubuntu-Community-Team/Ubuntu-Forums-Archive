---
title: "Problems with UBUNTU and ODBC"
date: 2020-07-01
forum: Installation &amp; Upgrades
---

### Post by jbravoaqp33 on 2020-07-01
The problem is that I am unable to implement on a web server (ubuntu18) the enabling for them to connect to Mysql via ODBC I would appreciate any help.
:confused::confused::confused::confused::confused::confused:

---

### Post by TheFu on 2020-07-01
What have you done?
What webapp is being implemented?  Does that webapp not have a native mysql interface?  Probably over 90% of webapps do so ODBC isn't necessary.

---

### Post by SeijiSensei on 2020-07-02
Do you want to write an app that will connect to a database via ODBC?  PHP has support for that: [https://www.php.net/manual/en/ref.uodbc.php](https://www.php.net/manual/en/ref.uodbc.php)

I've never used this so you're on your own. I use PostgreSQL most often and MySQL when forced to do so (hello, wordpress).

Is the MySQL database running on a Windows server?  You might consider migrating it to Linux, then using the MySQL ODBC driver to connect from Windows apps.  I use Access on Windows + PostgreSQL on Linux via the Postgres ODBC driver.

---

