---
title: "Is there a way I can copy my MYSQL database to USB drive?"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by ayet on 2010-02-13
Iam always working from 1 machine to another even with my laptop which i dont place all my data some of which in some machine, iam always constantly saving all my files specially my MYSQL database files which have grown in size, Is there a ways I can just copy & paste my MYSQL database? like in MSACCESS.

---

### Post by DaithiF on 2010-02-13
use mysqldump to 'copy' and mysql to 'paste', so
```
mysqldump -u username -ppassword databasename > /path/to/usbdrive/database.dump

```and then on laptop:
```
mysql -u username -ppassword < /path/to/usbdrive/database.dump

```

---

### Post by ayet on 2010-02-15
the mysqldump worked but when i used ```
mysql -u username -ppassword < /path/to/usbdrive/database.dump
```
an error occured
ERROR 1046 (3D000) at line 22: No database selected
i checked the path i saved the database.dump and its correct, what seems to be the problem here?

---

### Post by DaithiF on 2010-02-15
add the database name parameter on the restore command:

```
mysql -u username -ppassword -D databasename < /path/to/usbdrive/database.dump
```

it is sometimes cleaner to drop and recreate a database entirely when restoring, to do this you change the commands as follows:

```
mysqldump --add-drop-database -h host -u user -ppassword --databases databasename > /path/to/somewhere/database.dump

```and
```
mysql -h host -u user -ppassword < /path/to/somewhere/database.dump

```

---

### Post by ayet on 2010-02-15
nice.. tnks, it worked :popcorn:

---

