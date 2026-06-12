---
title: "Importing data in mysql?"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by fvs on 2007-08-20
've been trying to import data from a spreadsheet into mysql database,I have it in a cvs form with the right amount of fields as my database, but each time I import into mysql I get an error message,

mysql> load data infile '/home/frank/OpenOffice_Backup/Cus.cvs' into table Custome rs;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '/home /frank/OpenOffice_Backup/Cus.cvs into table Customers' at line 1
mysql> load data infile '/home/frank/OpenOffice_Backup/Cus.cvs' into table Custo mers;
ERROR 13 (HY000): Can't get stat of '/home/frank/OpenOffice_Backup/Cus.cvs' (Err code: 2)
 Any help appreciated. Thanks

---

### Post by eggdeng on 2007-08-21
Have you tried with the local keyword?
```
load data local infile '/home/frank/OpenOffice_Backup/Cus.cvs' into table Customers;
```

---

