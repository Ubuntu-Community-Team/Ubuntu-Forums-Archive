---
title: "udev update problems"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by cent.mox on 2011-05-04
I did an updated to Ubuntu 11.04 and i got this problem:

```
root@v35212:~# apt-get install udev
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Vorgeschlagene Pakete:
  watershed
Die folgenden Pakete werden aktualisiert (Upgrade):
  udev
1 aktualisiert, 0 neu installiert, 0 zu entfernen und 382 nicht aktualisiert.
9 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 424 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 1.733 kB Plattenplatz zusätzlich benutzt.
(Lese Datenbank ... 
dpkg: Warnung: Dateilisten-Datei des Paketes »udev« fehlt, es wird angenommen,
dass das Paket derzeit keine Dateien installiert hat.
(Lese Datenbank ... 41591 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von udev 167-0ubuntu3 (durch .../udev_167-0ubuntu3_amd64.deb) ...
dpkg-divert: Fehler: »Umleitung von /sbin/udevadm zu /sbin/udevadm.upgrade durch fake-udev« kollidiert mit »lokale Umleitung von /sbin/udevadm zu /sbin/udevadm.upgrade«
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/udev_167-0ubuntu3_amd64.deb (--unpack):
 Unterprozess neues pre-installation-Skript gab den Fehlerwert 2 zurück
dpkg-divert: Fehler: Keine Übereinstimmung mit Paket
  beim Entfernen von »Umleitung von /sbin/udevadm zu /sbin/udevadm.upgrade durch fake-udev«
  »lokale Umleitung von /sbin/udevadm zu /sbin/udevadm.upgrade« gefunden
dpkg: Fehler beim Aufräumen:
 Unterprozess neues post-removal-Skript gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/udev_167-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

