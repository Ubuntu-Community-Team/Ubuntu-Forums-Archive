---
title: "MySQL adapter &quot;mysql&quot; is not available: After Upgrade 9.10"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by thammonddoel on 2010-08-17
I receive the infamous:

"Database Error: Unable to connect to the database:The MySQL adapter "mysql" is not available."

after installing 56 package updates (I'd say that's a bit delinquesnt on my part - but it is what it is).

PHP works and has mysql showing in the paths, I can access MySQL and all databases and tables just fine from the console, but even a simple mysql_connect script in a web page returns neither a pass nor a fail - just stares at me.

This is on an InfinitelyVirtual VPS, and everything appears to work just fine except for the mysql adapter not working in Apache. 

Ubuntu is 9.10.
PHP: 5.2.10
MySQL 5.1.37
Apache 2.2.12

Probably a simple permissions thingy, but I can't seem to find where.  Any suggestions?

---

