---
title: "Update problem libgs8_8.61"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by jettapup on 2008-02-09
Installed 7.10 from cd, update 147 ? packages, 2 failed, 

E: /var/cache/apt/archives/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libgs.so.8.61')

E: /var/cache/apt/archives/openoffice.org-java-common_1%
3a2.3.0-1ubuntu5.3_all.deb: subprocess dpkg-deb --fsys-tarfile returned
error exit status 2


Each report is started with E:  what might that mean? if this was dos, I'd go to my e: drive if I had one,

Navigated the path and tried to delete the packages but got a denied access, ( which was probably good, I suppose)

Do I continue to try and up date at every reboot, or try something else.?

Thanks in advance
Jettapup

---

### Post by PmDematagoda on 2008-02-09
Remove the files using root permissions by executing:-
```
sudo rm /var/cache/apt/archives/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.3_i386.deb
```
and 
```
sudo rm /var/cache/apt/archives/openoffice.org-java-common_1%3a2.3.0-1ubuntu5.3_all.deb
```
Then try updating again.

Edit:- In the second command the file name is a whole one and not broken up into pieces, sorry for the typo.

---

### Post by jettapup on 2008-02-09
WOW that was fast !!!!!


Thank You,
I will do so as soon as I am fully awake !

JettaPup

---

