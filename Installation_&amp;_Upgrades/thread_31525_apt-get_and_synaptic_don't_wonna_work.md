---
title: "apt-get and synaptic don't wonna work"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by klausi banausi on 2005-05-03
hello - as linux newbee I'm quiet happy with the possibility to install something with the tool apt-get - but my 2 days old hoary has now a problem with apt-get and synaptic - see this......

root@angel:/home/klaus # apt-get install mc
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Die folgenden NEUEN Pakete werden installiert:
mc
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 1960kB Archive geholt werden.
Nach dem Auspacken werden 5468kB Plattenplatz zusätzlich benutzt.
Hole:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe mc 1:4.6.0-4.6.1-pre1-3 [1960kB]Es wurden 1960kB in 33s geholt (58,9kB/s)

Preconfiguring packages ...
dpkg: konnte Paket-Infodatei »/var/lib/dpkg/available« nicht zum Lesen öffnen: Datei oder Verzeichnis nicht gefunden
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@angel:/home/klaus #

I know it is in german but maybe somebody can help me
ciao and thanks in advance
klaus

---

### Post by matthieufecteau on 2005-05-03
Are you connected to the internet ?  If yes :  Is your loopback interface is started ?  To look further into that direction (loopback...), read the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback) 

It was my problem

---

### Post by klausi banausi on 2005-05-04
lo is running 

root@angel:/home/klaus # ifconfig
lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2264 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:204466 (199.6 KiB)  TX bytes:204466 (199.6 KiB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:xx:xx:xx:xx:xx
          inet Adresse:192.168.0.2  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::211:95ff:fe16:3d47/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7719 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:8785441 (8.3 MiB)  TX bytes:701926 (685.4 KiB)
          Interrupt:18 Basisadresse:0xe000

must be something else?!

---

### Post by hashimoto on 2005-05-04
Klausi is online and the package gets downloaded. It seems to complain that dpkg can't open "/var/lib/dpkg/available" for reading: file or directory not found. 

Somebody?

---

### Post by cutOff on 2005-05-04
Maybe removing 'available' file and try again.

---

### Post by klausi banausi on 2005-05-04
yea mister hashimoto - seems to be something else - anyway maybe I should reinstall the whole thing.  but this reminds me - reminds me  ](*,)  windooooof

---

