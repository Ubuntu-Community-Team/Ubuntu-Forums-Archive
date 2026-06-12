---
title: "Unable to install PHP-Pear MDB2 MySql driver removed by 12.10 install!"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2012-12-19
The 12.10 install deleted almost everything I had already installed on my system so I am forced to manually reinstall everything!  I am at the point of trying to recover the software configuration I had for my Apache server and I cannot get the system to reinstall the MYSql driver for the PEAR MDB2 module:

sudo pear install MDB2_Driver_Mysql
pear/MDB2_Driver_mysql requires PHP extension "mysql"
No valid packages found
install failed

---

### Post by jcobban on 2012-12-19
Ok I figured out this particular one.  I had to add an extra --nodeps keyword to this install.  It then warned me that I hadn't installed php-mysql.

**BUT I WOULDN'T HAVE TO BE DOING ALL THIS IF 12.10 HADN'T THROWN AWAY YEARS OF WORK ON CONFIGURING MY SYSTEM!**

---

