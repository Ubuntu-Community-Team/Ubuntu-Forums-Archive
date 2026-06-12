---
title: "What happened to libphp4.so?"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by zan0416 on 2008-01-22
I recently upgraded from 6.06 all the way to 7.10, and before the upgrade (on 6.06) I had apache/php4/mysql running a simple localhost testbed without any problems.  

Now I see apache has been replaced by apache2 in the Ubuntu upgrade process.  When I try to start apache2, I get the following error:

apache2: Syntax error on line 183 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php4.load: Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory

Looks like it can't find libphp4.so.  What am I missing?  

(Interestingly, when looking at the Ubuntu repos, I don't see much support of php4 or php in general, especially when compared to the debian repos.)   

Dan

---

