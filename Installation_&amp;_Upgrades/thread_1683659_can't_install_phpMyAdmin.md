---
title: "can't install phpMyAdmin"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by ubscott on 2011-02-07
hi, in an effort to fix my recent mysqld.sock file woes, i corrupted phpMyAdmin.  I have reviewed this page:
[https://help.ubuntu.com/community/phpMyAdmin#Installing%20from%20source](https://help.ubuntu.com/community/phpMyAdmin#Installing%20from%20source)

i was never able to install it from either Synaptic or from a command line.  i kept getting this error:
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.2-1ubuntu4.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.2-1ubuntu4.5_i386.deb)
  404  Not Found [IP: 91.189.88.30 80]

i even tried apt-get with the remove option set.  i still got that "failed to fetch" error afterwards.

from the page above, this command executed:
sudo svn checkout [https://phpmyadmin.svn.sourceforge.net/svnroot/phpmyadmin/tags/STABLE/phpMyAdmin](https://phpmyadmin.svn.sourceforge.net/svnroot/phpmyadmin/tags/STABLE/phpMyAdmin) phpMyAdmin
[FONT=Verdana]
unfortunately, i have nothing in this folder:
/phpMyAdmin/config

i have deleted it and recreated it, then set permissions on the folder:
sudo chmod o+rw config

when i try to look at the documention, i see nothing about troubleshooting:
[http://localhost/phpMyAdmin/Documentation.html](http://localhost/phpMyAdmin/Documentation.html)

when i try to run the setup script I get a 404:
[http://localhost/phpMyAdmin/scripts/setup.php](http://localhost/phpMyAdmin/scripts/setup.php)

setup.php has this permission:
drwxr-xr-x 

...
does anyone have any suggestions?  thanks.

[/FONT]

---

### Post by CharlesA on 2011-02-07
What version of Ubuntu are you running?

---

### Post by ubscott on 2011-02-08
Ubuntu 10.04.  thanks.

---

### Post by CharlesA on 2011-02-08
Be sure to update the index before trying to install it:

```
sudo apt-get update && sudo apt-get install phpmyadmin
```

---

### Post by ubscott on 2011-02-08
Charles, thanks!!

i learned how to solve it, what was wrong.  thanks again!

---

### Post by CharlesA on 2011-02-08
Glad you got it fixed, don't forget to mark the thread as solved from thread tools.

---

