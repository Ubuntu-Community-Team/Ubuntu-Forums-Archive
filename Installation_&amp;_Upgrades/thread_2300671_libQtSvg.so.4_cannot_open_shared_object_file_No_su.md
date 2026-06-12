---
title: "libQtSvg.so.4: cannot open shared object file: No such file or directory on ubuntu"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-10-27
on ubuntu 15.10
 
I have installed  UaExpert v1.3.1  from [https://www.unified-automation.com/downloads/opc-ua-clients.html](https://www.unified-automation.com/downloads/opc-ua-clients.html)
But when I try to launch the  UaExpert v1.3.1 I get the following errors.
I have google and tried all that I was able to find, but nothing worked.

./uaexpert 
./uaexpert: error while loading shared libraries: libQtSvg.so.4: cannot open shared object file: No such file or directory

---

### Post by hoboy on 2015-10-27
problem solved I sudo cp /opt/unifiedautomation/qt-4.8.6/lib/libQtSvg.so.4 /usr/lib/

---

