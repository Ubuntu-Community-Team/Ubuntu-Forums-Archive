---
title: "MySQL 5.0.38 upgrade doesn't work"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by angryfix on 2007-11-05
Hello.

Ubuntu version: 7.04
CPU: AMD64

I recently upgraded MySQL via Synaptic to MySQL version 5.0.38. Once that upgrade completed, MySQL started to act erratically, such that it couldn't recognize SQL that had previously worked with earlier versions of MySQL 5.0.

For example, the following SQL:

SELECT COUNT(*) ct
FROM sumfuncqueryobject sumfuncqueryobject_1 
WHERE sumfuncqueryobject_1.sumFuncLong IN 
(SELECT sumfuncqueryobject_1.sumFuncLong
FROM comfuncqueryobject comfuncqueryobject_2 
GROUP BY sumfuncqueryobject_1.sumFuncLong
HAVING SUM(comfuncqueryobject_2.comFuncLong) = sumfuncqueryobject_1.sumFuncLong)

Generates the following error:

"Reference 'sumFuncLong' not supported (forward reference in item list)"

I'm wondering if upgrading to MySQL 5.0.38 changed settings that altered the SQL mode. Strangely, this doesn't occur on Windows XP with MySQL 5.0.38, which is why I'm wondering if this is Ubuntu specific. Let me know if you have any ideas or need more information. Thanks.

---

