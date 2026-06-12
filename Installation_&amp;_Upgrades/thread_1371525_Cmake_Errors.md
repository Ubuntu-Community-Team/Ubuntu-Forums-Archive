---
title: "Cmake Errors"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by afderrick on 2010-01-03
Trying to install a KDE app (tellico) in Ubuntu.  The newest version has a few patch fixes from the one in the repos.

I am typing in:
```
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
```

It runs through the file and I get a
```
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/derrick/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:34 (find_package)


-- Configuring incomplete, errors occurred!
```

I have done some research and tried using a fix:
```
export CMAKE_MODULE_PATH=/usr/share/kde4/apps/cmake/modules
```

This has not fixed the problem.

I have also checked my kdelibs, I have 
kdelibs, kdelibs4c2a, kdelibs5, kdelibs5-data, kdelibs-bin
installed which are all the ones in the repos.  

Anyone know what I'm missing?

---

### Post by afderrick on 2010-01-03
Finally figured it out on the KDE forums.  I needed to install kdelibs5-dev and it worked like a champ.

---

