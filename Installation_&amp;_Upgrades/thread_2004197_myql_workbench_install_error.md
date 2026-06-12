---
title: "myql workbench install error"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by wizardintrainin on 2012-06-15
first time using ubuntu. trying to install mysql workbench and got this:

dependency is not satisfiable: libmysqlclient16 (>=5.1.21-1)

what gives?

---

### Post by elghaouti on 2012-06-27
The libmysqlclient16 package was removed from the 12.04 repos so you will need to download the old deb files for it:
32 bit version - [http://launchpadlibrarian.net/94563300/libmysqlclient16_5.1.58-1ubuntu5_i386.deb](http://launchpadlibrarian.net/94563300/libmysqlclient16_5.1.58-1ubuntu5_i386.deb)
64 bit version - [http://launchpadlibrarian.net/94808408/libmysqlclient16_5.1.58-1ubuntu5_amd64.deb](http://launchpadlibrarian.net/94808408/libmysqlclient16_5.1.58-1ubuntu5_amd64.deb)

folow this page : 
[http://setupguides.blogspot.com/2012/04/install-mysql-workbench-on-ubuntu-1204.html](http://setupguides.blogspot.com/2012/04/install-mysql-workbench-on-ubuntu-1204.html)

---

