---
title: "package failure upgrading to Breezy"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by jal on 2006-03-03
Some packages:
locales
 ubuntu-minimal
 ubuntu-base
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
failed to install when I upgraded from hoary to breezy. 

System is up :) and I haven't run into any problems (yet). 

Kynaptic shows locales in the intalled list.

 

```

john@acknak:~/downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up locales (2.3.5-1ubuntu12) ...
Generating locales...
  Usage:./usr/sbin/validlocale <locale>...Try `localedef --help' or `localedef --usage' for more information.
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
 ubuntu-minimal
 ubuntu-base
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Xian on 2006-03-03
What does the command below offer:

$ sudo dpkg-reconfigure locales

---

### Post by jal on 2006-03-06
<Sorry for the tardy answer, had to go away for a couple of days.>

john@acknak:~$ sudo dpkg-reconfigure locales
Password:
/usr/sbin/dpkg-reconfigure: locales is broken or not fully installed

---

### Post by jal on 2006-03-08
*bump*

I have just installed another package(apparently succesfully), it too complained about locale, printing the same "Usage:" message as below:
```

$ sudo dpkg --configure locales
Setting up locales (2.3.5-1ubuntu12) ...
Generating locales...
  Usage:./usr/sbin/validlocale <locale>...Try `localedef --help' or `localedef --usage' for more information.
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 locales

```

---

