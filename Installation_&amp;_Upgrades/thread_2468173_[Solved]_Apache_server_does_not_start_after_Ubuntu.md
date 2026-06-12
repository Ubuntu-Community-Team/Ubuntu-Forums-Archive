---
title: "[Solved] Apache server does not start after Ubuntu upgrade from 21.04 to 21.10"
date: 2021-10-20
forum: Installation &amp; Upgrades
---

### Post by bern1 on 2021-10-20
Hi, 
Apache2 server does not start after upgrade Ubuntu from 21.04 to 21.10. It is probably due to automatic upgrade php to the newer version
Systemctl gives me a following info:
```
Syntax error on line 146 of /etc/apache2/apache2.conf: Syntax error on line 3 of /etc/apache2/mods-enabled/php7.3.load: Cannot load /usr/lib/apache2/modules/libphp7.4.so into server: /usr/lib/apache2/modules/libphp7.4.so: cannot open shared object file: No such file or directory

```
How could I fix this?

---

### Post by TheFu on 2021-10-20
Did you look at line 3?

Did you read the error?  "No such file or directory" /usr/lib/apache2/modules/libphp7.4.so

So, the file the code wants is missing. It appears to be related to a specific version of php. If the 21.10 version of php is different, then I suspect that the first thing would be to change line 3 to point at the version of the file that the current php has and verify it is installed.  Does that seem reasonable?

What version of php is currently on the system?  I suspect it isn't 7.4.

BTW, you do realize that no production server should be running either 21.04 or 21.10, right?  They should be on 20.04 - the most recent LTS.

---

### Post by bern1 on 2021-10-20
> **TheFu said:**
> Did you look at line 3?

Did you read the error?  "No such file or directory" /usr/lib/apache2/modules/libphp7.4.so

So, the file the code wants is missing. It appears to be related to a specific version of php. If the 21.10 version of php is different, then I suspect that the first thing would be to change line 3 to point at the version of the file that the current php has and verify it is installed.  Does that seem reasonable?

What version of php is currently on the system?  I suspect it isn't 7.4.

BTW, you do realize that no production server should be running either 21.04 or 21.10, right?  They should be on 20.04 - the most recent LTS.

Thanks, 
There is new version of PHP8.0  in the current Ubuntu 21.10.
I've managed to solve my issue. 
In the /etc/apache2/mods-enabled directory there was many syminks among others php7.4.conf and php7.4.load which referenced to the files that did not existed (after upgrade). I've changed the names of this files to php8.0.conf and php8.0.load as well as its linkages and after restart apache2 works fine. 

I'm fine with current no LTS Ubuntu version.

---

