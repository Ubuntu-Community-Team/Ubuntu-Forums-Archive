---
title: "Some lib-problems (libx11-6,libxt6)"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by Morimando on 2005-04-28
```
(Lese Datenbank ... 16841 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libx11-6 (aus libx11-6_6.8.2-10_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: Fehler beim Bearbeiten von libx11-6_6.8.2-10_i386.deb (--install):
 Unterprozess pre-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 libx11-6_6.8.2-10_i386.deb
```
is what i get everytime i try to install those libs (again: libx11-6 , libxt6), happens with both versions that are available (without having marillat as repository)...
i'll translate:
```
Reading database... 16841 files and directories installed.
Extracting libx11-6 (from libx11-6_6.8.2-10_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: Errors occured while processing libx11-6_6.8.2-10_i386.deb (--install):
 Subprocess pre-installation script returned errorstatus 1 
Errors encountered while processing:
 libx11-6_6.8.2-10_i386.deb
```

what shall I do?

---

