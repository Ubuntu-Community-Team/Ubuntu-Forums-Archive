---
title: "MySQL for Ubuntu 12.04"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by netizen99 on 2012-05-03
Dear all,

I have just try net install Ubuntu 12.04 Desktop on a virtualbox in Windows 7 (32bit). It's look ok but I get some issue on MySQL.

I find the package mysql-query-browser is missing. have I do something wrong? Or it have been replaced?

I use python-mysqldb for update data in MySQL but after upgrade. I find part of the script can't work. The part that do a cursor.execute() with statement.
(insert into TABLE (col1, col2, ...) select * from xxx). The command look can run successfully. But I found later nothing is added to the TABLE.

Anyone have similar issue? The same script work when the machine is 11.10 version.

---

### Post by almariado on 2012-05-04
Hi!
mysql-query-browser has been replaced by mysql-workbench
You can istall it from synaptic, just look for "mysql-workbench" package.

Cheers.
João

---

### Post by netizen99 on 2012-05-07
Almariado,

Thanks! I can use the mysql workbench now, but I like the previous mysql query browser more.

I also solved my mysqldb issue, I missed the commit statement. it may because the default table type is changed. Thanks for your help!

---

