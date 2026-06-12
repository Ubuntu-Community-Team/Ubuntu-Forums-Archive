---
title: "apt-get upgrade fails bash korrupt"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Hook2013 on 2013-04-18
Hi all!

I just tried to install the newest updates on my ubuntu server 12.4.2.

This is what i got back:

```

root@ubuntu-server:~# sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
AbhÃ¤ngigkeitsbaum wird aufgebaut
Statusinformationen werden eingelesen... Fertig
Die folgenden Pakete werden aktualisiert (Upgrade):
  bash curl libcurl3 libcurl3-gnutls libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libpam-smbpass libpam-winbind
  libwbclient0 samba samba-common samba-common-bin samba-doc smbclient winbind
17 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
1 nicht vollstÃ¤ndig installiert oder entfernt.
Es mÃ¼ssen noch 0 B von 37,3 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 10,2 kB Plattenplatz freigegeben.
MÃ¶chten Sie fortfahren [J/n]? j
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 130855 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von bash 4.2-2ubuntu2 (durch .../bash_4.2-2ubuntu2.1_i386.deb) ...
dpkg (Unterprozess): altes pre-removal-Skript (/var/lib/dpkg/info/bash.prerm) kann nicht ausgefÃ¼hrt werden: Keine Berechtigung
dpkg: Warnung: Unterprozess altes pre-removal-Skript gab den Fehlerwert 2 zurÃ¼ck
dpkg - stattdessen wird Skript aus dem neuen Paket probiert ...
dpkg (Unterprozess): neues pre-removal-Skript (/var/lib/dpkg/tmp.ci/prerm) kann nicht ausgefÃ¼hrt werden: Keine Berechtigung
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/bash_4.2-2ubuntu2.1_i386.deb (--unpack):
 Unterprozess neues pre-removal-Skript gab den Fehlerwert 2 zurÃ¼ck
Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
dpkg (Unterprozess): installiertes post-installation-Skript (/var/lib/dpkg/info/bash.postinst) kann nicht ausgefÃ¼hrt werden: Keine Berechtigung
dpkg: Fehler beim AufrÃ¤umen:
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 2 zurÃ¼ck
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/bash_4.2-2ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Do you have any Idea to fix this?

lg Julius

---

### Post by ibjsb4 on 2013-04-18
Have you tried cleaning out var/cache/apt/archives?

```
sudo apt-get clean
sudo apt-get update
```

---

### Post by Hook2013 on 2013-04-18
Yes i tried all of them.
apt-get:
clean
autoclean
autoremove
update
upgrade

Allways an error.

It seems that an older bash installation is not ready.

I think remove an reinstall bash would be dangerous?

---

### Post by ibjsb4 on 2013-04-18
> I think remove an reinstall bash would be dangerous? 

I cannot say with certainty what results that would yield.

What about the universal fixes?

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by Hook2013 on 2013-04-18
Result:

```
root@ubuntu-server:~# dpkg --configure -a
dpkg: Fehler beim Bearbeiten von bash (--configure):
 Paket ist in einem sehr schlechten inkonsistenten Zustand - Sie sollten es
 nochmal installieren, bevor Sie die Konfiguration versuchen.
Fehler traten auf beim Bearbeiten von:
 bash
