---
title: "rsyslog broken, every apt-get upgrade hangs"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by Hammi on 2014-10-24
I have an Ubuntu 14.04.1 system. Recently, there was an upgrade to rsyslog, which I tried to install through apt-get dist-upgrade. The update did not go through (sorry, screen messages partially in Germany):

```
rsyslog (7.4.4-1ubuntu2.3) wird eingerichtet ...
The user `syslog' is already a member of `adm'.
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
```

And then the update process hung. On the next morning, I terminated this. Now, if I want to do anything with apt-get on the system (installing or removing any program, installing updates), dpkg also tries to configure rsyslog, and then hangs:

```
# apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Paketaktualisierung (Upgrade) wird berechnet... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  linux-headers-3.13.0-35 linux-headers-3.13.0-35-generic
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-35-generic
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden aktualisiert (Upgrade):
  libssl1.0.0 openssl python-requests tzdata wpasupplicant
5 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Es müssen 2.208 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 38,9 kB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] 
Holen: 1 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libssl1.0.0 i386 1.0.1f-1ubuntu2.7 [778 kB]
Holen: 2 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main tzdata all 2014i-0ubuntu0.14.04 [173 kB]
Holen: 3 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main openssl i386 1.0.1f-1ubuntu2.7 [479 kB]
Holen: 4 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main python-requests all 2.2.1-1ubuntu0.1 [42,9 kB]
Holen: 5 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main wpasupplicant i386 2.1-0ubuntu1.1 [734 kB]
Es wurden 2.208 kB in 0 s geholt (2.795 kB/s).
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 132328 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../libssl1.0.0_1.0.1f-1ubuntu2.7_i386.deb ...
Entpacken von libssl1.0.0:i386 (1.0.1f-1ubuntu2.7) über (1.0.1f-1ubuntu2.5) ...
Vorbereitung zum Entpacken von .../tzdata_2014i-0ubuntu0.14.04_all.deb ...
Entpacken von tzdata (2014i-0ubuntu0.14.04) über (2014e-0ubuntu0.14.04) ...
tzdata (2014i-0ubuntu0.14.04) wird eingerichtet ...

Current default time zone: 'Europe/Berlin'
Local time is now:      Fri Oct 24 07:48:30 CEST 2014.
Universal Time is now:  Fri Oct 24 05:48:30 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Lese Datenbank ... 132337 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../openssl_1.0.1f-1ubuntu2.7_i386.deb ...
Entpacken von openssl (1.0.1f-1ubuntu2.7) über (1.0.1f-1ubuntu2.5) ...
Vorbereitung zum Entpacken von .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
Entpacken von python-requests (2.2.1-1ubuntu0.1) über (2.2.1-1) ...
Vorbereitung zum Entpacken von .../wpasupplicant_2.1-0ubuntu1.1_i386.deb ...
Entpacken von wpasupplicant (2.1-0ubuntu1.1) über (2.1-0ubuntu1) ...
Trigger für man-db (2.6.7.1-1ubuntu1) werden verarbeitet ...
rsyslog (7.4.4-1ubuntu2.3) wird eingerichtet ...
The user `syslog' is already a member of `adm'.
```

(hangs)

As you can see, no updates are being configured anymore, as the update process does not go beyond the attempt to configure rsyslog.

Please help!

---

### Post by Hammi on 2014-10-24
update: As the dpkg process hung, I've downloaded rsyslog_7.4.4-1ubuntu2.3_i386.deb, unpacked it and looked at the postinst script. The postinst script runs fine until

```
invoke-rc.d rsyslog $_dh_action
```

(which is meant to "restart" rsyslog).

I tested this separately, and this invoke-rc.d command also just hangs if I run it separately (with "restart" instead of $_dh_action). It appears that also "service rsyslog start" just hangs.

Any hint where I might continue looking for the root cause and how to fix it?

---

### Post by gvelim on 2015-01-28
the way I fixed it in a brutal way is

1) sudo apt-get install -f and leave it there waiting
2) open a new terminal and run "sudo gnome-system-monitor"
3) find the rsyslogd process and kill it - the rsyslog child should be a zombie already

you should see (1) proceeding and completing. Job done

---

