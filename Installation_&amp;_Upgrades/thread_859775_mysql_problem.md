---
title: "mysql problem"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-07-14
I try to add a new user (abc), who should use a certain database (xyz)

I tried it with phpmyadmin:

A
==
1. I created an empty database xyz (main page of phpmyadmin)
2. I added a new user on the Privileges page with:
User: abc
Host: Any (%)
Password: (yes)
Global privileges:
   (Data:) SELECT, INSERT, UPDATE, DELETE, FILE
   (Structure:) CREATE, ALTER, INDEX, DROP, CREATE TEMPORARY TABLES
   (Administration:)    (nothing ticked)
   (Resource limits:)   (nothing ticked)

What does it mean so far? Can the user abc already access data of any
database? I guess no.)

B
==
I found "Database-specific privileges" for the user abc, where I added
the database xyz and ticked:
   (Data:) SELECT, INSERT, UPDATE, DELETE
   (Structure:) CREATE, ALTER, INDEX, DROP, CREATE TEMPORARY TABLES
   (Administration:)    (nothing ticked)

What confuses me is that I have already some databases setup for my own
web, but none of the users has "B" attached.
Currently I am going away from a single person using the database to
allow others also to use the database.



Trying to login (after Flush Privileges) on the commandline:

mysql -u abc -p xyz
and typing in the password of abc
I get a:
ERROR 1045 (28000): Access denied for user 'abc'@'localhost' (using password: YES)



I tried than to use the GRANT statement in mysql:
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, FILE, INDEX, ALTER, CREATE TEMPORARY TABLES ON detteweb.* TO "abc"@"%"IDENTIFIED BY "mypassword";
FLUSH PRIVILEGES;

with the same result: user abc cannot login to the database.

What do I miss?

bye

R.

---

### Post by cdtech on 2008-07-14
You need to grant privileges in this manor (using the command line):

You have to run MySQL as a user that has the permission to do so. By default, MySQL is installed with a root account with these permissions. **Typically** this account has no password when connecting from the localhost unless you altered this.

```
mysql -u root

-> grant all privileges on somedb.* to someusr@"localhost" identified by 'passwrd';
```

The .* indicates that this user will be permitted to work with all of the tables within the database **somedb**

someusr@"localhost"

The someusr is the username that is being created. The portion after the @ indicates the host from which this user is allowed to connect. In this case, this user can only connect from the localhost.

passwrd

The password to be used by the user.

**Or ::.**

```
mysql> grant all privileges on *.* to someusr@"%"
> identified by 'passwrd';
```

*.*

The user will be permitted to connect to all of the MySQL databases and all of the tables contained in those databases.

someusr@"%"

The user may connect to the database from any host or IP number.

Hope this helps......

---

