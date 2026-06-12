---
title: "mysql &amp; php5 have &quot;no installation candidate&quot;"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by theduuuuude on 2008-03-13
I have managed to install apache2 and get a web server running, however I'm having a hard time getting on either php5 or mysql packages installed.

When I use any "sudo apt-get" command to install any php5 or mysql package I get something like:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting apache2-mpm-itk instead of apache2
Package mysql-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql-server has no installation candidate

---

### Post by zvacet on 2008-03-14
**system>admin>software sources>**check all boxes under Ubuntu software and updates tab.Reload. Try to install again.

---

