---
title: "pdo pain in Karmic"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by acc427us on 2010-01-14
Installed php, mysql, etc. Seems OCI is not part of the normal install anymore so I installeed it according to Chez Xavier's excellent post [http://lacot.org/](http://lacot.org/). This included installing a down rev version of Oracle Instant Client.
 
However, I get 
php: symbol lookup error: /usr/lib/php5/20060613+lfs/pdo_mysql.so: undefined symbol: php_pdo_get_dbh_ce
When I try php.
 
After reading, I renamed pdo.ini to pdo.ini.orig to get my MqSql and php back running but I'd really like to get the Oracle connection working as well
 
From other posts, it seems php seems to there are some libraries loaded out of order.
 
Any suggestions?

---

