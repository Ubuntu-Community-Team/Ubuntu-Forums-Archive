---
title: "LAMP Individual Installs - Problems :("
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by r3ntry on 2007-04-02
I did install UBuntu Server and LAMP, but I could not get the desktop working and I thought to myself I would install them manually on a UBuntu WOrkstation 6.10.

apt-get install mysql-server

project@ubuntu:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Broken packages


and apache

project@ubuntu:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache2 has no installation candidate


I just don't understand why it is doing this, Its a completely fresh installation of LInux, Just enabled the network card and changed the sources to no CD's and, enabled multiverse.

---

### Post by EmmEff on 2007-04-02
Did you enable universe as well?

---

