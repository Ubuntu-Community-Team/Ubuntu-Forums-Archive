---
title: "new python3-update-manager package pre-removal script process returned error"
date: 2023-02-04
forum: Installation &amp; Upgrades
---

### Post by bromptonaut2 on 2023-02-04
When I try to install software with *ubuntu software* or *snap store* I get the error Message
*new python3-update-manager package pre-removal script process returned error*

```
sudo apt update 
```
terminates with the message
```
sh: 1: /usr/lib/cnf-update-db: not found
Paketlisten werden gelesen… Fertig
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

```

```
sudo apt upgrade
```
gives
```
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 update-manager : Hängt ab von: update-manager-core (= 1:22.04.9) aber 1:22.04.10 ist installiert
 update-manager-core : Hängt ab von: python3-update-manager (= 1:22.04.10) aber 1:22.04.9 ist installiert
E: Unerfüllte Abhängigkeiten. Versuchen Sie »apt --fix-broken install« ohne Angabe eines Pakets (oder geben Sie eine Lösung an).

```

```
sudo apt --fix-broken install
```
gives
```
Die folgenden zusätzlichen Pakete werden installiert:
  python3-software-properties python3-update-manager software-properties-common software-properties-gtk update-manager
Die folgenden Pakete werden aktualisiert (Upgrade):
  python3-software-properties python3-update-manager software-properties-common software-properties-gtk update-manager
5 aktualisiert, 0 neu installiert, 0 zu entfernen und 79 nicht aktualisiert.
53 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 707 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 39,9 kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] 

```

```
sudo apt --fix-broken install
```
gives a series of messages like
```
Anforderung zur Speicherung des aktuellen Systemzustands
Erfolgreich als "autozsys_lb87wh" gespeichert
(Lese Datenbank ... 394117 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../python3-update-manager_1%3a22.04.10_all.deb ...
/var/lib/dpkg/info/python3-update-manager.prerm: 6: py3clean: not found
dpkg: Warnung: »altes python3-update-manager-Skript des Paketes pre-removal«-Unterprozess gab den Fehlerwert 127 zurück
dpkg: stattdessen wird Skript aus dem neuen Paket probiert ...
/var/lib/dpkg/tmp.ci/prerm: 6: py3clean: not found
dpkg: Fehler beim Bearbeiten des Archivs /var/cache/apt/archives/python3-update-manager_1%3a22.04.10_all.deb (--unpack):
 »neues python3-update-manager-Skript des Paketes pre-removal«-Unterprozess gab den Fehlerwert 127 zurück

```

reboot doesn't help ;-)

Does anybody know what to do here?

ubuntu 22.04.1
64 bit 
kernel 5.15.0-57

---

### Post by MAFoElffen on 2023-02-04
I'm doing a somewhat educated guess...

It says it can't find 'py3clean'. 'py3clean' is a part of package ' python3-minimal_3.4.0-0ubuntu2_amd64 '... What happens if you do
```

apt list python3-minimal --installed

```
Is that package there?

---

### Post by bromptonaut2 on 2023-02-06
```
:sudo apt list  python3-minimal --installed
Auflistung… Fertig
python3-minimal/jammy-updates,now 3.10.6-1~22.04 amd64  [Installiert,automatisch]
N: Es gibt 1 zusätzliche Version. Bitte verwenden Sie die Option »-a«, um sie anzuzeigen.

:sudo apt list  python3-minimal --installed -a
Auflistung… Fertig
python3-minimal/jammy-updates,now 3.10.6-1~22.04 amd64  [Installiert,automatisch]
python3-minimal/jammy 3.10.4-0ubuntu2 amd64

```

Does that mean there are two versions installed?

---

### Post by #&amp;thj^% on 2023-02-06
Just driving by here,
```
me on Mon Feb 06 at 11:04 AM in ~ branch: (HEAD) 
>> apt list python3-minimal --installed
Listing... Done
python3-minimal/lunar,now 3.11.1-0ubuntu1 amd64 [installed,automatic]


me on Mon Feb 06 at 11:05 AM in ~ branch: (HEAD) 
>> apt list python3-minimal --installed -a
Listing... Done
python3-minimal/lunar,now 3.11.1-0ubuntu1 amd64 [installed,automatic]


```

have you tried:
```
sudo apt install python3-minimal python3 --reinstall
```
if that succeeds use:
```
sudo apt autoremove
```

---

### Post by bromptonaut2 on 2023-02-06
Thank you for the suggestion. 

```
$ sudo apt install python3-minimal python3 --reinstall
 
Paketlisten werden gelesen… Fertig
Abhängigkeitsbaum wird aufgebaut… Fertig
Statusinformationen werden eingelesen… Fertig
Probieren Sie »apt --fix-broken install«, um dies zu korrigieren.
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 update-manager : Hängt ab von: update-manager-core (= 1:22.04.9) aber 1:22.04.10 soll installiert werden
 update-manager-core : Hängt ab von: python3-update-manager (= 1:22.04.10) aber 1:22.04.9 soll installiert werden
E: Unerfüllte Abhängigkeiten. Versuchen Sie »apt --fix-broken install« ohne Angabe eines Pakets (oder geben Sie eine Lösung an).

```

And I already tried »apt --fix-broken install«. 
Is it risky (if possible) to uninstall and then re-install python3?

---

### Post by #&amp;thj^% on 2023-02-06
> Is it risky (if possible) to uninstall and then re-install python3? 
Can you translate a bit for me, ah never mind translation:
```
update-manager-core : Depends on: python3-update-manager (= 1:22.04.10) but 1:22.04.9 should be installed
```

1-What changes have you recently made to your system? 
Also this might end up being a system breaker IE:
```
sudo apt remove --purge python3-minimal -s
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python3 : PreDepends: python3-minimal (= 3.11.1-0ubuntu1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```
One final thought from me, can you install 
```
python3-all
```
My system is in good shape but:
```
apt policy python3-all 
python3-all:
  Installed: (none)
  Candidate: 3.11.1-0ubuntu1
  Version table:
     3.11.1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages

```
EDIT: Please try to remove the older python pkg:
```
sudo apt remove python3-minimal '3.10.6-1~22.04'

```

---

### Post by bromptonaut2 on 2023-02-07
SOLVED

It was a missing symbolic link in /usr/bin/

Apparently the symbolic link *python3* pointing to *python3.10* was lost, for what reason ever.

Thank you for helping!

---

### Post by #&amp;thj^% on 2023-02-07
> **bromptonaut2 said:**
> SOLVED

It was a missing symbolic link in /usr/bin/

Apparently the symbolic link *python3* pointing to *python3.10* was lost, for what reason ever.

Thank you for helping!

Thanks for sharing your fix, very helpful. ;)

---

