---
title: "dpkg can't find mkinitrd"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by d-nbuntu-k on 2013-12-09
Hello,

when running 'dpkg --configure -a' it says it cant find mkinitrd[1]. I'm running Kubuntu 13.10 and I know mkinitrd is depricated and mkinitramfs should used instead. But how can I tell dpkg to use mkinitramfs instead of mkinitrd?


[1]
```

sudo dpkg --configure -a
linux-image-3.11.0-14-generic (3.11.0-14.21) wird eingerichtet ...
Running depmod.
sh: 1: /usr/bin/mkinitrd: not found
Failed to create initrd image.
dpkg: Fehler beim Bearbeiten von linux-image-3.11.0-14-generic (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 2 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-image-extra-3.11.0-14-generic:
 linux-image-extra-3.11.0-14-generic hängt ab von linux-image-3.11.0-14-generic; aber:
  Paket linux-image-3.11.0-14-generic ist noch nicht konfiguriert.


dpkg: Fehler beim Bearbeiten von linux-image-extra-3.11.0-14-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-image-generic:
 linux-image-generic hängt ab von linux-image-3.11.0-14-generic; aber:
  Paket linux-image-3.11.0-14-generic ist noch nicht konfiguriert.
 linux-image-generic hängt ab von linux-image-extra-3.11.0-14-generic; aber:
  Paket linux-image-extra-3.11.0-14-generic ist noch nicht konfiguriert.


dpkg: Fehler beim Bearbeiten von linux-image-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 linux-image-3.11.0-14-generic
 linux-image-extra-3.11.0-14-generic
 linux-image-generic



```




Thanks for your help.

Chris

---

