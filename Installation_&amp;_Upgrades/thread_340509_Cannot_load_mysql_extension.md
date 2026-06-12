---
title: "Cannot load mysql extension"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by mukatira on 2007-01-17
After re-installing mysql I am faced with this error when I go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

[COLOR="Red"][SIZE="6"]phpMyAdmin - Error[/SIZE][/COLOR]
Cannot load mysql extension. Please check your PHP configuration. - Documentation

I have followed some instructions from other forms and edited the php.ini file and uncommented  extension=mysql.so and restarted apache

Not sure what else to do now.

Thanks in anticipation

-sm

---

### Post by mukatira on 2007-01-17
Figured it out!

When I use locate to locate mysql.so (to be included in the extension_dir (php.ini), this is the result I get
root@**ubuntu:/# locate mysql.so
/usr/lib/perl5/auto/DBD/mysql/ext/mysql.so
/usr/lib/perl5/auto/DBD/mysql/mysql.so
I tried both the directories in php.ini and the error continued.

Then I used find to find the mysql.so file to be included it in extension_dir (php.in)
root@**ubuntu:/# find / -name 'mysql.so'
find: /proc/18263/task: No such file or directory
find: /proc/18263/fd: No such file or directory
/usr/lib/perl5/auto/DBD/mysql/ext/mysql.so
/usr/lib/perl5/auto/DBD/mysql/mysql.so
**/usr/lib/php5/20051025/mysql.so**
When I use the /usr/lib/php5/20051025/ path to indicate extension_dir [COLOR="Red"]**ALL IS GOOD**[/COLOR]!

Go fligure ..... anyone know why locate was unable to locate /usr/lib/php5/20051025/mysql.so ?

Cheers

-Sm

---

