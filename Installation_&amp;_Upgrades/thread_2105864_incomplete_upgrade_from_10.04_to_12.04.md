---
title: "incomplete upgrade from 10.04 to 12.04"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by Rincewind2011 on 2013-01-17
Hello,
I tried to upgrade from ubuntu 10.04 to ubuntu 12.04.
While doing this my netbook went in suspend mode and when waking up I recognized the upgrade was NOT complete.
I tried to fix this by starting the upgrade again but the update-manager refused to so because of broken packages.
I tried
sudo aptitude safe-upgrade
and after that, my desktop looks very strange and I have not gained anything since update-manager is now broken too. :-(
Furthermore most of the broken packages are related to tex-common.

Is there anything I can do to fix these broken packages?
And to complete the upgrade?

Thanks for your help.

---

### Post by ibjsb4 on 2013-01-17
You can try

```
sudo apt-get -f install
```

Item #5

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Rincewind2011 on 2013-01-17
I already tried this.
It doesn't work. :-(

---

### Post by ibjsb4 on 2013-01-17
```
sudo apt-get update
```

How big of a mess is it?

Maybe post it using code tags.

[ATTACH]230180[/ATTACH]

---

### Post by Rincewind2011 on 2013-01-17
[HTML]sudo apt-get update yields the following

```

OK   http://archive.canonical.com precise Release.gpg
Ign http://archive.canonical.com/ubuntu/ precise/partner Translation-de
OK   http://de.archive.ubuntu.com precise Release.gpg
OK   http://de.archive.ubuntu.com/ubuntu/ precise/main Translation-de
OK   http://de.archive.ubuntu.com/ubuntu/ precise/restricted Translation-de
OK   http://de.archive.ubuntu.com/ubuntu/ precise/universe Translation-de
OK   http://de.archive.ubuntu.com/ubuntu/ precise/multiverse Translation-de
Hole:1 http://de.archive.ubuntu.com precise-updates Release.gpg [198B]
OK   http://de.archive.ubuntu.com/ubuntu/ precise-updates/main Translation-de
OK   http://de.archive.ubuntu.com/ubuntu/ precise-updates/restricted Translation-de
OK   http://de.archive.ubuntu.com/ubuntu/ precise-updates/universe Translation-de
OK   http://archive.canonical.com precise Release  
OK   http://de.archive.ubuntu.com/ubuntu/ precise-updates/multiverse Translation-de
Hole:2 http://de.archive.ubuntu.com precise-security Release.gpg [198B]
Ign http://de.archive.ubuntu.com/ubuntu/ precise-security/main Translation-de
Ign http://de.archive.ubuntu.com/ubuntu/ precise-security/restricted Translation-de
Ign http://de.archive.ubuntu.com/ubuntu/ precise-security/universe Translation-de
Ign http://de.archive.ubuntu.com/ubuntu/ precise-security/multiverse Translation-de
OK   http://de.archive.ubuntu.com precise Release
Hole:3 http://de.archive.ubuntu.com precise-updates Release [49,6kB]
OK   http://archive.canonical.com precise/partner Packages                     
Hole:4 http://de.archive.ubuntu.com precise-security Release [49,6kB]          
OK   http://de.archive.ubuntu.com precise/main Packages  
OK   http://de.archive.ubuntu.com precise/restricted Packages
OK   http://de.archive.ubuntu.com precise/main Sources
OK   http://de.archive.ubuntu.com precise/restricted Sources
OK   http://de.archive.ubuntu.com precise/universe Packages
OK   http://de.archive.ubuntu.com precise/universe Sources
OK   http://de.archive.ubuntu.com precise/multiverse Packages
OK   http://de.archive.ubuntu.com precise/multiverse Sources
Hole:5 http://de.archive.ubuntu.com precise-updates/main Packages [460kB]
Hole:6 http://de.archive.ubuntu.com precise-updates/restricted Packages [8.999B]
Hole:7 http://de.archive.ubuntu.com precise-updates/main Sources [200kB]
Hole:8 http://de.archive.ubuntu.com precise-updates/restricted Sources [4.743B]
Hole:9 http://de.archive.ubuntu.com precise-updates/universe Packages [169kB]
Hole:10 http://de.archive.ubuntu.com precise-updates/universe Sources [69,8kB]
Hole:11 http://de.archive.ubuntu.com precise-updates/multiverse Packages [9.678B]
Hole:12 http://de.archive.ubuntu.com precise-updates/multiverse Sources [4.240B]
Hole:13 http://de.archive.ubuntu.com precise-security/main Packages [222kB]
Hole:14 http://de.archive.ubuntu.com precise-security/restricted Packages [3.968B]
Hole:15 http://de.archive.ubuntu.com precise-security/main Sources [60,4kB]
Hole:16 http://de.archive.ubuntu.com precise-security/restricted Sources [1.950B]
Hole:17 http://de.archive.ubuntu.com precise-security/universe Packages [61,8kB]
Hole:18 http://de.archive.ubuntu.com precise-security/universe Sources [19,3kB]
Hole:19 http://de.archive.ubuntu.com precise-security/multiverse Packages [2.366B]
Hole:20 http://de.archive.ubuntu.com precise-security/multiverse Sources [1.379B]
Es wurden 1.399kB in 2s geholt (482kB/s)                      
Paketlisten werden gelesen... Fertig

```

The mess is big as I can not open my update-manager anymore and the graphics of my desktop is a mess.

---

### Post by ibjsb4 on 2013-01-17
This may or may not have to do with your problem, but it needs to be explored.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/940825](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/940825)

