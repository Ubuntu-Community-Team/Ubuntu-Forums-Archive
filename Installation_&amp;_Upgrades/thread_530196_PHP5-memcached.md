---
title: "PHP5-memcached"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by taholder on 2007-08-20
I have been following a tutorial here to get Memcached installed on the 7.04 version of ubuntu. The tutorial can be found here [http://pecl.php.net/bugs/bug.php?id=10541](http://pecl.php.net/bugs/bug.php?id=10541)

Everything's gone fairly smootly (once I installed GCC) but I've now run in to a known bug trying to install the PECL php5-memcached module. The details of the bug are here: [http://pecl.php.net/bugs/bug.php?id=10541](http://pecl.php.net/bugs/bug.php?id=10541)

The problem is, a number of places around the net say it's easy to solve using a symlink from as follows:

ln -s /usr/include/php5 /usr/include/php

The trouble is, I've done this exactly as it says, and I still get exactly the same error "Cannot find
php_session.h"

Any help is greatly appreciated as I spent many hours on this over the weekend, however, I am a total linux noob so please use kid gloves :)

---

