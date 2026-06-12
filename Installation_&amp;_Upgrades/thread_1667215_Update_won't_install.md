---
title: "Update won't install"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by djbill on 2011-01-14
Hi folks, I've some problems with Ubuntu 10.10, Update Manager and dcraw. If I try install update or new software I receive this error...

```
simone@simone-laptop:~$ sudo apt-get install --reinstall dcraw
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze * * * 
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
 *hplip-cups linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Usare "apt-get autoremove" per rimuoverli.
0 aggiornati, 0 installati, 1 reinstallati, 0 da rimuovere e 79 non aggiornati.
È necessario scaricare 180kB di archivi.
Dopo quest'operazione, verranno occupati 0B di spazio su disco.
Scaricamento di:1 http://archive.ubuntu.com/ubuntu/ maverick/main dcraw i386 8.99-1 [180kB]
Recuperati 180kB in 1s (175kB/s)
Selezionato il pacchetto dcraw.
(Lettura del database... 60%dpkg: errore fatale non recuperabile, uscita:
 il file con l'elenco dei file del pacchetto "dcraw" contiene un nome file vuoto
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I've done also some apt-get commands but without results.

**sudo apt-get update**
```
Trovato http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en * * * 
Trovato http://archive.ubuntu.com maverick Release.gpg * * * * * * * * * * * * 
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en * * * * * * 
Trovato http://archive.ubuntu.com/ubuntu/ maverick/main Translation-it * * * * 
Scaricamento di:1 http://extras.ubuntu.com maverick Release.gpg [72B] * * * * *
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en * * * * * * *
Trovato http://ppa.launchpad.net maverick Release.gpg * * * * * * * * * * * * *
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ maverick/main Translation-it
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-it * * * 
Trovato http://archive.canonical.com maverick Release * * * * * * * * * * * * *
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-it * * * * * * *
Trovato http://extras.ubuntu.com maverick Release * * * * * * * * * * * * * * *
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en * * * 
Trovato http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en *
Trovato http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en * *
Trovato http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-it
Scaricamento di:2 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Trovato http://ppa.launchpad.net maverick Release * * * * * * * * * * * * 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Trovato http://archive.canonical.com maverick/partner i386 Packages * * * * * *
Trovato http://extras.ubuntu.com maverick/main i386 Packages * * * * * * * * *
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-it
Trovato http://archive.ubuntu.com maverick-backports Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Trovato http://ppa.launchpad.net maverick/main Sources
Trovato http://ppa.launchpad.net maverick/main i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-it
Scaricamento di:3 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-it
Scaricamento di:4 http://archive.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Trovato http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Trovato http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Trovato http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-it
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Trovato http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-it
Trovato http://archive.ubuntu.com maverick Release
Scaricamento di:5 http://archive.ubuntu.com maverick-updates Release [31,4kB]
Trovato http://archive.ubuntu.com maverick-backports Release
Scaricamento di:6 http://archive.ubuntu.com maverick-security Release [27,2kB]
Scaricamento di:7 http://archive.ubuntu.com maverick-proposed Release [31,4kB]
Trovato http://archive.ubuntu.com maverick/main Sources
Trovato http://archive.ubuntu.com maverick/restricted Sources
Trovato http://archive.ubuntu.com maverick/universe Sources
Trovato http://archive.ubuntu.com maverick/multiverse Sources
Trovato http://archive.ubuntu.com maverick/main i386 Packages
Trovato http://archive.ubuntu.com maverick/restricted i386 Packages
Trovato http://archive.ubuntu.com maverick/universe i386 Packages
Trovato http://archive.ubuntu.com maverick/multiverse i386 Packages
Scaricamento di:8 http://archive.ubuntu.com maverick-updates/main Sources [71,3kB]
Scaricamento di:9 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]
Scaricamento di:10 http://archive.ubuntu.com maverick-updates/universe Sources [23,7kB]
Scaricamento di:11 http://archive.ubuntu.com maverick-updates/multiverse Sources [1068B]
Scaricamento di:12 http://archive.ubuntu.com maverick-updates/main i386 Packages [195kB]
Scaricamento di:13 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Scaricamento di:14 http://archive.ubuntu.com maverick-updates/universe i386 Packages [77,2kB]
Scaricamento di:15 http://archive.ubuntu.com maverick-updates/multiverse i386 Packages [2522B]
Trovato http://archive.ubuntu.com maverick-backports/main i386 Packages
Trovato http://archive.ubuntu.com maverick-backports/restricted i386 Packages
Trovato http://archive.ubuntu.com maverick-backports/universe i386 Packages
Trovato http://archive.ubuntu.com maverick-backports/multiverse i386 Packages
Scaricamento di:16 http://archive.ubuntu.com maverick-security/main Sources [19,0kB]
Scaricamento di:17 http://archive.ubuntu.com maverick-security/restricted Sources [14B]
Scaricamento di:18 http://archive.ubuntu.com maverick-security/universe Sources [8221B]
Scaricamento di:19 http://archive.ubuntu.com maverick-security/multiverse Sources [649B]
Scaricamento di:20 http://archive.ubuntu.com maverick-security/main i386 Packages [59,4kB]
Scaricamento di:21 http://archive.ubuntu.com maverick-security/restricted i386 Packages [14B]
Scaricamento di:22 http://archive.ubuntu.com maverick-security/universe i386 Packages [31,4kB]
Scaricamento di:23 http://archive.ubuntu.com maverick-security/multiverse i386 Packages [1655B]
Scaricamento di:24 http://archive.ubuntu.com maverick-proposed/restricted i386 Packages [1797B]
Scaricamento di:25 http://archive.ubuntu.com maverick-proposed/main i386 Packages [31,0kB]
Scaricamento di:26 http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages [610B]
Scaricamento di:27 http://archive.ubuntu.com maverick-proposed/universe i386 Packages [14,9kB]
Recuperati 630kB in 6s (101kB/s) * * * * * * * * * * * * * * * * * * * * * * * 
Lettura elenco dei pacchetti... Fatto
```

**sudo apt-get upgrade**
```
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze * * * 
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti saranno aggiornati:
 *acroread apparmor apparmor-utils aptdaemon brasero brasero-cdrkit
 *brasero-common cups cups-bsd cups-client cups-common cups-ppdc cupsddk dpkg
 *evince evince-common evolution evolution-common evolution-data-server
 *evolution-data-server-common evolution-plugins icedtea-6-jre-cacao ifupdown
 *indicator-sound libapparmor-perl libapparmor1 libbrasero-media1
 *libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2
 *libcupsmime1 libcupsppdc1 libebackend1.2-0 libebook1.2-9 libecal1.2-7
 *libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13
 *libedataserverui1.2-8 libegroupwise1.2-13 libevdocument3 libevolution
 *libevview3 libgdata-google1.2-1 libgdata1.2-1 libparted0debian1 libsmbclient
 *libsqlite3-0 libwbclient0 libx264-98 linux-firmware linux-generic
 *linux-headers-generic linux-image-generic media-player-info openjdk-6-jre
 *openjdk-6-jre-headless openjdk-6-jre-lib openssh-client parted python
 *python-aptdaemon python-aptdaemon-gtk python-minimal samba-common
 *samba-common-bin smbclient ssh-askpass-gnome tar ttf-symbol-replacement
 *ubuntu-docs ubuntu-sso-client winbind wine wine1.2 xserver-common
 *xserver-xorg-core
79 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 0B/170MB di archivi.
Dopo quest'operazione, verranno occupati 2052kB di spazio su disco.
Continuare [S/n]? s
Estrazione dei template dai pacchetti: 100%
Preconfigurazione dei pacchetti in corso
(Lettura del database... 60%dpkg: errore fatale non recuperabile, uscita:
 il file con l'elenco dei file del pacchetto "dcraw" contiene un nome file vuoto
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

**sudo apt-get install -f**
```
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze * * * 
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
 *hplip-cups linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Usare "apt-get autoremove" per rimuoverli.
0 aggiornati, 0 installati, 0 da rimuovere e 79 non aggiornati.

```

Sorry for my poor english but I'm only an italian student...

---

### Post by sikander3786 on 2011-01-15
Seems like there is a problem with your /dpkg/status file. Try using an older file instead.

Backup the existing one:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Use the older one:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Update & Upgrade:

```
sudo apt-get update && sudo apt-get upgrade
```

If it still contains errors, please change your Language to English and post the whole output.

---

