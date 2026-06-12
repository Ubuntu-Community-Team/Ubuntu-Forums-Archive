---
title: "help with software installation"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by nadjulius on 2010-05-04
i am new to ubuntu. i have tried to install some of the software applications like dreamweaver, coldfusion, php and mysql that i have been using on windows 7 , but it has been in vain. any assistant in  this regard is highly welcome. thanks

---

### Post by gzarkadas on 2010-05-04
Open the synaptics package manager (System|Administration|Synaptic Package Manager).

To install mysql type `mysql' in the search box and select the packages:
-- mysql-server
-- mysql-admin (this is to administer the server)

Type `php' in the search box and select the packages:
-- php5

You may also want to install
-- phpmyadmin (administers mysql server from a web interface)

To use php in your box you most probably will also have to install apache. Type this in the search box of the synaptics package manager and select what you want. For dreamweaver and coldfusion I can't help you.

---

### Post by oldos2er on 2010-05-04
Windows software does not run natively on Linux. It may be possible to run some Win apps under wine ([http://www.winehq.org/](http://www.winehq.org/)) but it's probably best to look for Linux software soutions. Php and mysql are in the repositories, fwiw.

---

