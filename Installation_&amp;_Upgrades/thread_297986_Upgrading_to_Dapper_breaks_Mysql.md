---
title: "Upgrading to Dapper breaks Mysql ?"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by emersony on 2006-11-12
Upgrading to Dapper broke mysql in the following way: 

Mysql-client_4.0.24-10Sarge3_i386 depends on libreadline4 (for libreadline.so.4) however libreadline4 conflicts with readline-common which about a million things now depend on in 
Dapper. 

So, no libreadline4 means no mysql-client? That is without going up to mysql5 which not really looking forward to. 

   In Hoary and Breezy, libreadline4 & libreadline5 happily co-exist without readline-common and mysql runs fine. 	

If anyone has any ideas on getting Mysql back up on Dapper I've really been round the block way too many times on this one. 

Emerson

---