[https://bugs.launchpad.net/update-manager/+bug/1004918](https://bugs.launchpad.net/update-manager/+bug/1004918)

[https://www.google.com/search?client=ubuntu&channel=fs&q=http%3A%2F%2Fde.archive.ubuntu.com+precise-security%2Funiverse+Sources&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=http%3A%2F%2Fde.archive.ubuntu.com+precise-security%2Funiverse+Sources&ie=utf-8&oe=utf-8)

---

### Post by Rincewind2011 on 2013-01-17
The problem is not that I have no connection to the internet or that there are problems fetching packages.
The problem is that there are now broken packages, either not properly removed or installed.
Furthermore the update-manager does not start anymore.

---

### Post by ibjsb4 on 2013-01-17
> **Rincewind2011 said:**
> The problem is not that I have no connection to the internet or that there are problems fetching packages.
The problem is that there are now broken packages, either not properly removed or installed.
Furthermore the update-manager does not start anymore.

Ok, good enough.

I suspect package conflicts between the old and the new, so lets see if its in your sources.  Please post the following.

```
cat /etc/apt/sources.list
```and

```
cat /etc/apt/sources.list.d/*
```Also what does "hole" mean in your language?

---

### Post by Rincewind2011 on 2013-01-17
I get the following:
```

rincewind@Arbeitszwerg:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise universe
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://de.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://de.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://de.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-security multiverse

```

and 

```

rincewind@Arbeitszwerg:~$ cat /etc/apt/sources.list.d/*
# deb http://ppa.launchpad.net/gma500/ppa/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert
deb http://ppa.launchpad.net/gma500/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/gma500/ppa/ubuntu lucid main
# deb http://ppa.launchpad.net/ricotz/ppa/ubuntu lucid main
# deb http://ppa.launchpad.net/ricotz/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/ricotz/ppa/ubuntu lucid main

```

If "hole" is not English, then it has the meaning of "fetching" or "getting s.th.".

---

### Post by ibjsb4 on 2013-01-17
Ok, as you can see, list.d still has Lucid and needs to be removed.  So ..

```
sudo rm -r /etc/apt/sources.list.d/*  && sudo apt-get update
```

Try your update manager now.

---

### Post by Rincewind2011 on 2013-01-17
removed it.
But update-manager is still broken.

```

rincewind@Arbeitszwerg:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk

```

Tried to reinstall but got the error that there are broken packages:
```

rincewind@Arbeitszwerg:~$ sudo apt-get install --reinstall update-manager
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder dass, wenn Sie die
Unstable-Distribution verwenden, einige erforderliche Pakete noch nicht
erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben nicht-erfüllte Abhängigkeiten:
  isc-dhcp-client: Stört: network-manager (< 0.8.2~rc1) aber 0.8-0ubuntu3.3 soll installiert werden
  libasound2: Stört: libasound2-plugins (< 1.0.24) aber 1.0.22-0ubuntu6 soll installiert werden
  libglib2.0-0: Stört: gnome-control-center (< 1:3) aber 1:2.30.1-0ubuntu2 soll installiert werden
  nautilus: Empfiehlt: brasero (>= 2.26) soll aber nicht installiert werden
            Stört: gnome-bluetooth (< 3.0) aber 2.30.0-0ubuntu3 soll installiert werden
  ppp: Stört: network-manager (<= 0.8.0.999-1) aber 0.8-0ubuntu3.3 soll installiert werden
       Stört: network-manager-pptp (<= 0.8.0.999-1) aber 0.8-0ubuntu3 soll installiert werden
E: Kaputte Pakete

```

---

### Post by ibjsb4 on 2013-01-17
```
sudo dpkg --configure -a && sudo apt-get -f install
```

And with that, Im out of ideas  :(

---

### Post by Rincewind2011 on 2013-01-17
Well, that didn't work either, got:
```

rincewind@Arbeitszwerg:~$ sudo dpkg --configure -a && sudo apt-get -f install
[sudo] password for rincewind: 
Richte tex-common ein (2.10) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building format(s) --all.
        This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.Q6k5JGxz
Please include this file if you report a bug.

dpkg: Fehler beim Bearbeiten von tex-common (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-metapost:
 texlive-metapost hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-metapost (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-science:
 texlive-science hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-science (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex-extra-doc:
 texlive-latex-extra-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex-extra-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-science-doc:
 texlive-science-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-science-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-fonts-extra-doc:
 texlive-fonts-extra-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-fonts-extra-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-metapost-doc:
 texlive-metapost-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-metapost-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-luatex:
 texlive-luatex hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-luatex (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-generic-recommended:
 texlive-generic-recommended hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-generic-recommended (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-pstricks-doc:
 texlive-pstricks-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-pstricks-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-fonts-recommended:
 texlive-fonts-recommended hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-fonts-recommended (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von latex2html:
 latex2html hängt ab von texlive-fonts-recommended; aber:
  Paket texlive-fonts-recommended ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von latex2html (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-pictures:
 texlive-pictures hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-pictures (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von preview-latex-style:
 preview-latex-style hängt ab von tex-common; aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von preview-latex-style (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-fonts-extra:
 texlive-fonts-extra hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-fonts-extra (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von context:
 context hängt ab von texlive-metapost (>= 2009); aber:
  Paket texlive-metapost ist noch nicht konfiguriert.
 context hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von context (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-pictures-doc:
 texlive-pictures-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-pictures-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von pgf:
 pgf hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von pgf (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-bibtex-extra:
 texlive-bibtex-extra hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-bibtex-extra (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex-recommended-doc:
 texlive-latex-recommended-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex-recommended-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex-recommended:
 texlive-latex-recommended hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex-recommended (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-pstricks:
 texlive-pstricks hängt ab von texlive-generic-recommended (>= 2009-1); aber:
  Paket texlive-generic-recommended ist noch nicht konfiguriert.
 texlive-pstricks hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-pstricks (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-math-extra:
 texlive-math-extra hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
 texlive-math-extra hängt ab von texlive-fonts-recommended (>= 2009-1); aber:
  Paket texlive-fonts-recommended ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-math-extra (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex3:
 texlive-latex3 hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex3 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von tipa:
 tipa hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von tipa (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex-base:
 texlive-latex-base hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex-base (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-fonts-recommended-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von latex-beamer:
 latex-beamer hängt ab von pgf (>= 1.00-1); aber:
  Paket pgf ist noch nicht konfiguriert.
 latex-beamer hängt ab von texlive-latex-base; aber:
  Paket texlive-latex-base ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von latex-beamer (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-font-utils:
 texlive-font-utils hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-font-utils (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex-base-doc:
 texlive-latex-base-doc hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex-base-doc (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-common:
 texlive-common hängt ab von tex-common (>= 2.0); aber:
  Paket tex-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-common (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von feynmf:
 feynmf hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
 feynmf hängt ab von texlive-latex-base; aber:
  Paket texlive-latex-base ist noch nicht konfiguriert.
 feynmf hängt ab von texlive-font-utils; aber:
  Paket texlive-font-utils ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von feynmf (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-xetex:
 texlive-xetex hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
 texlive-xetex hängt ab von texlive-common (>= 2009-1); aber:
  Paket texlive-common ist noch nicht konfiguriert.
 texlive-xetex hängt ab von texlive-latex-base (>= 2009-1); aber:
  Paket texlive-latex-base ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-xetex (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-latex-extra:
 texlive-latex-extra hängt ab von preview-latex-style; aber:
  Paket preview-latex-style ist noch nicht konfiguriert.
 texlive-latex-extra hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
 texlive-latex-extra hängt ab von texlive-common (>= 2009-1); aber:
  Paket texlive-common ist noch nicht konfiguriert.
 texlive-latex-extra hängt ab von texlive-pictures (>= 2009-1); aber:
  Paket texlive-pictures ist noch nicht konfiguriert.
 texlive-latex-extra hängt ab von texlive-latex-base (>= 2009-1); aber:
  Paket texlive-latex-base ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-latex-extra (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive-extra-utils:
 texlive-extra-utils hängt ab von tex-common (>= 2.00); aber:
  Paket tex-common ist noch nicht konfiguriert.
 texlive-extra-utils hängt ab von texlive-common (>= 2009-1); aber:
  Paket texlive-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive-extra-utils (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von texlive:
 texlive hängt ab von texlive-fonts-recommended (>= 2009-1); aber:
  Paket texlive-fonts-recommended ist noch nicht konfiguriert.
 texlive hängt ab von texlive-latex-recommended (>= 2009-1); aber:
  Paket texlive-latex-recommended ist noch nicht konfiguriert.
 texlive hängt ab von texlive-latex-base (>= 2009-1); aber:
  Paket texlive-latex-base ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von texlive (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 tex-common
 texlive-metapost
 texlive-science
 texlive-latex-extra-doc
 texlive-science-doc
 texlive-fonts-extra-doc
 texlive-metapost-doc
 texlive-luatex
 texlive-generic-recommended
 texlive-pstricks-doc
 texlive-fonts-recommended
 latex2html
 texlive-pictures
 preview-latex-style
 texlive-fonts-extra
 context
 texlive-pictures-doc
 pgf
 texlive-bibtex-extra
 texlive-latex-recommended-doc
 texlive-latex-recommended
 texlive-pstricks
 texlive-math-extra
 texlive-latex3
 tipa
 texlive-latex-base
 texlive-fonts-recommended-doc
 latex-beamer
 texlive-font-utils
 texlive-latex-base-doc
 texlive-common
 feynmf
 texlive-xetex
 texlive-latex-extra
 texlive-extra-utils
 texlive

```

Suppose I shoud get rid of tex for a moment?!

---

### Post by ibjsb4 on 2013-01-17
> **Rincewind2011 said:**
> Suppose I shoud get rid of tex for a moment?!

Sounds like a good idea, also get rid of source code by unchecking the box in software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by ibjsb4 on 2013-01-17
One other thing that hasn't been done yet is a cleaning.

```
sudo apt-get clean && sudo apt-get autoremove --purge && sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

### Post by Rincewind2011 on 2013-01-28
removed tex
But still cannot install anything.
When removing some unnecessary games using synaptic got the following answer:
```

Rebuilding /usr/share/applications/desktop.de_DE.utf8.cache...
ERROR: Cannot import gmenu, is a package upgrade in progress?

```
But there is no upgrade in progress?!

---

### Post by Rincewind2011 on 2013-02-01
Removing tex didn't help at all.
There was too much broken, so I rescued my /home and reinstalled the total system.
Now everything works again. ;-)

I didn't find a real solution to the problem but now the case is close anyway.

---

