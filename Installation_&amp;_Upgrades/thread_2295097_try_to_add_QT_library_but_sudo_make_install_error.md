---
title: "try to add QT library but sudo make install error"
date: 2015-09-16
forum: Installation &amp; Upgrades
---

### Post by YingHua_Chen on 2015-09-16
Hi, I am trying to add QT library in my xubuntu 14.04 environrment and following steps from the web as below.

[http://doc.qt.io/qt-4.8/install-x11.html](http://doc.qt.io/qt-4.8/install-x11.html)

but something wrong when the step "** sudo make install** "

.obj/qtypeavailablefn.o: file not recognized: File truncated
collect2: error: ld returned 1 exit status
make[3]: *** [../../lib/libQt5XmlPatterns.so.5.2.0] Error 1
make[3]: Leaving directory `/home/ubuntu/opt/qt-everywhere-opensource-src-5.2.0/qtxmlpatterns/src/xmlpatterns'
make[2]: *** [sub-xmlpatterns-install_subtargets] Error 2
make[2]: Leaving directory `/home/ubuntu/opt/qt-everywhere-opensource-src-5.2.0/qtxmlpatterns/src'
make[1]: *** [sub-src-install_subtargets] Error 2
make[1]: Leaving directory `/home/ubuntu/opt/qt-everywhere-opensource-src-5.2.0/qtxmlpatterns'
make: *** [module-qtxmlpatterns-install_subtargets] Error 2

---

### Post by Sweet_Baby_Jamie on 2015-09-16
Why not just add it from the Ubuntu repository?  Use Synaptic Package Manager and search for "Qt."  It's all there!  Adding software from some web site should not be typical for Ubuntu users.

---

### Post by spjackson on 2015-09-16
I notice that the documentation you refer to is for Qt 4.8 but the source you are trying to build is Qt 5.2. Although I would not expect this conflict to be the cause of your error, Qt 4 and Qt 5 are sufficiently different that referring to the wrong documentation might lead you into difficulties.

Whether you want Qt 4 or 5, the sensible approach is to install the right package, rather than to build it yourself. That being said, if you have all the necessary development dependencies it should be possible to build it. Could something catastrophic have occurred during the build process, e.g. out of disk space. I can't think what else would cause ".obj/qtypeavailablefn.o: file not recognized: File truncated".

---

### Post by YingHua_Chen on 2015-09-30
Thank you :)
I will try to install in another way and notice the QT version.

---

