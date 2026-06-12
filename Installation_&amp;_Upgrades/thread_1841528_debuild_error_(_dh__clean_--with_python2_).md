---
title: "debuild error ( dh  clean --with python2 )"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by uahmed on 2011-09-09
hi

I am new at here . I want to make the debian of blink i follow the instruction and to make debian i execute the command debuild , but it throws me this error

```

gnome@gnome:~/blink/blink-qt/dist/blink-0.2.8$ debuild
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package blink
dpkg-buildpackage: source version 0.2.8
dpkg-buildpackage: source changed by Saul Ibarra <saul@ag-projects.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh  clean --with python2
dh: unable to load addon python2: Can't locate Debian/Debhelper/Sequence/python2.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 8) line 2.
BEGIN failed--compilation aborted at (eval 8) line 2.

make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc failed


```I didnt find any solution of it any help please !

---

### Post by uahmed on 2011-09-12
any help in that ??

---

