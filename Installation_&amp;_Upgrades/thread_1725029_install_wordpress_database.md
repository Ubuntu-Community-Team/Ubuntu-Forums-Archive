---
title: "install wordpress database"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by mick463 on 2011-04-09
Hi there i am trying to install wordpress on my ubuntu 10.04 (upgraded from 9.04) at the moment i am trying to use this guide [http://www.techkaki.com/2011/04/how-to-install-wordpress-locally-on-ubuntu-10-10-with-lamp/](http://www.techkaki.com/2011/04/how-to-install-wordpress-locally-on-ubuntu-10-10-with-lamp/) when i get to the SET PASSWORD FOR wordpress = PASSWORD(“wordpresspassword”); i get the error 

mysql> SET PASSWORD FOR wordpress = PASSWORD(“wordpresspassword”);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '“wordpresspassword”)' at line 1

what am i doing wrong i can get a web page if i use [http://localhost](http://localhost) which is the IT WORKS page but if i do [http://127.0.0.1/wordpress/](http://127.0.0.1/wordpress/) i get Error establishing a database connection or if i use a certan database that has no password i get you have downloaded a phtml file what do you want firefox to do with it please help i am at a loss.

---

### Post by mrmjtudor on 2011-07-06
Use single quotes ie ' rather than "

---

