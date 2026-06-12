---
title: "PHP and mysql module"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by pspeakman on 2010-02-08
Hey, I've upgraded to newest ubuntu and found that mysql didn't work with php when I did so - I'm on a power PC, which has some issues with Flash (i.e. it doesn't work) but everything else has been fine.
I have found many others with this problem and followed all the suggestions but it still doesn't work.

root@ubuntu:/usr/lib/php5/ext# dpkg --list | grep php5-mysql
ii  php5-mysql                            5.2.10.dfsg.1-2ubuntu6                     MySQL module for php5

Tells me that it's installed.
But i still get this:
Fatal error: Call to undefined function mysql_connect() in ....

---