root@ubuntu-server:~# apt-get -f install
Paketlisten werden gelesen... Fertig
AbhÃ¤ngigkeitsbaum wird aufgebaut
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 17 nicht aktualisiert.
1 nicht vollstÃ¤ndig installiert oder entfernt.
Es mÃ¼ssen noch 0 B von 616 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusÃ¤tzlich benutzt.
(Lese Datenbank ... 130855 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von bash 4.2-2ubuntu2 (durch .../bash_4.2-2ubuntu2_i386.deb) ...
dpkg (Unterprozess): altes pre-removal-Skript (/var/lib/dpkg/info/bash.prerm) kann nicht ausgefÃ¼hrt werden: Keine Berechtigung
dpkg: Warnung: Unterprozess altes pre-removal-Skript gab den Fehlerwert 2 zurÃ¼ck
dpkg - stattdessen wird Skript aus dem neuen Paket probiert ...
dpkg (Unterprozess): neues pre-removal-Skript (/var/lib/dpkg/tmp.ci/prerm) kann nicht ausgefÃ¼hrt werden: Keine Berechtigung
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/bash_4.2-2ubuntu2_i386.deb (--unpack):
 Unterprozess neues pre-removal-Skript gab den Fehlerwert 2 zurÃ¼ck
dpkg (Unterprozess): installiertes post-installation-Skript (/var/lib/dpkg/info/bash.postinst) kann nicht ausgefÃ¼hrt werden: Keine Berechtigung
dpkg: Fehler beim AufrÃ¤umen:
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 2 zurÃ¼ck
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/bash_4.2-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu-server:~#
```

---

### Post by Hook2013 on 2013-04-18
Hi all!

Is here nobody who knows a solution?

lg Julius

---

### Post by steeldriver on 2013-04-18
I don't speak German but it looks like a very specific problem with the permissions on the package's script files in /var/lib/dpkg/info 

What does the following say?

```
ls -l /var/lib/dpkg/info/bash.*
```

---

### Post by Hook2013 on 2013-04-19
> **steeldriver said:**
> I don't speak German but it looks like a very specific problem with the permissions on the package's script files in /var/lib/dpkg/info 

What does the following say?

```
ls -l /var/lib/dpkg/info/bash.*
```

The Result is:

```

root@ubuntu-server:~# ls -l /var/lib/dpkg/info/bash.*
-rw-r--r-- 1 root root   77 Apr  3  2012 /var/lib/dpkg/info/bash.conffiles
-rw-r--r-- 1 root root  928 Dez  1 08:16 /var/lib/dpkg/info/bash.list
-rw-r--r-- 1 root root 1331 Apr  3  2012 /var/lib/dpkg/info/bash.md5sums
-rwxr-xr-x 1 root root  596 Apr  3  2012 /var/lib/dpkg/info/bash.postinst
-rwxr-xr-x 1 root root  493 Apr  3  2012 /var/lib/dpkg/info/bash.postrm
-rwxr-xr-x 1 root root 9636 Apr  3  2012 /var/lib/dpkg/info/bash.preinst
-rwxr-xr-x 1 root root  289 Apr  3  2012 /var/lib/dpkg/info/bash.prerm
root@ubuntu-server:~#

```

---

### Post by Hook2013 on 2013-04-22
Hi all!

At the moment i also can not install new packages, because of this error:

```

root@ubuntu-server:~# apt-get install htop
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Die folgenden NEUEN Pakete werden installiert:
  htop
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 23 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 682 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 184 kB Plattenplatz zusätzlich benutzt.
(Lese Datenbank ... 130855 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von bash 4.2-2ubuntu2 (durch .../bash_4.2-2ubuntu2_i386.deb) ...
dpkg (Unterprozess): altes pre-removal-Skript (/var/lib/dpkg/info/bash.prerm) kann nicht ausgeführt werden: Keine Berechtigung
dpkg: Warnung: Unterprozess altes pre-removal-Skript gab den Fehlerwert 2 zurück
dpkg - stattdessen wird Skript aus dem neuen Paket probiert ...
dpkg (Unterprozess): neues pre-removal-Skript (/var/lib/dpkg/tmp.ci/prerm) kann nicht ausgeführt werden: Keine Berechtigung
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/bash_4.2-2ubuntu2_i386.deb (--unpack):
 Unterprozess neues pre-removal-Skript gab den Fehlerwert 2 zurück
dpkg (Unterprozess): installiertes post-installation-Skript (/var/lib/dpkg/info/bash.postinst) kann nicht ausgeführt werden: Keine Berechtigung
dpkg: Fehler beim Aufräumen:
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/bash_4.2-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu-server:~#

```

Can anyone tell me:

Is it dangerous to complete remove the complete package 'bash' and reinstall it with apt-get?
I have 4 Intranet Websites and an samba-server running on this server and dont want to loose them.

thx for help

lg Julius

---

### Post by grahammechanical on 2013-04-22
My guess is that you are using Bash to run the update commands.

[http://ss64.com/bash/](http://ss64.com/bash/)

You could try ```
sudo apt-get --reinstall bash
```

And see what happens.

Regards,

---

