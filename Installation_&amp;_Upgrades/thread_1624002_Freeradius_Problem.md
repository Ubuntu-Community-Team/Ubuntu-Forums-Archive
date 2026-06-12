---
title: "Freeradius Problem"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by volvolinux on 2010-11-17
Hello
 
I am lost in Freeradius on Ubuntu....
 
I want to use peap authentication in ubuntu platform, but it seems that the rlm_eap_tls.so has license problem and not built in the ubuntu freeradius, then I try to build the source code and find that in hardy 8.04, it need the debhelper version >=6.04.
 
Then i donwload the debhelpler 8.00 and try to make it a deb package by using:
 
[EMAIL="matt@radius:~/debhelper$"]matt@radius:~/debhelper$[/EMAIL] dpkg-buildpackage -rfakeroot                          
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package debhelper
dpkg-buildpackage: source version 8.0.0
dpkg-buildpackage: source changed by Joey Hess <[EMAIL="joeyh@debian.org"]joeyh@debian.org[/EMAIL]>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
./run dh clean
[COLOR=red]Undefined subroutine &Getopt::Long::GetOptionsFromArray called at /home/matt/debhelper/Debian/Debhelper/Dh_Getopt.pm line 156.
[/COLOR]make: *** [clean] Error 255
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2
 
 
Can someone help me on this issue?
 
thanks!!!!!

---

