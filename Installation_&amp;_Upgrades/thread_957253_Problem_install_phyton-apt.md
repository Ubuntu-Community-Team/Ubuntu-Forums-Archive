---
title: "Problem install phyton-apt"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by datru on 2008-10-24
Hello

I get these errors if i try to install aptitude install python-apt:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Richte lsb-core ein (3.1-23.1ubuntu3) ...
/var/lib/dpkg/info/lsb-core.postinst: 65: pycentral: not found
dpkg: Fehler beim Bearbeiten von lsb-core (--configure):
 Unterprozess post-installation script gab den Fehlerwert 127 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-graphics:
 lsb-graphics hängt ab von lsb-core; aber:
  Paket lsb-core ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-graphics (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb:
 lsb hängt ab von lsb-core; aber:
  Paket lsb-core ist noch nicht konfiguriert.
 lsb hängt ab von lsb-graphics; aber:
  Paket lsb-graphics ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Richte python-apt ein (0.7.3.1ubuntu4.2) ...
/var/lib/dpkg/info/python-apt.postinst: 6: pycentral: not found
dpkg: Fehler beim Bearbeiten von python-apt (--configure):
 Unterprozess post-installation script gab den Fehlerwert 127 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-cxx:
 lsb-cxx hängt ab von lsb-core; aber:
  Paket lsb-core ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-cxx (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-desktop:
 lsb-desktop hängt ab von lsb-graphics; aber:
  Paket lsb-graphics ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-desktop (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 lsb-core
 lsb-graphics
 lsb
 python-apt
 lsb-cxx
 lsb-desktop
Paketlisten werden gelesen... Fertig        
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Reading extended state information      
Initializing package states... Fertig
Writing extended state information... Fertig
Building tag database... Fertig            
```

i think the main problem is this:
```
/var/lib/dpkg/info/lsb-core.postinst: 65: pycentral: not found

```

Can someone help me?

Thanks!

---

### Post by datru on 2008-10-24
If i try to start the python interpreter /usr/bin/python2.5 i geht this error:

```
/usr/bin/python2.5 -v
# installing zipimport hook
import zipimport # builtin
# installed zipimport hook
'import site' failed; traceback:
ImportError: No module named site
Python 2.5.1 (r251:54863, Jul 31 2008, 23:17:40) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.


```

---

