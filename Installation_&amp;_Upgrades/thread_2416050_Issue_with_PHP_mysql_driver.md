---
title: "Issue with PHP mysql driver"
date: 2019-04-04
forum: Installation &amp; Upgrades
---

### Post by tbaror on 2019-04-04
Hello All,

I have Ubuntu 18.04 server running with apache2 and application Mysql based probably since update  i have issue with php Msql driver , and i cant find a way to resolve it uninstall reinstall the driver still having same issue .
When i run command shown below i get  following output any idea how to fix it ?
Please advice
Thanks

 ```
php --ini | grep "Loaded"
PHP Warning:  PHP Startup: Unable to load dynamic library 'pdo_mysql' (tried: /usr/lib/php/20180731/pdo_mysql (/usr/lib/php/20180731/pdo_mysql: cannot open shared object file: No such file or directory), /usr/lib/php/20180731/pdo_mysql.so (/usr/lib/php/20180731/pdo_mysql.so: undefined symbol: mysqlnd_allocator)) in Unknown on line 0
Loaded Configuration File:         /etc/php/7.3/cli/php.ini
```

---

### Post by SeijiSensei on 2019-04-04
Did you install the php7.3-mysql module?

Try creating a file in the root of the website with just the single line "<?php phpinfo() ?>".  Now access that file from a browser, and you will see a complete list of all the various PHP modules in use.  What do you see for MySQL?

---

