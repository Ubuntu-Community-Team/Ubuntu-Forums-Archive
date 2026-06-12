---
title: "Ubuntu software center repair error"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by Mythek on 2012-09-20
When I open my software center it asks me to repair it and then i say yes. It comes up with an error

installArchives() failed: dpkg: dependency problems prevent configuration of libmtp-dev: 
 libmtp-dev depends on libmtp8 (= 1.0.2-1ubuntu1); however: 
  Package libmtp8 is not installed. 
dpkg: error processing libmtp-dev (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 libmtp-dev 
Error in function:  
dpkg: dependency problems prevent configuration of libmtp-dev: 
 libmtp-dev depends on libmtp8 (= 1.0.2-1ubuntu1); however: 
  Package libmtp8 is not installed. 
dpkg: error processing libmtp-dev (--configure): 
 dependency problems - leaving unconfigured

---

### Post by Bashing-om on 2012-09-20
Mythek;

  Hi ! ... As libmtp-dev is a developer package, I ask ...do you really need a developer package as this one is to support the transfer of music files on
USB digital audio players and movie files on USB portable media players.

This package contains the headers and development libraries.

If not; what happens when you uninstall the package:
```
sudo apt-get --purge remove libmtp-dev
```[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by Mythek on 2012-09-24
Fixed it thanks :guitar:

---

