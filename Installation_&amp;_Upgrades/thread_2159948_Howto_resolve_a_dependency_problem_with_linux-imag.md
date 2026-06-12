---
title: "Howto resolve a dependency problem with linux-image-server and linux-headers-server?"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by Spider IT on 2013-07-05
Hi all,  I'm using Ubuntu 12.04 LTS Server and want to install Subversion. As this couldn't be done because of missing dependencies, I tried to fix this problem. Therefore I had to delete some old files from /boot, because an upgrade process couldn't be finished. And now, on trying to fix the dependencies, I get the following (sorry, German, but I think you will understand the messages):  ...:~$ sudo apt-get -f install [sudo] password for ...: Paketlisten werden gelesen... Fertig Abhängigkeitsbaum wird aufgebaut Statusinformationen werden eingelesen... Fertig Abhängigkeiten werden korrigiert... Fertig Die folgenden zusätzlichen Pakete werden installiert:   linux-server Die folgenden Pakete werden aktualisiert (Upgrade):   linux-server 1 aktualisiert, 0 neu installiert, 0 zu entfernen und 99 nicht aktualisiert. 1 nicht vollständig installiert oder entfernt. Es müssen noch 0 B von 1.734 B an Archiven heruntergeladen werden. Nach dieser Operation werden 1.024 B Plattenplatz zusätzlich benutzt. Möchten Sie fortfahren [J/n]? Traceback (most recent call last):   File "/usr/bin/apt-listchanges", line 237, in      main()   File "/usr/bin/apt-listchanges", line 48, in main     debs = apt_listchanges.read_apt_pipeline(config)   File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in read_apt_pipeline     return map(lambda pkg: filenames[pkg], order)   File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in      return map(lambda pkg: filenames[pkg], order) KeyError: 'linux-server' dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-server:  linux-server hängt ab von linux-image-server (= 3.2.0.38.46); aber:   Version von linux-image-server auf dem System ist 3.2.0.49.59.  linux-server hängt ab von linux-headers-server (= 3.2.0.38.46); aber:   Version von linux-headers-server auf dem System ist 3.2.0.49.59. dpkg: Fehler beim Bearbeiten von linux-server (--configure):  Abhängigkeitsprobleme - verbleibt unkonfiguriert Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist                                                                                    Fehler traten auf beim Bearbeiten von:  linux-server E: Sub-process /usr/bin/dpkg returned an error code (1)  Any help is gladly appreciated! Kind regards René

---

### Post by Spider IT on 2013-07-05
Solved! aptitude corrected everything while installing subversion. And after that, I called it again to update the 99 not updated packages.

---

