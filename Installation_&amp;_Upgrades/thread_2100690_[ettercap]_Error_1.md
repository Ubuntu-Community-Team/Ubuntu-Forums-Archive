---
title: "[ettercap] Error 1"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by CupOfItalian on 2013-01-02
For those who are installing ettercap in ubuntu 12.04, most of us get the error while make of:

make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/usr/local/Programs/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/Programs/ettercap/src'
make: *** [all-recursive] Error 1

To fix this:

cd src
gedit Makefile

change 'LIBS = ' *to match* 'EC_LIBS = '

then have fun with no errors!!   ):P

---

### Post by dino99 on 2013-01-02
is there a bug report sent to launchpad ?

---

### Post by CupOfItalian on 2013-01-03
This is the original post: [https://sites.google.com/site/websiteselblogdelhacker/instal-lar-ettercap-ng-0-7-4](https://sites.google.com/site/websiteselblogdelhacker/instal-lar-ettercap-ng-0-7-4) it's in spanish, but i found one translated into english. I didn't find a link that reported a bug. So I don't think so.

---

