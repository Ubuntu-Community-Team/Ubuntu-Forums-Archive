---
title: "dbconfig/drupal-5.1 require no mysql password"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by giancarlo76 on 2007-09-21
Installing drupal-5.1 on feisty I get an apparently unrecoverable error:

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

I really don't like to have a root account without a password, but I found no way to install drupal other than

```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('');
```

Why dbconfig doesn't prompt me for a password?
Am I missing something?

Thanks,
giancarlo76

---

### Post by Ozeuss on 2007-09-23
this is your mysql root password, not your filesystem ('ubuntu') password, so sudo rules and such do not apply. In mysql you HAVE to have a root password, it not locked. having no password i much worse than having one... so run the SET PASSWORD again with  a strong password. if its only for testing purposes, make apache listen to localhost only (howto in the ubuntu wiki).
in addition, you probably want a different user for drupal: 
```
mysql> CREATE DATABASE drupal; 
mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON drupal.* TO 'drupalu'@'localhost' IDENTIFIED BY 'drupalp'; 
```
that will create the database and user (you can change their names and the pasword of course). these are the minimum privileges for drupal.

enjoy drupal, it's great!

---

