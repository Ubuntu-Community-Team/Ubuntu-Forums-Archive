---
title: "Breezy to Dapper Update: problems with cpio and other packages"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by chris_pmf on 2006-06-04
Hello,

I hope anybody can help me, I get this when I try to repair the broken packages, but it don't really help.
> $ sudo dpkg --configure -a
Richte cpio ein (2.6-10) ...
update-alternatives: internal error: /var/lib/dpkg/alternatives/mt corrupt: missing newline after manflag
dpkg: Fehler beim Bearbeiten von cpio (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von initramfs-tools:
 initramfs-tools hängt ab von cpio; aber:
  Paket cpio bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von initramfs-tools (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von alien:
 alien hängt ab von cpio; aber:
  Paket cpio bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von alien (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von dpkg-dev:
 dpkg-dev hängt ab von cpio (>= 2.4.2-2); aber:
  Paket cpio bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von dpkg-dev (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-core:
 lsb-core hängt ab von cpio; aber:
  Paket cpio bereitstellt, ist noch nicht konfiguriert.
 lsb-core hängt ab von alien (>= 8.36); aber:
  Paket alien bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-core (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von ubuntu-standard:
 ubuntu-standard hängt ab von cpio; aber:
  Paket cpio bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von ubuntu-standard (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von initrd-tools:
 initrd-tools hängt ab von cpio; aber:
  Paket cpio bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von initrd-tools (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-graphics:
 lsb-graphics hängt ab von lsb-core; aber:
  Paket lsb-core bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-graphics (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb:
 lsb hängt ab von lsb-core; aber:
  Paket lsb-core bereitstellt, ist noch nicht konfiguriert.
 lsb hängt ab von lsb-graphics; aber:
  Paket lsb-graphics bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von udev:
 udev hängt ab von initramfs-tools (>= 0.40ubuntu30); aber:
  Paket initramfs-tools bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von udev (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von ubuntu-minimal:
 ubuntu-minimal hängt ab von initramfs-tools; aber:
  Paket initramfs-tools bereitstellt, ist noch nicht konfiguriert.
 ubuntu-minimal hängt ab von udev; aber:
  Paket udev bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von ubuntu-minimal (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von usplash:
 usplash hängt ab von initramfs-tools (>= 0.40ubuntu30); aber:
  Paket initramfs-tools bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von usplash (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-cxx:
 lsb-cxx hängt ab von lsb-core; aber:
  Paket lsb-core bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-cxx (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von debhelper:
 debhelper hängt ab von dpkg-dev (>= 1.7.0); aber:
  Paket dpkg-dev bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von debhelper (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von hal:
 hal hängt ab von udev (>= 0.065); aber:
  Paket udev bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von hal (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von pcmciautils:
 pcmciautils hängt ab von udev; aber:
  Paket udev bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von pcmciautils (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lsb-desktop:
 lsb-desktop hängt ab von lsb-graphics; aber:
  Paket lsb-graphics bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lsb-desktop (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von mdadm:
 mdadm hängt ab von udev (>= 0.79-0ubuntu22); aber:
  Paket udev bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von mdadm (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lvm-common:
 lvm-common hängt ab von mdadm; aber:
  Paket mdadm bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lvm-common (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von lvm2:
 lvm2 hängt ab von lvm-common (>> 1.5.8); aber:
  Paket lvm-common bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von lvm2 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 cpio
 initramfs-tools
 alien
 dpkg-dev
 lsb-core
 ubuntu-standard
 initrd-tools
 lsb-graphics
 lsb
 udev
 ubuntu-minimal
 usplash
 lsb-cxx
 debhelper
 hal
 pcmciautils
 lsb-desktop
 mdadm
 lvm-common
 lvm2

---

