---
title: "dpkg: Fehler beim Bearbeiten von initramfs-tools"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Ph1b on 2012-02-06
Hey, I'm getting the following error when trying to update my system. I did a apt-get update before.

> andrea@andrea-Extensa-5230:~$ [COLOR=Red]sudo apt-get upgrade[/COLOR]
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
[COLOR=Red]4 nicht vollständig installiert oder entfernt.[/COLOR]
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? J
initramfs-tools (0.99ubuntu8) wird eingerichtet ...
update-initramfs: deferring update (trigger activated)
linux-image-3.0.0-15-generic (3.0.0-15.26) wird eingerichtet ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled
(3.0.0-15.25 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.0.0-15.25 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
Fatal: No images have been defined.
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: Fehler beim Bearbeiten von linux-image-3.0.0-15-generic (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 2 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-backports-modules-cw-3.1-3.0.0-15-generic:
 linux-backports-modules-cw-3.1-3.0.0-15-generic hängt ab von linux-image-3.0.0-15-generic; aber:
  Paket linux-image-3.0.0-15-generic ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von linux-backports-modules-cw-3.1-3.0.0-15-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-backports-modules-net-3.0.0-15-generic:
 linux-backports-modules-net-3.0.0-15-generic hängt ab von linux-image-3.0.0-15-generic; aber:
  Paket linux-image-3.0.0-15-generic ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von linux-backports-modules-net-3.0.0-15-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Trigger für initramfs-tEs wurde kein Apport-Bericht verfasst, da die  Fehlermeldung darauf hindeutet, dass dies lediglich ein Folgefehler  eines vorherigen Problems ist.
                                                                    Es  wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf  hindeutet, dass dies lediglich ein Folgefehler eines vorherigen Problems  ist.
              ools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
Fatal: No images have been defined.
[COLOR=Red]run-parts: /etc/initramfs/post-update.d//[/COLOR][COLOR=Red]runlilo exited with return code 1
dpkg: Fehler beim Bearbeiten von initramfs-tools (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist

[/COLOR] [COLOR=Red]             Fehler traten auf beim Bearbeiten von:
 linux-image-3.0.0-15-generic
 linux-backports-modules-cw-3.[/COLOR][COLOR=Red]1-3.0.0-15-generic
 linux-backports-modules-net-[/COLOR][COLOR=Red]3.0.0-15-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
How can I solve this?

---

### Post by zvacet on 2012-02-07
```
sudo dpkg --configure -a
```

---

### Post by Ph1b on 2012-02-14
I tried it, but once again, I got a bunch of errors:

```
andrea@andrea-Extensa-5230:~$ sudo dpkg --configure -a 
initramfs-tools (0.99ubuntu8) wird eingerichtet ... 
update-initramfs: deferring update (trigger activated) 
linux-image-3.0.0-15-generic (3.0.0-15.26) wird eingerichtet ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.25 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.25 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools  3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic 
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic  /boot/vmlinuz-3.0.0-15-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier  3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.0.0-15-generic  /boot/vmlinuz-3.0.0-15-generic 
Fatal: No images have been defined. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at  /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010. 
dpkg: Fehler beim Bearbeiten von linux-image-3.0.0-15-generic (--configure): 
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert  2 zurück 
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von  linux-backports-modules-cw-3.1-3.0.0-15-generic: 
 linux-backports-modules-cw-3.1-3.0.0-15-generic hängt ab von  linux-image-3.0.0-15-generic; aber: 
  Paket linux-image-3.0.0-15-generic ist noch nicht konfiguriert. 
dpkg: Fehler beim Bearbeiten von  linux-backports-modules-cw-3.1-3.0.0-15-generic (--configure): 
 Abhängigkeitsprobleme - verbleibt unkonfiguriert 
linux-image-3.0.0-16-generic (3.0.0-16.28) wird eingerichtet ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools  3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic 
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic  /boot/vmlinuz-3.0.0-16-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier  3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.0.0-16-generic  /boot/vmlinuz-3.0.0-16-generic 
Fatal: No images have been defined. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at  /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postinst line 1010. 
dpkg: Fehler beim Bearbeiten von linux-image-3.0.0-16-generic (--configure): 
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert  2 zurück 
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von  linux-image-generic: 
 linux-image-generic hängt ab von linux-image-3.0.0-16-generic; aber: 
  Paket linux-image-3.0.0-16-generic ist noch nicht konfiguriert. 
dpkg: Fehler beim Bearbeiten von linux-image-generic (--configure): 
 Abhängigkeitsprobleme - verbleibt unkonfiguriert 
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von  linux-backports-modules-net-3.0.0-15-generic: 
 linux-backports-modules-net-3.0.0-15-generic hängt ab von  linux-image-3.0.0-15-generic; aber: 
  Paket linux-image-3.0.0-15-generic ist noch nicht konfiguriert. 
dpkg: Fehler beim Bearbeiten von  linux-backports-modules-net-3.0.0-15-generic (--configure): 
 Abhängigkeitsprobleme - verbleibt unkonfiguriert 
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-generic: 
 linux-generic hängt ab von linux-image-generic (= 3.0.0.16.19); aber: 
  Paket linux-image-generic ist noch nicht konfiguriert. 
dpkg: Fehler beim Bearbeiten von linux-generic (--configure): 
 Abhängigkeitsprobleme - verbleibt unkonfiguriert 
Trigger für initramfs-tools werden verarbeitet ... 
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic 
Fatal: No images have been defined. 
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1 
dpkg: Fehler beim Bearbeiten von initramfs-tools (--configure): 
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert  1 zurück 
Fehler traten auf beim Bearbeiten von: 
 linux-image-3.0.0-15-generic 
 linux-backports-modules-cw-3.1-3.0.0-15-generic 
 linux-image-3.0.0-16-generic 
 linux-image-generic 
 linux-backports-modules-net-3.0.0-15-generic 
 linux-generic 
 initramfs-tools 
```

---

