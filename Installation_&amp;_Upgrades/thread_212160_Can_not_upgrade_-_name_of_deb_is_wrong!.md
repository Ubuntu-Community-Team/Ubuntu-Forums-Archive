---
title: "Can not upgrade - name of deb is wrong!?"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by c.barnes on 2006-07-09
Hi!

Im trying to upgrade my Dapper Drake, but when I do

sudo apt-get update
sudo apt-get upgrade

I get: 

[INDENT]Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Die folgenden Pakete werden aktualisiert:
  compiz compiz-gnome cupsys cupsys-bsd cupsys-client libcairo2 libcairo2-dev
  libcupsimage2 libcupsys2 libgnomecups1.0-1 pmount
11 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 2566kB von 3887kB Archiven geholt werden.
Nach dem Auspacken werden 135kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]?[/INDENT]

and after saying J (yes) I get:

[INDENT]Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/main libcupsys2 1.2.1-0ubuntu1
  404 Not Found
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/main libcupsimage2 1.2.1-0ubuntu1
  404 Not Found
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/main cupsys 1.2.1-0ubuntu1
  404 Not Found
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/main cupsys-bsd 1.2.1-0ubuntu1
  404 Not Found
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-upd ... [/INDENT]

and many more of those 404 No Found messages.

After I`ve compared packages through the webinterface, I see: 

upgrade wants to load: libcupsys2 1.2.1-0ubuntu1
but at [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper-updates/main ther is only a:
libcupsys2_1.2.1-2ubuntu2_i386.deb

:confused:   !?

what is the difference between ubuntu1 and ubuntu2 ??

What should I do?

CU
Cliff

---

### Post by c.barnes on 2006-07-09
After a few hours it's working again - I've nothing changed.

---

