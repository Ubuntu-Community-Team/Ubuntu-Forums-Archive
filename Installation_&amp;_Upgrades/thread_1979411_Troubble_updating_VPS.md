---
title: "Troubble updating VPS"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by Juukamen on 2012-05-13
Logged in to my VPS trough PuTTy and began updating it. Went well for a few hours and here is where it stopped up. Do not know how to overcome this problem. 

Welcome to Ubuntu 11.10 (GNU/Linux 2.6.18-274.7.1.el5.028stab095.1 i686)

 * Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

 New release '12.04 LTS' available.
 Run 'do-release-upgrade' to upgrade to it.

 *** System restart required ***
 You have mail.
 Last login: Sun May 13 13:17:46 2012 from 208.277.116.262
* root@server:~# ***apt-get clean**
* root@server:~# ***apt-get check**
 Reading package lists... Done
 Building dependency tree
 Reading state information... Done
 You might want to run 'apt-get -f install' to correct these.
 The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (> 2.15) but 2.13-20ubuntu5.1 is installed
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1) but 2.15-0ubuntu10 is installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10) but 2.13-20ubuntu5.1 is installed
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.3-4ubuntu2 is instal led
 E: Unmet dependencies. Try using -f.
* root@server:~#*** apt-get -f install**
 Reading package lists... Done
 Building dependency tree
 Reading state information... Done
 Correcting dependencies... failed.
 The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (> 2.15) but 2.13-20ubuntu5.1 is installed
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1) but 2.15-0ubuntu10 is installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10) but 2.13-20ubuntu5.1 is installed
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.3-4ubuntu2 is instal led
 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by he ld packages.
E: Unable to correct dependencies
* root@server:~#*

---

### Post by Juukamen on 2012-05-14
that hard to fix i guess... :/

---

### Post by Juukamen on 2012-05-14
sound some interessting...

*root@server:/#*** dpkg --configure -a**
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10); however:
  Version of libc6 on system is 2.13-20ubuntu5.1.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.15); however:
  Version of libc6 on system is 2.13-20ubuntu5.1.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnih-dbus1:
 libnih-dbus1 depends on libnih1 (= 1.0.3-4ubuntu9); however:
  Version of libnih1 on system is 1.0.3-4ubuntu2.
dpkg: error processing libnih-dbus1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libc-dev-bin
 libnih-dbus1
*root@server:/#*

---

