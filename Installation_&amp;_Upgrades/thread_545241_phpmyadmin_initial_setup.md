---
title: "phpmyadmin initial setup"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Rick Z on 2007-09-07
Before I start the question…  Here what I did to successfully access localhost/phpmyadmin

Install php5, mysql, and phpmyadmin.
Once the mysql is installed, I create a root user in mysql.

I am able to see everything under the following URL [http://localhost/](http://localhost/)
This should display the Index of / which is what is listed in /var/www I have 2 directories and one php file.

apache2-default
phpmyadmin
testphp.php

Now, I have a question that is related to phpmyadmin initial setup. I went to the phpmyadmin website [http://www.phpmyadmin.net/documentation/#quick_install](http://www.phpmyadmin.net/documentation/#quick_install) and found the following task extremely confused...

cd phpMyAdmin
mkdir config # create directory for saving
chmod o+rw config # give it world writable permissions

Now, Which directory of phpmyadmin are we looking at? Is this under /etc/phpmyadmin, /var/www/phpmyadmin, /var/lib/phpmyadmin, or /usr/share/phpmyadmin???? Maybe there's another directories!!! Well, what I did was that I went to /etc/phpmyadmin/ and did the task as the doc says, but when I refresh the [http://localhost/phpmyadmin/scripts/setup.php](http://localhost/phpmyadmin/scripts/setup.php) the "Configuration" section icon "Save" & "Load" are still gray out. According to the phpmyadmin's doc or book, this should NOT be gray out once you mkdir config and set the premission. I even bought the book Mastering phpMyAdmin 2.8 and the steps are similar, yet I can't get this setup. 

Can anyone please help me to the right direction?

---

