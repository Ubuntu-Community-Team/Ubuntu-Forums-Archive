---
title: "Cannot upgrade Mysql 5.1"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by 4thfloorstudios on 2010-10-11
Hi,
I am trying to update my MySQL database but get this errors (sorry, in german...):
```

Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Die folgenden Pakete sind zurückgehalten worden:
  libboost-dev php5-dev
Die folgenden Pakete werden aktualisiert:
  mysql-client-5.1
1 aktualisiert, 0 neu installiert, 0 zu entfernen und 2 nicht aktualisiert.
Es müssen noch 0B von 8.257kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? J
(Lese Datenbank ... 466084 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von mysql-client-5.1 5.1.50-0.dotdeb.0 (durch .../mysql-client-5.1_5.1.51-0.dotdeb.1_i386.deb) ...
Entpacke Ersatz für mysql-client-5.1 ...
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/mysql-client-5.1_5.1.51-0.dotdeb.1_i386.deb (--unpack):
 Versuche, »/usr/bin/mysql« zu überschreiben, welches auch in Paket mysql-client-core-5.1 0:5.1.41-3ubuntu12.6 ist
dpkg-deb: Unterprozess einfügen mit Signal (Broken pipe) getötet
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/mysql-client-5.1_5.1.51-0.dotdeb.1_i386.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Especially this message:

```
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/mysql-client-5.1_5.1.51-0.dotdeb.1_i386.deb (--unpack):
 Versuche, »/usr/bin/mysql« zu überschreiben, welches auch in Paket mysql-client-core-5.1 0:5.1.41-3ubuntu12.6 ist
```

says that "mysql-client-5.1_5.1.51-0.dotdeb.1_i386.deb" cannot be upgraded.

I do not want to uninstall mysql completely because then a big list of other packages is deinstalled too :)

Can anyone help me?

Thanks,
Oliver

---

### Post by 4thfloorstudios on 2010-10-12
Ok, now I completely reinstalled MySQL and everything is working, but....

After uninstalling MySQL, I could not select KDE anymore in my login screen.

The cause was that the package "kdebase-workspace-bin" was removed with MySQL.

After reinstalling it, everything worked fine again, but what a crap is this? You uninstall a database and cannot work anymore on your desktop?!?

Hope this helsp someone else...

---

