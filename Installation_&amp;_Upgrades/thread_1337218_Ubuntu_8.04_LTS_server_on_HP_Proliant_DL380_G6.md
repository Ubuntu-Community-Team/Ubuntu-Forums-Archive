---
title: "Ubuntu 8.04 LTS server on HP Proliant DL380 G6"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by lptr on 2009-11-25
Found here: [http://www.ubuntu.com/partners/hp](http://www.ubuntu.com/partners/hp) that G6 is only supported with new server version 9.10. 

We having an DL360 G5 that is still running 8.04 LTS. For some weird circumstances this machine needs to get exchanged by a new DL380 G6. Another option would be to buy instead of a G6 server an old DL380 G5. 

The problem is that there is a very tight timeframe to do the right steps. What would you suggest? Distupgrade or buying a G5 machine with SmartArray controller that can run old config immediately?

rob*

Update: I actually ordered inbetween a Proliant DL380 G6. We will set up a new machine. Additionally I ordered a backup drive for the current mirror. Will respawn the mirror to get a quick live setup. 

Does anyone know if it is possible to mount this single backup RAID0+1 set drive on a SmartArray  P410i controller to only getting the data down there? No mirror of course - in other words: Mounting as a broken mirror ? Is this possible. I know that the old ACU (array controller utility) for Debian only provided part of the full functions normally available under Windows stuff.

---

### Post by lptr on 2009-12-02
Ok answering myself - maybe anyone finds following valueable.

We did a new installation on 9.04 AMD for some reasons. Configured machine new and moved data over there manually. HP provides some licences to activate regarding tools to manipulate mirrors and the like. Don't know how much is it, though.


What we are now trying is getting that hardware support utils from HP running. Especially we are interested that ACU (this RAID util for Smart Array Controller p400i) and CLI tools for iLO2 will work. Until now there is no go. 

Anyone knowing how to resolve i386 dependencies for example libc6-i386 in hp-health? There seems to be no source to recompile it ourselves and provided tools obviously are not compatible with Server 9.04 AMD :(

```
# dpkg -i ./hp-health_8.2.5.47-11_amd64.deb 
Wähle vormals abgewähltes Paket hp-health.
(Lese Datenbank ... 51341 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke hp-health (aus .../hp-health_8.2.5.47-11_amd64.deb) ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von hp-health:
 hp-health hängt ab von libc6-i386 (>= 2.7-1); aber:
  Paket libc6-i386 ist nicht installiert.
dpkg: Fehler beim Bearbeiten von hp-health (--install):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Verarbeite Trigger für man-db ...
Fehler traten auf beim Bearbeiten von:
 hp-health
``````
# dpkg -i ./hpacucli_8.28-13.0.10-9_amd64.deb 
Wähle vormals abgewähltes Paket hpacucli.
(Lese Datenbank ... 51394 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke hpacucli (aus .../hpacucli_8.28-13.0.10-9_amd64.deb) ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von hpacucli:
 hpacucli hängt ab von lib32gcc1 (>= 1:4.1.1); aber:
  Paket lib32gcc1 ist nicht installiert.
 hpacucli hängt ab von lib32stdc++6 (>= 4.1.1); aber:
  Paket lib32stdc++6 ist nicht installiert.
 hpacucli hängt ab von libc6-i386 (>= 2.7-1); aber:
  Paket libc6-i386 ist nicht installiert.
dpkg: Fehler beim Bearbeiten von hpacucli (--install):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Verarbeite Trigger für man-db ...
Fehler traten auf beim Bearbeiten von:
 hpacucli
```

---

