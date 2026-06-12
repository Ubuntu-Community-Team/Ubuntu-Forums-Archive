---
title: "Apache user &amp; group"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by McHenry on 2006-09-29
When setting file ownership etc what is the user and group that should be used for apache.

For example on Centos I set files to apache:users

Thanks

---

### Post by scxtt on 2006-09-29
by default it's **www-data** - but you can set that via apache2.conf ...
```
:> cat /etc/apache2/apache2.conf | grep www-
User www-data
Group www-data
```

---

