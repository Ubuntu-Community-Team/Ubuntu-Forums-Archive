---
title: "[SOLVED] PHP execution problem...."
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by James- on 2008-02-19
I installed :  apache2 php libapache2-mod-php5

when I go to [http://localhost/index.php](http://localhost/index.php)

it asks me if I want to save it... PLEASE HELP!!!


found it:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
> Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. Be sure to clear your browser's cache before testing your site again. 

---

