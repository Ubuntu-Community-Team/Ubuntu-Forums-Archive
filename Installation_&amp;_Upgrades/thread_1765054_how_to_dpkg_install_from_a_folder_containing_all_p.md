---
title: "how to dpkg install from a folder containing all packages including dependencies??"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by bhupinderjitbawa on 2011-05-22
HI i want to install package say PHP5 
i have all the dependencies packages of php5 in a folder.

or 
say i have all the packages in a folder and i want to install using dpkg

but when i try to install the main package it say these dependencies are missing..
there are more than 40-50 packages so its not possible to install manully first one package and then another..

eg:

```
bhupinder packages # dpkg -i apache2_2.2.17-1ubuntu1_i386.deb
(Reading database ... 140101 files and directories currently installed.)
Preparing to replace apache2 2.2.17-1ubuntu1 (using apache2_2.2.17-1ubuntu1_i386.deb) ...
Unpacking replacement apache2 ...
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (= 2.2.17-1ubuntu1) | apache2-mpm-prefork (= 2.2.17-1ubuntu1) | apache2-mpm-event (= 2.2.17-1ubuntu1) | apache2-mpm-itk (= 2.2.17-1ubuntu1); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is not installed.
 apache2 depends on apache2.2-common (= 2.2.17-1ubuntu1); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2

```

now i have to install rest of the package manually ...is there any solution so that i can install it with single command...???

---

### Post by ajgreeny on 2011-05-22
Navigate to the folder containing all the .debs and run ```
sudo dpkg -i *.deb
```and the system will work out the installation for you without throwing any dependency errors, as it will know the dependency packages are already marked for install.

Make sure you have only the .deb packages you want to install in the folder, or you may get error messages about other installation and re-installation problems.

---

